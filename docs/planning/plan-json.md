---
layout: default
title: Plan JSON Format
parent: Planning
nav_order: 3
---

# Plan JSON — `kitforge-plan` v1

A plan is data: rooms on the grid, door and window marks on named edges, a
roof choice, and a seed. The JSON form is the same plan the canvas draws and
the text parser produces — one model, three doors. A person, the Plan Canvas,
or an external tool such as an AI coding agent can author it.

## Example

```json
{
  "kitforge-plan": 1,
  "name": "Sample Outpost",
  "gridSize": 2.0,
  "floors": 1,
  "seed": 12345,
  "roof": { "type": "Flat" },
  "rooms": [
    {
      "id": "room_storage",
      "role": "Storage",
      "bounds": { "x": 0, "y": 0, "width": 4, "height": 3 },
      "edges": [
        { "side": "South", "offset": 1, "mark": "Door" },
        { "side": "East", "offset": 1, "mark": "Window" }
      ]
    }
  ]
}
```

## Fields

### Root

- `kitforge-plan` — format version, always `1`. Required.
- `name` — plan name. Default `Untitled Plan`.
- `gridSize` — grid size in meters. Default `2.0`. Must be greater than zero.
- `floors` — storey count. Default `1`. Must be at least 1.
- `seed` — build seed. The same kit, plan, and seed produce the same
  structure. Default `12345`.
- `roof.type` — `Flat`, `Pitched`, or `None`. Default `Flat`.
- `rooms` — the room list. A plan needs at least one room to build.

### Room

- `id` — room name.
- `role` — `Generic`, `Storage`, `Living`, or `Watch`. The role guides
  interior dressing: Storage favours crates, Living favours a table and bunk.
  Default `Generic`.
- `bounds` — `x`, `y` origin in grid cells, `width` and `height` in cells.
  Width and height must be positive.
- `edges` — marks on the room's boundary. Each has a `side` (`South`,
  `West`, `North`, `East`), an `offset` in cells along that edge, and a
  `mark` (`Door`, `Window`, `Open`, or `Wall`). Default mark `Wall`.

## Compatibility rules

- Unknown fields, at root or room level, are ignored — newer files stay
  readable.
- Missing fields take the defaults above.

## Errors name the field

A malformed plan fails with the field named, never a bare exception:

- Missing or unsupported version: `Missing or invalid 'kitforge-plan' version.`
- `Field 'gridSize' must be greater than zero.`
- `Field 'floors' must be at least 1.`
- `Room '{id}' bounds width and height must be positive.`
- `Edge offset {offset} is out of bounds for room '{id}' on edge {side}.`

Fix the named field and load the plan again. In code, load plans with
`KitForge.LoadPlan` — see the [API Reference]({{ site.baseurl }}/docs/api/).
