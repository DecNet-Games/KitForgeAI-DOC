---
layout: default
title: Rooms, Roles & Edge Marks
parent: Planning
nav_order: 4
---

# Rooms, Roles & Edge Marks

The reference for the three vocabularies every plan uses — whether you draw
it on the canvas, describe it in text, or write it as JSON.

## Rooms

A room is a rectangle of grid cells: an origin (`x`, `y` in cells) and a size
(`width` × `height` in cells). Multiple rooms combine into larger footprints,
including **L and T shapes** built from several rectangles. A plan needs at
least one room to build.

## Room roles

A room's role guides interior dressing — which of your kit's Prop pieces the
builder favours for that room.

| Role | Dressing behaviour |
|---|---|
| `Generic` | Default. No special favour. |
| `Storage` | Favours crates. |
| `Living` | Favours a table and bunk. |
| `Watch` | A watch-room role, for towers and posts. |

In JSON the role is the room's `role` field; in the text grammar it is
`role [role]` or `[role] room`; in the API it is the `RoomRole` enum
(`Generic`, `Storage`, `Living`, `Watch`).

## Edge sides

Every mark sits on one named side of a room's boundary:

`South` · `West` · `North` · `East`

In the text grammar the sides are written lowercase: `south`, `north`,
`east`, `west`.

## Edge marks

| Mark | Meaning |
|---|---|
| `Wall` | A plain wall piece. The default when no mark is set. |
| `Door` | A door-wall piece at this cell, with the door leaf where the kit provides one. |
| `Window` | A window-wall piece at this cell. |
| `Open` | No wall piece — an open edge. |

Each mark also carries an `offset`: the cell index along that edge, counting
from the room's origin corner. An offset outside the edge fails with the
field named — see [Plan JSON Format]({{ site.baseurl }}/docs/planning/plan-json/).

## How marks become pieces

At build time each marked cell is filled from the profiled kit by role: a
`Door` mark asks for a **WallDoor** piece, a `Window` mark for a
**WallWindow** piece, a corner where two walls meet for a **WallCorner**
piece. If the kit has no piece for a role, the structure still builds and the
skip is reported by role — a wrong piece is never substituted. See
[Building & Assembly Rules]({{ site.baseurl }}/docs/building/assembly-rules/).
