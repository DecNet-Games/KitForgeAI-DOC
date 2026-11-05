---
layout: default
title: FAQ
nav_order: 9
---

# FAQ

## Where do I buy KitForge AI? Is it free on GitHub?

KitForge AI is sold exclusively through the **Unity Asset Store**. This site
is documentation only — there is no free download of the product from GitHub
or anywhere else. See [Installation & Setup]({{ site.baseurl }}/docs/getting-started/installation/).

## Which Unity versions are supported?

Unity **2022.3 LTS** and **Unity 6**. The package is
`com.decnetgames.kitforgeai`, version 1.0.0, with no third-party
dependencies.

## Do I need my own modular kit to use it?

No. The package ships a complete 11-piece **Fixture Kit** (2 m grid) and a
**Sample Outpost** plan, so the first build works minutes after import. When
you are ready, profile your own kit folder instead — see
[Kit Profiling]({{ site.baseurl }}/docs/kit-profiling/).

## What counts as a "kit"?

A folder of prefabs. Loose meshes or FBX files without prefabs are not
supported. The profiler measures every prefab, classifies its role, and
detects the grid the pieces snap to.

## The profiler classified a piece wrong. Can I fix it?

Yes. Every piece's role is a dropdown in the Kit section — change it and the
piece is marked as manually overridden. Re-profiling keeps your overrides;
the profiler never silently takes them back. See
[Role Overrides & the Profile Asset]({{ site.baseurl }}/docs/kit-profiling/role-overrides/).

## A piece does not fit the grid. Will it be stretched to fit?

Never. An off-grid piece is listed in the profile report with its name and
measured size and is excluded from builds by default. You can include it per
piece in the Kit Profile asset; it is then placed at the nearest grid fit,
and the build report says so.

## The Build button is off. Why?

The window always says why. The usual cause: **no kit profiled yet** — the
Kit section says so and the Build button stays off with the reason written
on it. Profile a kit first.

## My plan will not load. What is wrong?

The Plan section names the failing field — errors name the field, never a
bare exception (for example: `Field 'gridSize' must be greater than zero.`).
Fix that field and load again. The full error list is in
[Plan JSON Format]({{ site.baseurl }}/docs/planning/plan-json/).

## Pieces were skipped in the build report. Is that an error?

No — it is information. The kit has no piece for that role. Add a piece with
that role to the kit and re-profile, or remove the mark from the plan. A
wrong piece is never substituted. See
[The Build Report]({{ site.baseurl }}/docs/building/build-report/).

## Can I undo a build?

Yes — a whole build is a single Undo step. Generation writes only into the
structure root it creates, and your kit prefabs are never edited.

## Is the same plan guaranteed to build the same structure?

Yes. Same kit profile, same plan, same seed: the identical structure, every
time. The build report's SHA-256 determinism hash represents the exact
sequence and transforms of placed pieces.

## Does it work at runtime, in a shipped game?

No — generation is an Editor-time tool in v1. Generated structures are
ordinary scene content and work in your builds like anything you placed by
hand. See [What v1 Is Not]({{ site.baseurl }}/docs/what-v1-is-not/).

## Does it follow terrain?

No. Structures build on a flat base at the root's position; sloped-terrain
foundations are not in v1.

## Can an AI coding agent drive it?

Yes. The full workflow is a public C# API that never throws across the
boundary, and the [Agent Guide]({{ site.baseurl }}/docs/api/agent-guide/)
shows the exact workflow: write a plan JSON, call the API, read the build
report.

## How do I remove the sample content?

Delete the two folders Setup created — `Assets/KitForge AI Samples/` and
`Assets/KitForge AI/` — and remove the package with Package Manager. Nothing
is written outside those two folders.
