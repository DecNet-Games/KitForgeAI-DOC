---
layout: default
title: Interior Dressing
parent: Building
nav_order: 2
---

# Interior Dressing

A built shell is only half a structure. KitForge AI also dresses the
interior — using **your kit's own Prop pieces**, placed by room role and by a
density you choose.

![Stand inside what you planned — the dressed interior at ground level]({{ site.baseurl }}/assets/images/showcase-09.jpg)

## Dressing by room role

Each room's role guides which props the builder favours:

- **Storage** favours crates.
- **Living** favours a table and bunk.
- **Generic** and **Watch** take the neutral selection.

Roles are set per room in the plan — on the
[canvas]({{ site.baseurl }}/docs/planning/plan-canvas/), in the
[text grammar]({{ site.baseurl }}/docs/planning/text-plan-grammar/) (`role storage`),
or in [JSON]({{ site.baseurl }}/docs/planning/plan-json/) (`"role": "Storage"`).

## Density

The Build section's interior-density control sets how full rooms get:
`Empty`, `Sparse`, or `Furnished` (the `InteriorDensity` enum in code).

## Re-dressing

Changed your mind about the furniture? **Re-dressing replaces only the
interior** — the shell is untouched. In the window, re-run dressing with new
settings; in code, call `KitForge.ReDress(root, profile, plan, seed)` with a
new seed to re-roll the arrangement (see the
[API Reference]({{ site.baseurl }}/docs/api/facade-methods/)).

> Dressing uses the pieces your kit provides. There is no furnishing beyond
> the kit's own Prop pieces in v1 — if a room role favours a prop your kit
> does not have, that placement is skipped and reported like any other skip.
