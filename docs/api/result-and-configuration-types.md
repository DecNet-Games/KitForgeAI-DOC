---
layout: default
title: Result & Configuration Types
parent: API Reference
nav_order: 2
---

# Result & Configuration Types

## Result types

### `ProfileResult`

- `bool Success` — true if profiling succeeded.
- `string ErrorMessage` — diagnostic explanation if profiling failed.
- `KitProfile Profile` — the generated or updated KitProfile asset.
- `int PieceCount` — total prefabs scanned in the kit.
- `List<string> Warnings` — warnings for off-grid pieces or classification
  anomalies.

### `PlanResult`

- `bool Success` — true if plan loading or parsing succeeded.
- `string ErrorMessage` — named field error if the plan is invalid.
- `StructurePlan Plan` — the validated StructurePlan data model.

### `BuildResult`

- `bool Success` — true if assembly succeeded.
- `string ErrorMessage` — error description if assembly failed.
- `GameObject RootObject` — the instantiated scene root GameObject.
- `BuildReport Report` — detailed census and placement report.

## `BuildReport`

- `bool success` — true if the build completed without fatal errors.
- `string summary` — human-readable outcome summary line.
- `int totalPlaced` — total count of modular pieces instantiated.
- `int totalSkipped` — total count of piece placements skipped due to
  missing kit roles.
- `string determinismHash` — SHA-256 hash representing the exact sequence
  and transforms of placed pieces.
- `List<CensusEntry> census` — breakdown of placed piece counts per role.
- `List<SkippedPieceEntry> skippedPieces` — details of skipped roles and
  plain-language reasons.
- `List<string> warnings` — diagnostic placement warnings.

See also [The Build Report]({{ site.baseurl }}/docs/building/build-report/).

## Configuration & options

### `BuildOptions`

- `int Seed` — pseudorandom seed for deterministic placement
  (default: 12345).
- `InteriorDensity Density` — prop density setting (`Empty`, `Sparse`,
  `Furnished`).
- `string RootName` — custom name for the root GameObject.
- `bool ClearExisting` — whether to clear an existing structure root before
  rebuilding.

### `ProfilingOptions`

- `float GridTolerance` — grid alignment tolerance in meters
  (default: 0.05 m).
- `bool ExcludeOffGrid` — whether to exclude off-grid pieces from assembly
  by default (default: `true`).

## Enums

- **`PieceRole`**: `Unknown`, `Wall`, `WallDoor`, `WallWindow`, `WallCorner`,
  `Floor`, `RoofFlat`, `RoofPitched`, `DoorLeaf`, `Prop`.
- **`RoofType`**: `None`, `Flat`, `Pitched`.
- **`RoomRole`**: `Generic`, `Storage`, `Living`, `Watch`.
- **`EdgeSide`**: `South`, `West`, `North`, `East`.
- **`EdgeMarkType`**: `Wall`, `Door`, `Window`, `Open`.
- **`InteriorDensity`**: `Empty`, `Sparse`, `Furnished`.
