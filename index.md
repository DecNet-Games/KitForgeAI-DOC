---
layout: home
title: Home
nav_order: 1
description: "KitForge AI builds structures from your own modular kit. Point it at a folder of kit prefabs, draw or describe the plan, and it assembles the structure on your kit's own grid."
permalink: /
---

# KitForge AI
{: .fs-9 }

Build structures from **your own modular kit**. Point KitForge AI at a folder of kit prefabs, draw or describe the plan, and it assembles the structure on your kit's own grid — from native prefabs you can keep editing by hand.
{: .fs-6 .fw-300 }

[Get started]({{ site.baseurl }}/docs/getting-started/){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Buy on the Unity Asset Store](https://assetstore.unity.com/publishers/118262){: .btn .fs-5 .mb-4 .mb-md-0 }

![KitForge AI — build structures from your own modular kit]({{ site.baseurl }}/assets/images/cover.png)

---

## Stop placing the same walls one piece at a time

If you build levels with a modular snap kit, you know the cost: hours spent placing the same walls, corners, doors and roofs, one piece at a time, every time the layout changes. KitForge AI takes over the repetitive assembly.

- **Profile** — point it at the kit you already own. It measures every piece, detects the grid, and classifies each piece's role. Every classification is yours to override.
- **Plan** — draw the plan on a canvas, describe it in a short line of text, or write it as JSON. All three produce the same plan.
- **Build** — one click assembles the structure: walls, corners, door and window pieces, floor slabs, roofs, and a dressed interior. The whole build is a single Undo step.

<video controls width="100%" poster="{{ site.baseurl }}/assets/images/showcase-01.jpg">
  <source src="{{ site.baseurl }}/assets/video/kitforge-demo.mp4" type="video/mp4">
</video>

*The full loop — profile, plan, build — in the real editor window.*

![Profile, plan, build]({{ site.baseurl }}/assets/images/profile-plan-build.gif)

## Why developers use it

> **Pro Tip:** The pieces KitForge AI places are ordinary instances of *your* prefabs under one structure root. Select them, move them, re-material them — there is no black-box mesh to fight with afterwards.

- **Your kit, not ours.** A kit is a folder of prefabs you already own — commercial snap kits or your own. Naming presets ship for common conventions, including POLYGON-style names.
- **Deterministic.** Same kit profile, same plan, same seed: the identical structure, every time, verified by a SHA-256 determinism hash in the build report.
- **Honest about fit.** A piece that does not fit the grid is reported by name with its measured size and excluded — never scaled, stretched, or force-fitted.
- **Drivable from code.** The full workflow is a public C# API, and every build returns a structured report: what was placed, what was skipped, and why.

## Quick links

- [Installation & Setup]({{ site.baseurl }}/docs/getting-started/installation/) — Asset Store import, one-click Setup, and what Setup creates.
- [Quick Start]({{ site.baseurl }}/docs/getting-started/quick-start/) — from import to a standing sample outpost.
- [Kit Profiling]({{ site.baseurl }}/docs/kit-profiling/) — how your kit becomes a Kit Profile.
- [Planning]({{ site.baseurl }}/docs/planning/) — the Plan Canvas, the text-plan grammar, and the `kitforge-plan` JSON format.
- [API Reference]({{ site.baseurl }}/docs/api/) — the public C# API, result types, and the agent guide.
- [What v1 Is Not]({{ site.baseurl }}/docs/what-v1-is-not/) — the honest scope list for this version.

## Requirements

- Unity **2022.3 LTS** or **Unity 6** (package `com.decnetgames.kitforgeai`, version 1.0.0).
- Editor-only tool — nothing ships inside your player build.
- No third-party dependencies. Generation runs entirely on your machine: no network calls, no external service.
