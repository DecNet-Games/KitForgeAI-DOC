---
layout: default
title: The Home Window
parent: Getting Started
nav_order: 3
---

# The Home Window

Everything in KitForge AI happens in one Editor window:
**Tools > Decnet Games > KitForge AI > Open KitForge AI**.

![The KitForge AI home window]({{ site.baseurl }}/assets/images/cap-layout.jpg)

## The welcome screen and the next-step card

The first open shows the full welcome: the product name, the version, and the
quick actions — **Run Setup / Verify Install**, profile the included kit,
load the sample plan. After that, the window opens as a tool, with your last
section, profile, and plan remembered.

A **next-step card** always names the single next action for where you are:
run Setup, profile a kit, load a plan, build. You never have to guess which
step comes next — follow the card.

## The three sections

### Kit

The profile summary and role overrides. It shows the summary line (for
example *"11 pieces ready, grid 2 m, 0 warnings"*), every profiled piece with
its role in a dropdown you can change, and the **Profile a Kit** /
**Profile the included Fixture Kit** actions. Details:
[Kit Profiling]({{ site.baseurl }}/docs/kit-profiling/).

### Plan

The plan summary and its three inputs — the **Plan Canvas**, the
**Parse Description** text field, and loading a **plan JSON** file — plus the
plan parameters: floors, roof, and seed. Before you build, the window shows
the plan summary in plain language: footprint, floors, doors, windows, and
roof. Details: [Planning]({{ site.baseurl }}/docs/planning/).

### Build

The **Build Structure** button, the seed and interior-density controls, and —
after a build — the **build report** under the button: how many pieces were
placed, and anything that was skipped, with the reason. Details:
[Building]({{ site.baseurl }}/docs/building/).

## Reversible by design

- A whole build is a **single Undo step**.
- Generation writes only into the structure root it creates.
- Your kit prefabs are never edited.
