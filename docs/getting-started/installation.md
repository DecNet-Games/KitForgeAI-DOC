---
layout: default
title: Installation & Setup
parent: Getting Started
nav_order: 1
---

# Installation & Setup

## 1. Get KitForge AI from the Unity Asset Store

KitForge AI is sold **exclusively through the Unity Asset Store**. There is no
free download of the product from GitHub or anywhere else — this site is
documentation only. If a page offers you the tool itself for free, it is not
us.

- Package: `com.decnetgames.kitforgeai`
- Version: 1.0.0
- Requires: Unity **2022.3 LTS** or **Unity 6**
- Dependencies: none

## 2. Import the package

1. Open your project in Unity.
2. Open **Window > Package Manager**, choose **My Assets**, find
   **KitForge AI**, and click **Download**, then **Import** — or import the
   package from the Asset Store window directly.
3. Three samples ship with the package and are offered in Package Manager:
   **Fixture Kit** (the included 11-piece modular snap kit on a 2 m grid),
   **Sample Outpost** (a sample scene and plan files), and **API Example**
   (a headless C# driving script). You can import them from Package Manager,
   or let Setup import them for you in the next step.

## 3. Open the window and run Setup

Choose **Tools > Decnet Games > KitForge AI > Open KitForge AI**. The first
open shows the welcome screen with the product name, the version, and the
quick actions.

![The KitForge AI welcome screen on first run]({{ site.baseurl }}/assets/images/cap-welcome.jpg)

Click **Run Setup / Verify Install**. Setup:

- checks the install,
- imports the Fixture Kit, Sample Outpost, and API Example samples into
  `Assets/KitForge AI Samples/`,
- creates your working folder `Assets/KitForge AI/`,
- reports each thing it did, in plain language, in a setup report.

![The setup report after Run Setup]({{ site.baseurl }}/assets/images/cap-setup-report.jpg)

Setup is safe to run again: running it a second time changes nothing and
never overwrites a sample copy you edited.

![Setup and documentation are one click from the Get Started section]({{ site.baseurl }}/assets/images/showcase-14.jpg)

## 4. Removing KitForge AI content

There is no one-action uninstaller in v1. To remove the sample content,
delete the two folders Setup created — `Assets/KitForge AI Samples/` and
`Assets/KitForge AI/` — and remove the package from your project with
Package Manager. Nothing is written outside those two folders.

## Next step

[Quick Start]({{ site.baseurl }}/docs/getting-started/quick-start/) — profile the included kit, load the sample plan, and build your first structure.
