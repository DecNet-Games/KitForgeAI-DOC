---
layout: default
title: API Reference
nav_order: 6
has_children: true
permalink: /docs/api/
---

# API Reference

The whole KitForge AI workflow is a public C# API in the namespace
`DecnetGames.KitForgeAI` — the same operations the home window performs.

- Assembly: `DecnetGames.KitForgeAI.Editor.dll` (Facade and Profiler) /
  `DecnetGames.KitForgeAI.Runtime.dll` (Data Model and Serializers)
- Facade constants: `KitForge.PackageId` = `"com.decnetgames.kitforgeai"`,
  `KitForge.Version` = `"1.0.0"`

**Every public method returns a result object and never throws across the
public boundary.** Check `Success`; if it is false, `ErrorMessage` contains
the exact problem and the fixing action.

- [Facade Methods]({{ site.baseurl }}/docs/api/facade-methods/) — `ProfileKit`, `LoadPlan`, `ParseTextPlan`, `Build`, `ReDress`.
- [Result & Configuration Types]({{ site.baseurl }}/docs/api/result-and-configuration-types/) — the result objects, `BuildReport`, options, and enums.
- [Agent Guide]({{ site.baseurl }}/docs/api/agent-guide/) — how an AI coding agent drives KitForge AI end to end.
