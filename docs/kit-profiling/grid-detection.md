---
layout: default
title: Grid Detection & Off-Grid Pieces
parent: Kit Profiling
nav_order: 2
---

# Grid Detection & Off-Grid Pieces

KitForge AI builds on **your kit's own grid**. During profiling it measures
the pieces and detects the grid size they snap to — the included Fixture Kit,
for example, profiles as *"grid 2 m"*. Every plan and build then works in
cells of that size, so a 4 × 3-cell room on a 2 m grid is an 8 × 6 m
footprint.

![The Sample Outpost footprint: 4 × 3 cells on a 2 m grid — 8 × 6 m]({{ site.baseurl }}/assets/images/showcase-10.jpg)

## Off-grid pieces

A piece whose footprint does not fit the detected grid is:

- **listed in the profile report** with its name and its measured size,
- **excluded from builds by default** — KitForge AI never scales, stretches,
  or force-fits a piece.

If you want an off-grid piece used anyway, include it per piece in the Kit
Profile asset. It is then placed at the nearest grid fit, and the build
report says so.

Two profiling options govern this behaviour (see also the
[API Reference]({{ site.baseurl }}/docs/api/result-and-configuration-types/)):

- `GridTolerance` — grid alignment tolerance in meters (default 0.05 m).
- `ExcludeOffGrid` — whether off-grid pieces are excluded from assembly by
  default (default `true`).

## Kits that are not on a grid

A kit is a folder of prefabs. Kits whose pieces do not snap to a consistent
grid are reported off-grid and excluded, not force-fitted — freeform kits are
outside v1's scope (see [What v1 Is Not]({{ site.baseurl }}/docs/what-v1-is-not/)).
Loose meshes or FBX files without prefabs are not supported either.
