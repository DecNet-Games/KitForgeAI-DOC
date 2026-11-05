---
layout: default
title: Role Overrides & the Profile Asset
parent: Kit Profiling
nav_order: 3
---

# Role Overrides & the Profile Asset

The profiler's classification is a starting point, not a verdict. Every
classification is yours to change.

![Every role is yours to override]({{ site.baseurl }}/assets/images/showcase-04.jpg)

## Overriding a role

In the Kit section, each piece lists its role in a dropdown. Change it, and
the piece is marked as **manually overridden**. Re-profiling the same kit
keeps your overrides — the profiler never silently takes them back.

![From empty kit to ready kit: the profile before and after]({{ site.baseurl }}/assets/images/showcase-13.jpg)

## The summary line

After profiling, the Kit section shows a summary such as:

> "11 pieces ready, grid 2 m, 0 warnings"

A warning names the piece and the one action that fixes it: reclassify the
piece, or accept that it is excluded.

![The full piece list with every role, in the real window]({{ site.baseurl }}/assets/images/cap-kit-profiler-full.jpg)

## Saving the profile

Profiling writes a **Kit Profile** asset holding:

- the grid size,
- the role map (including your overrides),
- the per-piece data.

Keep it with your project. Builds read the profile, not the raw folder, so a
build is the same on every machine that has the profile.
