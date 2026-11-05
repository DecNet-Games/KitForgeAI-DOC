---
layout: default
title: Building & Assembly Rules
parent: Building
nav_order: 1
---

# Building & Assembly Rules

In the **Build** section, click **Build Structure**. The assembly engine
reads the Kit Profile and the plan, and places pieces cell by cell on the
kit's grid.

## What gets placed

- **Perimeter walls** along every room boundary, with correct rotations.
- **Corners** where two walls meet, using the kit's WallCorner pieces.
- **Door and window pieces** at the marked edges — the plan's `Door` and
  `Window` marks substitute the matching WallDoor / WallWindow pieces, and a
  door leaf where the kit provides one.
- **Floor slabs** on the kit grid.
- **Storeys** — add floors in the plan to stack the structure.
- **Roofs** — a flat or pitched roof closes the top when your kit provides
  the pieces and the plan asks for one.

![Macro detail of a built structure]({{ site.baseurl }}/assets/images/cap-build-detail.jpg)

## When a piece is missing

If the kit has no piece for a role, **the structure still builds** and the
skip is reported — by role, with the reason — in the
[build report]({{ site.baseurl }}/docs/building/build-report/). A wrong piece
is never substituted.

## Determinism

The build is deterministic: same kit profile, same plan, same seed — the
identical structure, every time. The build report carries a SHA-256
determinism hash over the exact sequence and transforms of placed pieces, so
you can prove two builds are identical.

## Safety rules

- **One Undo.** A whole build is a single Undo step.
- Generation writes only into the structure root it creates.
- Your kit prefabs are never edited.
- Structures build on a flat base at the root's position — there is no
  terrain conforming in v1 (see [What v1 Is Not]({{ site.baseurl }}/docs/what-v1-is-not/)).
