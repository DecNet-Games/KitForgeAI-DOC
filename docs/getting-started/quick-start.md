---
layout: default
title: Quick Start
parent: Getting Started
nav_order: 2
---

# Quick Start

From import to a standing sample outpost, using only the home window. The
window's next-step card names the current step the whole way. If you have not
installed yet, start with [Installation & Setup]({{ site.baseurl }}/docs/getting-started/installation/).

![Profile, plan, build]({{ site.baseurl }}/assets/images/profile-plan-build.gif)

## 1. Open the window

Choose **Tools > Decnet Games > KitForge AI > Open KitForge AI**. The welcome
screen shows the product name, the version, and the quick actions.

## 2. Run Setup

Click **Run Setup / Verify Install**. Setup checks the install, imports the
Fixture Kit, Sample Outpost, and API Example samples into
`Assets/KitForge AI Samples/`, and creates your working folder
`Assets/KitForge AI/`. It reports each thing it did in plain language.
Running Setup again changes nothing and never overwrites a sample copy you
edited.

## 3. Profile the included kit

In the **Kit** section, click **Profile the included Fixture Kit**. KitForge
AI scans the 11 pieces, classifies each piece's role, and detects the 2 m
grid. The summary line reads how many pieces are ready and how many warnings
the kit has.

![The Kit section after profiling the Fixture Kit]({{ site.baseurl }}/assets/images/cap-kit-profiler.jpg)

To use your own kit instead, click **Profile a Kit** and choose its folder —
see [Kit Profiling]({{ site.baseurl }}/docs/kit-profiling/).

## 4. Load the sample plan

In the **Plan** section, click **Load the Sample Outpost Plan**. The plan
summary appears in plain language: rooms, footprint, floors, doors, windows,
and roof.

![The Plan Canvas with the Sample Outpost room placed]({{ site.baseurl }}/assets/images/cap-plan-canvas.jpg)

## 5. Build the structure

In the **Build** section, click **Build Structure**. The outpost assembles in
the scene: walls, a door, windows, a flat roof, and a dressed interior. The
build report under the button reads how many pieces were placed and names
anything that was skipped, with the reason.

![The build report after building the Sample Outpost]({{ site.baseurl }}/assets/images/cap-build-report.jpg)

Every placed piece is an instance of a kit prefab — select it, move it, keep
editing it. One Undo removes the whole generated structure.

![The built Sample Outpost in the scene]({{ site.baseurl }}/assets/images/cap-scene-outpost.jpg)

## 6. Make it yours

- **Draw your own plan** on the canvas in the Plan section: drag to add a
  room, click a room edge to cycle door and window marks, set floors and
  roof. See [The Plan Canvas]({{ site.baseurl }}/docs/planning/plan-canvas/).
- **Describe it in text** in the Parse Description field — the grammar is in
  [Text Plan Grammar]({{ site.baseurl }}/docs/planning/text-plan-grammar/).
- **Profile your own kit** and build your structures from your own pieces.

## If something stops you

- **No kit profiled yet** — the Kit section says so and the Build button
  stays off with the reason written on it. Profile a kit first.
- **A plan field is wrong** — the Plan section names the failing field. Fix
  that field and load again.
- **Pieces skipped in the report** — the kit has no piece for that role. Add
  a piece with that role to the kit, or remove the mark from the plan.

More answers are in the [FAQ]({{ site.baseurl }}/docs/faq/).
