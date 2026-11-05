---
layout: default
title: The Plan Canvas
parent: Planning
nav_order: 1
---

# The Plan Canvas

The Plan Canvas is a top-down grid surface in the Plan section of the home
window. It is the fastest way to design a structure by hand.

![Draw the plan on the canvas]({{ site.baseurl }}/assets/images/showcase-05.jpg)

## Working on the canvas

- **Drag** to add a room as a rectangle of grid cells.
- **Click a room edge** to cycle the door and window marks on that edge.
- **Set floors and roof** with the plan parameter fields — and a room's role
  (Generic, Storage, Living, Watch) where the room should be dressed
  differently.
- **Remove or undo** edits with the canvas controls (Remove Selected Room,
  Undo Edit).

![Set floors, choose the roof]({{ site.baseurl }}/assets/images/showcase-12.jpg)

## Reading the plan

Before you build, the window shows the plan summary in plain language:
footprint, floors, doors, windows, and roof. The canvas, the text parser, and
a JSON file all produce the same plan object — editing on the canvas edits
the same data the other two doors produce.

![One room, fully specified — the Sample Outpost read straight from its plan]({{ site.baseurl }}/assets/images/showcase-07.jpg)

Rooms can combine into **L and T shapes** via multiple rectangles. Footprints
are grid rectangles: there are no diagonal or curved walls in v1 (see
[What v1 Is Not]({{ site.baseurl }}/docs/what-v1-is-not/)).
