---
layout: default
title: API Example
parent: Samples
nav_order: 3
---

# API Example

This sample demonstrates driving KitForge AI programmatically using strictly
the public C# API surface in the `DecnetGames.KitForgeAI` namespace
(Package Manager sample **API Example**, path `Samples~/APIExample`).

## What the driver does

The `APIExampleDriver` script executes an automated end-to-end workflow:

1. **Profile Kit** — scans a modular kit folder (`KitForge.ProfileKit`) and
   detects piece roles and grid dimensions.
2. **Load Plan** — reads a structure plan from a JSON file
   (`KitForge.LoadPlan`).
3. **Assemble Structure** — places kit prefabs into the active scene
   (`KitForge.Build`) with deterministic seed ordering.
4. **Audit Census** — reads the `BuildReport` to verify piece counts,
   skipped pieces, and placement integrity.

## Usage

To execute the example in the Unity Editor:

```csharp
using DecnetGames.KitForgeAI.Samples;

// Run with default sample paths:
bool success = APIExampleDriver.RunExample();

// Or run with custom kit and plan paths:
bool customSuccess = APIExampleDriver.RunExample(
    "Assets/MyModularKit",
    "Assets/Plans/CastleOutpost.json"
);
```

All methods return strongly-typed result objects (`ProfileResult`,
`PlanResult`, `BuildResult`) and never throw exceptions across the public
boundary.

> Next: the full [API Reference]({{ site.baseurl }}/docs/api/) and the
> [Agent Guide]({{ site.baseurl }}/docs/api/agent-guide/) for driving
> KitForge AI from an AI coding agent.
