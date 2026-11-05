# PUSH NOTE — KitForgeAI-DOC (built 2026-11-05, local only, NOT pushed)

## What this folder is

The complete, push-ready source tree for KitForge AI's documentation site,
rebuilt to the Decnet house "-DOC" pattern (master prompt:
`~/workspace/unity-listings/perch-docsite-prompt.md`):

- Just the Docs Jekyll site via `remote_theme` (no `theme:` gem key, no
  `just-the-docs` gem in the Gemfile — the pairing that fixed the two known
  GitHub Pages errors: "The just-the-docs theme could not be found" and
  "The github-pages gem can't satisfy your Gemfile's dependencies").
- 29 content pages: Home + Getting Started (3) + Kit Profiling (3) +
  Planning (4) + Building (3) + API Reference (3) + Samples (3) +
  What v1 Is Not + FAQ + Support, with section landing pages.
- Real media only, repo-relative under `assets/`: cover, demo video
  (`assets/video/kitforge-demo.mp4`), profile-plan-build GIF, 15 showcase
  images, 10 real editor captures (store proofs resized to JPG ≤1600 px,
  whole assets folder ≈ 6.5 MB). Content sourced solely from the shipped
  `Documentation~` (copies in `../work/docs-src/`) + verified product facts.
- The old single-page build in `../docs-site/` was left untouched as
  reference; this tree supersedes it.

## Exact repo to create

- **Name:** `KitForgeAI-DOC`
- **Owner:** `DecNet-Games` (GitHub org account)
- **Visibility:** public (required for GitHub Pages on this setup)
- **Live URL once Pages is on:** https://decnet-games.github.io/KitForgeAI-DOC/
  (matches the `baseurl: "/KitForgeAI-DOC"` already set in `_config.yml`)

## Push route (do this from the laptop, per the standing no-card-spam rule)

Bulk pushes go via laptop git over SSH — never the GitHub connector.

1. BOSS creates the empty repo `DecNet-Games/KitForgeAI-DOC` on GitHub
   (no README, no .gitignore — this tree carries its own).
2. Copy this folder's contents to the laptop clone location, then:
   `git init` (if needed) → `git add .` → `git commit` → the final
   `git push` is BOSS's own ~10-second action at his terminal (laptop git
   credentials only work interactively — known constraint).
3. On GitHub: repo **Settings → Pages → Build and deployment → Source:
   GitHub Actions** (the standard github-pages workflow), or "Deploy from a
   branch" → `main` / root if Actions is unavailable. PERCH-DOC/PULSE-DOC
   run on the same org setup — mirror whichever source they use.
4. After the first successful build, verify:
   - the live URL loads with the Just the Docs theme (no theme error),
   - Home shows the cover, GIF, and the demo video plays,
   - nav order: Home, Getting Started, Kit Profiling, Planning, Building,
     API Reference, Samples, What v1 Is Not, FAQ, Support.
5. Only after the site is live: the portal listing description for KitForge
   AI can carry the house link line with
   `DOCUMENTATION → https://decnet-games.github.io/KitForgeAI-DOC/`
   (dead-link rule: never publish the link before the site resolves).

## What remains

- Repo creation + push + Pages enable: BOSS-side steps above (by design —
  this build stopped at a complete local tree, per instructions).
- Nothing in the tree itself: content, config, Gemfile, and media are
  complete and internally verified (page count, front matter, parent/nav
  links, and every asset reference checked against disk).
