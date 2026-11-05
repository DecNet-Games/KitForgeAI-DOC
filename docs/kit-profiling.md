---
layout: default
title: Kit Profiling
nav_order: 3
has_children: true
permalink: /docs/kit-profiling/
---

# Kit Profiling

Profiling is how KitForge AI learns your kit. You point it at a folder of kit
prefabs; it measures each prefab, classifies its role, detects the grid, and
saves the result as a **Kit Profile** asset that your builds use.

- [How Profiling Works]({{ site.baseurl }}/docs/kit-profiling/how-profiling-works/) — what the profiler reads, how roles are classified, and the naming presets.
- [Grid Detection & Off-Grid Pieces]({{ site.baseurl }}/docs/kit-profiling/grid-detection/) — how the grid is found, and what happens to pieces that do not fit it.
- [Role Overrides & the Profile Asset]({{ site.baseurl }}/docs/kit-profiling/role-overrides/) — changing any classification, the summary line, and saving the profile.

![The profiler reads your pieces — you confirm the roles]({{ site.baseurl }}/assets/images/showcase-03.jpg)

> **Pro Tip:** Builds read the Kit Profile asset, not the raw folder — so a build is the same on every machine that has the profile. Keep the profile with your project.
