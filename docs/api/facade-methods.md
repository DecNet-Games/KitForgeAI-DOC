---
layout: default
title: Facade Methods
parent: API Reference
nav_order: 1
---

# Facade Methods — `KitForge`

The static `KitForge` facade is the primary entry point for KitForge AI
operations. All methods return result objects and never throw exceptions
across the public boundary.

## Constants

- `string PackageId`: `"com.decnetgames.kitforgeai"`
- `string Version`: `"1.0.0"`

## Methods

### `ProfileResult ProfileKit(string folderPath, ProfilingOptions options = null)`

Profiles a modular kit folder, classifying prefabs and detecting grid
dimensions.

- `folderPath`: project-relative or absolute path to the kit prefab folder.
- `options`: optional profiling configuration parameters.
- **Returns:** a `ProfileResult` containing the generated `KitProfile` or a
  failure description.

### `PlanResult LoadPlan(string jsonOrPath)`

Loads and validates a structure plan from a JSON string or file path.

- `jsonOrPath`: raw JSON string or file path to a `kitforge-plan: 1` file.
- **Returns:** a `PlanResult` containing the loaded `StructurePlan` or a
  failure description.

### `PlanResult ParseTextPlan(string textDescription)`

Parses a concise structured text description into a `StructurePlan` using the
local grammar (see [Text Plan Grammar]({{ site.baseurl }}/docs/planning/text-plan-grammar/)).

- `textDescription`: the structured description string.
- **Returns:** a `PlanResult` containing the parsed `StructurePlan` or a
  failure description.

### `BuildResult Build(KitProfile profile, StructurePlan plan, BuildOptions options = null)`

Assembles a complete modular structure from a kit profile and structure plan.

- `profile`: profiled kit asset containing classified prefab roles.
- `plan`: structure plan specifying dimensions, openings, and roof style.
- `options`: optional build settings (`Seed`, `Density`, `RootName`).
- **Returns:** a `BuildResult` containing the instantiated root GameObject
  and the detailed `BuildReport`.

### `BuildResult ReDress(GameObject structureRoot, KitProfile profile, StructurePlan plan, int seed)`

Replaces interior props in an existing generated structure without altering
the structural shell.

- `structureRoot`: root GameObject of an existing generated structure.
- `profile`: profiled kit asset.
- `plan`: structure plan.
- `seed`: random seed for prop scattering.
- **Returns:** a `BuildResult` containing the updated structure root and
  report.

> See the [Agent Guide]({{ site.baseurl }}/docs/api/agent-guide/) for a complete worked workflow using these methods, and the [API Example sample]({{ site.baseurl }}/docs/samples/api-example/) for a runnable driver.
