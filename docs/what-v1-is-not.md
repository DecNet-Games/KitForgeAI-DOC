---
layout: default
title: What v1 Is Not
nav_order: 8
---

# What v1 Is Not

The honest scope list for KitForge AI version 1. If a workflow you need is on
this page, it is not in this version — plan around that, or write to
[support@decnetgames.com](mailto:support@decnetgames.com) and say which one
matters to you.

- **No runtime (in-game) generation.** Generation is an Editor tool.
  Generated structures are ordinary scene content and work in builds like
  anything you placed by hand.
- **No terrain conforming.** Structures build on a flat base at the root's
  position. Sloped-terrain foundations are not in v1.
- **No freeform or non-grid kits.** Kits whose pieces do not snap to a
  consistent grid are reported off-grid and excluded, not force-fitted.
- **No diagonal or curved walls.** Footprints are grid rectangles; rooms may
  combine into L and T shapes via multiple rectangles.
- **No interior furnishing beyond the kit's own Prop pieces.** Dressing uses
  the pieces your kit provides, placed by room role and density.
- **No cloud or language-model plan generation.** The text parser is a
  local, documented grammar ([Text Plan Grammar]({{ site.baseurl }}/docs/planning/text-plan-grammar/))
  that runs on your machine.
- **No one-action uninstaller.** To remove the sample content, delete the
  two folders Setup created: `Assets/KitForge AI Samples/` and
  `Assets/KitForge AI/`. Nothing else is written outside them.
- **No support for kits stored as loose meshes or FBX files without
  prefabs.** A kit is a folder of prefabs.
