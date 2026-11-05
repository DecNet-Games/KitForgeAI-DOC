---
layout: default
title: Text Plan Grammar
parent: Planning
nav_order: 2
---

# Text Plan Grammar

KitForge AI includes a local, deterministic text plan parser that converts
short structured descriptions into strongly-typed `StructurePlan` assets.
Type a description into the **Parse Description** field in the Plan section
and click **Parse Description**. There is no cloud or language model involved
— the grammar below runs entirely on your machine, and a failed parse names
the exact token that failed.

- Grammar version: 1.0.0
- Namespace: `DecnetGames.KitForgeAI`

## Grammar syntax overview

A text plan description is composed of comma-separated or semicolon-separated
clauses specifying footprint dimensions, floors, roof style, edge openings,
room roles, and placement parameters.

### 1. Structure dimensions and name

Format: `[name] [width]x[height]` or `[width]x[height]`

- `[name]` (optional): alphanumeric structure label (e.g. `outpost`,
  `watchtower`, `barracks`). Default: `Untitled Plan`.
- `[width]x[height]`: positive integer grid dimensions in modular units
  (e.g. `4x3`, `8x6`).

### 2. Storey count

Format: `[count] floors` or `floors [count]` or `[count] floor`

- Positive integer defining vertical storey stacking. Default: `1`.

### 3. Roof style

Format: `[style] roof`

- `flat roof`: instantiates flat roof slabs covering the structure footprint.
- `pitched roof`: instantiates symmetric pitched ridge pieces across the
  upper storey.
- `no roof`: leaves the top storey open without roof geometry.
  Default: `flat roof`.

### 4. Wall openings (doors and windows)

Format: `[door|doors|window|windows] [direction] [at offset]`

- `direction`: compass side along the room perimeter (`south`, `north`,
  `east`, `west`).
- `offset` (optional): zero-based integer index along the specified edge.
  Default: `1`.

### 5. Functional room role

Format: `role [role]` or `[role] room`

- Supported roles: `generic`, `storage`, `living`, `watch`.
- Determines prop selection rules during interior dressing passes.
  Default: `generic`.

### 6. Placement seed & modular grid

Format: `seed [integer]`, `grid [float]`

- `seed`: integer controlling deterministic random prop and piece variations.
  Default: `12345`.
- `grid`: modular grid snap size in meters (e.g. `grid 2.0`). Default: `2.0`.

## Canonical examples

The following canonical examples are verified by the automated test suite
(A-L2-03).

### Example 1: Basic outpost

```text
outpost 4x3, door south at 1, windows east at 1, flat roof
```

- Name: `outpost`
- Grid bounds: 4 units wide by 3 units deep
- Storeys: 1
- Roof: Flat
- Openings: door on South edge (offset 1), window on East edge (offset 1)

This is also the exact plan line shipped with the Sample Outpost sample, with
`role storage` added:

```text
outpost 4x3, door south at 1, windows east at 1, flat roof, role storage
```

### Example 2: Two-storey watchtower

```text
watchtower 3x3, 2 floors, door south at 1, pitched roof, role watch
```

- Name: `watchtower`
- Grid bounds: 3 units wide by 3 units deep
- Storeys: 2
- Roof: Pitched
- Role: Watch
- Openings: door on South edge (offset 1)

### Example 3: Outpost with multiple openings

```text
outpost 8x6, door south at 2, window north at 2, windows east at 1, flat roof, seed 12345
```

- Name: `outpost`
- Grid bounds: 8 units wide by 6 units deep
- Storeys: 1
- Roof: Flat
- Seed: 12345
- Openings: door on South edge (offset 2), window on North edge (offset 2),
  window on East edge (offset 1)

### Example 4: Multi-room compound

```text
room storage 2x3 at 0,0, role storage, door south at 1; room living 2x3 at 2,0, role living, window east at 1, flat roof
```

- Storeys: 1
- Roof: Flat
- Rooms:
  - `storage`: bounds (0, 0, 2, 3), role `Storage`, door on South edge
    (offset 1)
  - `living`: bounds (2, 0, 2, 3), role `Living`, window on East edge
    (offset 1)

## From text to plan object

Parsing produces the same `StructurePlan` the canvas draws and the JSON
format loads. You can parse a line of text, then keep editing the result on
the canvas. The code equivalent is `KitForge.ParseTextPlan` — see the
[API Reference]({{ site.baseurl }}/docs/api/).
