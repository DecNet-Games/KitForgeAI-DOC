---
layout: default
title: How Profiling Works
parent: Kit Profiling
nav_order: 1
---

# How Profiling Works

Profiling a kit means scanning every prefab in the kit's folder and recording
what each piece is. To profile, click **Profile a Kit** in the Kit section
and choose the folder — or **Profile the included Fixture Kit** to scan the
sample kit.

## What the profiler reads

For every prefab in the folder, the profiler records:

- **Bounds and pivot** — the piece's measured size and where its pivot sits.
- **Role** — Wall, WallDoor, WallWindow, WallCorner, Floor, RoofFlat,
  RoofPitched, DoorLeaf, Prop, or Unknown.
- **Grid fit** — whether the piece's footprint lands on the detected grid.

## How roles are classified

Roles are classified **first from prefab-name tokens, then from geometry**:

- A wide flat slab reads as a floor or roof piece.
- A tall thin piece reads as a wall.

Naming presets ship for common modular-kit naming conventions, including
POLYGON-style names. A preset is a token map only — it helps the profiler read
names it has seen before; it never changes your prefabs.

![Eleven pieces, every role covered]({{ site.baseurl }}/assets/images/showcase-11.jpg)

## What you get

Profiling writes a **Kit Profile** asset holding the grid size, the role map,
and the per-piece data, and the Kit section shows a summary such as
*"11 pieces ready, grid 2 m, 0 warnings"*.

A warning names the piece and the one action that fixes it: reclassify the
piece, or accept that it is excluded. Every classification is yours to
change — see [Role Overrides & the Profile Asset]({{ site.baseurl }}/docs/kit-profiling/role-overrides/).
