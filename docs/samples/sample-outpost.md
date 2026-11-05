---
layout: default
title: Sample Outpost
parent: Samples
nav_order: 2
---

# Sample Outpost

The Sample Outpost is the worked example that ships with the package: a
sample scene and plan files for generating the sample outpost from the
Fixture Kit (Package Manager sample **Sample Outpost**, path
`Samples~/SampleOutpost`).

## The plan

- **Footprint:** 4 × 3 cells on the Fixture Kit's 2 m grid — 8 × 6 m
- **Floors:** 1
- **Openings:** 1 door (South, offset 1), 1 window (East, offset 1)
- **Roof:** Flat
- **Room role:** Storage

![The Sample Outpost footprint: 8 × 6 m]({{ site.baseurl }}/assets/images/showcase-10.jpg)

The shipped plan line (the text form of the same plan) is exactly:

```text
outpost 4x3, door south at 1, windows east at 1, flat roof, role storage
```

## Build it

1. Run Setup (imports the samples).
2. **Profile the included Fixture Kit** in the Kit section.
3. **Load the Sample Outpost Plan** in the Plan section — the plan summary
   appears in plain language.
4. **Build Structure** in the Build section.

![The built Sample Outpost, aerial view]({{ site.baseurl }}/assets/images/cap-scene-outpost.jpg)

![The built Sample Outpost in the Game view]({{ site.baseurl }}/assets/images/cap-game-view.jpg)

The outpost assembles in the scene: walls, a door, windows, a flat roof, and
a dressed interior. The build report under the button reads how many pieces
were placed and names anything that was skipped, with the reason. One Undo
removes the whole generated structure.
