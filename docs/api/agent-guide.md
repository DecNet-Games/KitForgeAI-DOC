---
layout: default
title: Agent Guide
parent: API Reference
nav_order: 3
---

# Agent Guide

This guide explains how autonomous AI coding agents (such as Claude, Cursor,
GitHub Copilot, or Antigravity) drive KitForge AI programmatically.

## Architecture & integration model

KitForge AI provides a headless, strongly-typed C# API in the namespace
`DecnetGames.KitForgeAI`. All public methods return structured result types
and never throw exceptions across the public boundary:

- `KitForge.ProfileKit(folderPath, options)` → `ProfileResult`
- `KitForge.LoadPlan(jsonOrPath)` → `PlanResult`
- `KitForge.ParseTextPlan(textDescription)` → `PlanResult`
- `KitForge.Build(profile, plan, options)` → `BuildResult`
- `KitForge.ReDress(root, profile, plan, seed)` → `BuildResult`

## Step 1 · Profile the kit

Before building, point KitForge AI at your kit folder to generate a
`KitProfile`.

```csharp
using DecnetGames.KitForgeAI;

ProfileResult profileResult = KitForge.ProfileKit("Assets/MyKitFolder");
if (!profileResult.Success)
{
    // Handle actionable error
    Debug.LogError(profileResult.ErrorMessage);
    return;
}

KitProfile profile = profileResult.Profile;
```

The profiler detects the kit's grid size (e.g. 2.0 m) and classifies prefabs
into roles (`Wall`, `WallDoor`, `WallWindow`, `WallCorner`, `Floor`,
`RoofFlat`, `RoofPitched`, `DoorLeaf`, `Prop`).

## Step 2 · Author the structure plan

Agents can generate structure plans using either the versioned JSON format
or the structured text grammar.

### Option A: JSON format (`kitforge-plan: 1`)

```json
{
  "kitforge-plan": 1,
  "name": "Guard Outpost",
  "gridSize": 2.0,
  "floors": 1,
  "seed": 12345,
  "roof": {
    "type": "Flat"
  },
  "rooms": [
    {
      "id": "main_room",
      "role": "Storage",
      "bounds": { "x": 0, "y": 0, "width": 4, "height": 3 },
      "edges": [
        { "side": "South", "offset": 1, "mark": "Door" },
        { "side": "East", "offset": 1, "mark": "Window" }
      ]
    }
  ]
}
```

Load the plan:

```csharp
PlanResult planResult = KitForge.LoadPlan(jsonContentOrFilePath);
if (!planResult.Success)
{
    Debug.LogError(planResult.ErrorMessage);
    return;
}
StructurePlan plan = planResult.Plan;
```

### Option B: Structured text plan

```csharp
string text = "4x3 outpost, South door, East window, flat roof, storage room";
PlanResult planResult = KitForge.ParseTextPlan(text);
if (!planResult.Success)
{
    Debug.LogError(planResult.ErrorMessage);
    return;
}
StructurePlan plan = planResult.Plan;
```

## Step 3 · Build the structure

```csharp
BuildOptions options = new BuildOptions
{
    Seed = plan.seed,
    Density = InteriorDensity.Furnished
};

BuildResult buildResult = KitForge.Build(profile, plan, options);
if (!buildResult.Success)
{
    Debug.LogError(buildResult.ErrorMessage);
    return;
}

GameObject structureRoot = buildResult.RootObject;
BuildReport report = buildResult.Report;
```

## Step 4 · Inspect the build report

The `BuildReport` provides a complete, factual census of what was placed and
what was skipped:

```csharp
Debug.Log($"Built {report.summary}");
Debug.Log($"Placed: {report.totalPlaced}, Skipped: {report.totalSkipped}");
Debug.Log($"Determinism Hash: {report.determinismHash}");

// Verify piece census
foreach (var censusEntry in report.census)
{
    Debug.Log($"Role: {censusEntry.role}, Placed Count: {censusEntry.count}");
}

// Check skipped pieces
if (report.totalSkipped > 0)
{
    foreach (var skip in report.skippedPieces)
    {
        Debug.LogWarning($"Skipped {skip.role}: {skip.reason}");
    }
}
```

## Step 5 · Re-dress interior props independently

To vary or re-roll prop arrangements without touching the assembled
structural shell:

```csharp
BuildResult dressResult = KitForge.ReDress(structureRoot, profile, plan, newSeed: 54321);
if (dressResult.Success)
{
    Debug.Log("Interior re-dressed successfully.");
}
```

## Agent best practices

1. **Always check result objects.** Check `.Success` on every result. If
   false, `.ErrorMessage` contains the exact problem and the fixing action.
2. **Deterministic reproducibility.** The `seed` field guarantees that
   identical inputs produce the exact same layout and piece sequence hash.
3. **Native instances.** All generated instances are native Unity prefab
   links under a single root GameObject. You can inspect or modify child
   components directly.
4. **Undo support.** Every assembly and re-dress operation registers a
   single clean Undo group in the Unity Editor (`"Build Structure"`).
