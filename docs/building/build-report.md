---
layout: default
title: The Build Report
parent: Building
nav_order: 3
---

# The Build Report

Every build ends with a report. In the window it appears **under the Build
Structure button**; in code it is the `BuildReport` inside the `BuildResult`.

![The build report in the Build section]({{ site.baseurl }}/assets/images/cap-build-report.jpg)

The report under the button reads how many pieces were placed and names
anything that was skipped, with the reason.

## BuildReport fields

- `success` — true if the build completed without fatal errors.
- `summary` — a human-readable outcome summary line.
- `totalPlaced` — total count of modular pieces instantiated.
- `totalSkipped` — total count of piece placements skipped due to missing
  kit roles.
- `determinismHash` — SHA-256 hash representing the exact sequence and
  transforms of placed pieces. Same profile, plan, and seed → same hash.
- `census` — breakdown of placed piece counts per role (`CensusEntry`:
  role + count).
- `skippedPieces` — details of skipped roles and plain-language reasons
  (`SkippedPieceEntry`).
- `warnings` — diagnostic placement warnings.

## Reading a skip

A skip is information, not an error: it means the plan asked for a piece role
your kit does not contain (or contains only off-grid — see
[Grid Detection & Off-Grid Pieces]({{ site.baseurl }}/docs/kit-profiling/grid-detection/)).
Fix it by adding a piece with that role to the kit and re-profiling, or by
removing the mark from the plan.

> **Pro Tip:** When you write to support, include the build report text from
> the Build section — with your Unity version and the kit name from your Kit
> Profile, it is usually enough to reproduce the issue. See
> [Support]({{ site.baseurl }}/docs/support/).
