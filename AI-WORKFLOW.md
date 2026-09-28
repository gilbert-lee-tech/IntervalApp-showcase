# How I built this with Claude Code

I rewrote Interval App from Apache Cordova to React + TypeScript with [Claude Code](https://www.anthropic.com/claude-code), Anthropic's agentic coding tool, as my pair programmer. I owned the plan, the decisions and every review and merge; Claude Code did most of the hands-on implementation. This page shows what that looked like, using numbers taken straight from the project's (private) Git history.

## How I worked

- **I planned the rewrite in phases** (scaffold, data, components, audio, PWA, deployment, cleanup) and gave Claude Code one phase or feature at a time.
- **Every change went through its own branch and pull request.** Claude Code wrote the code, ran the build and checks, and opened the PR; I reviewed and merged every one myself.
- **Production only changes through a reviewed promotion.** Work lands on an integration branch first, which deploys to a preview site; a separate PR promotes it to production.
- **Project rules live in a `CLAUDE.md` file** in the repo, which Claude Code reads at the start of every session: architecture notes, the Git workflow, and hard-won "don't do this" lessons. Keeping it up to date is part of the work, as the timeline below shows.

## By the numbers

| | |
|---|---|
| Calendar days | 7 (Sep 21–27, 2026) |
| First commit to live in production | about 2 days (Sep 21 → Sep 23) |
| Pull requests merged | 35 (30 changes + 5 promotions to production) |
| Commits (excluding merges) | 65, of which **63 co-authored with Claude** |
| The other 2 | the initial import of the old app from GitLab |
| Merge commits | 35, **every one a PR I reviewed and merged** |

## Timeline

Every merged pull request, grouped by stage (dates are Pacific time). Phase numbers follow the original plan; there was no separate Phase 6 PR.

### Rewrite, phase by phase

| PR | Merged | Title |
|---|---|---|
| #2 | Sep 22 | Phase 1: Scaffold Vite + React + TypeScript project |
| #3 | Sep 22 | Phase 2: Interval/note data, asset-existence check, copy assets |
| #4 | Sep 22 | Phase 3: Interval/mode/note components, ported CSS |
| #5 | Sep 22 | Phase 4: Real audio playback |
| #6 | Sep 23 | Phase 5: PWA — manifest, icons, offline-capable service worker |
| #7 | Sep 23 | Phase 7: Prepare for Cloudflare deployment |
| #8 | Sep 23 | Phase 7b: Add wrangler config for Cloudflare's unified deploy flow |
| #9 | Sep 23 | Phase 7c: Fix wrangler.jsonc worker name mismatch |
| #10 | Sep 23 | Phase 8: Remove legacy Cordova app, rewrite README/CLAUDE.md |

### First features after the port

| PR | Merged | Title |
|---|---|---|
| #11 | Sep 23 | Add student install guide at /install.html |
| #12 | Sep 23 | Add "Download for offline" button; fix service worker not controlling the page |
| #13 | Sep 23 | Update CLAUDE.md for the offline-controls/install-guide additions |

### Redesign and UX refinements

| PR | Merged | Title |
|---|---|---|
| #15 | Sep 24 | Side-by-side note picker + interval grid, SVG/error overlay on the piano |
| #16 | Sep 24 | Classic conservatory redesign: parchment, navy, brass, serif type |
| #17 | Sep 24 | Fix Cloudflare Workers Builds failing on every branch/PR |
| #18 | Sep 24 | Play on mode-tab click too, not just interval click; default to Min2/Tunes |
| #19 | Sep 24 | Move sheet-music overlay below the piano instead of covering it |
| #20 | Sep 24 | Fix overlay fade-out, tune timing, add not-allowed cursor while playing |
| #21 | Sep 24 | Recolor app icon to match the Classic conservatory theme |
| #22 | Sep 24 | Add COMPARISON.md: legacy Cordova/Backbone app vs. the React rewrite |
| #24 | Sep 26 | Refactor theme colors/fonts into CSS custom properties |

### Docs, deployment and portfolio

| PR | Merged | Title |
|---|---|---|
| #27 | Sep 26 | Update README's Deployment/Contributing sections for current workflow |
| #28 | Sep 26 | Update CLAUDE.md for the current state of the project |
| #30 | Sep 27 | Document the legacy-UI deployment |
| #31 | Sep 27 | Document a leftover Cloudflare build check |
| #32 | Sep 27 | Add the legacy-UI URL to README |
| #33 | Sep 27 | Add the legacy-UI URL to COMPARISON.md |
| #34 | Sep 27 | Retheme install.html to match the Classic app theme |
| #35 | Sep 27 | Fix wording issues from a review of the Markdown docs |
| #37 | Sep 27 | Document the public IntervalApp-showcase repo in CLAUDE.md |

### Promotions to production

| PR | Merged | Title |
|---|---|---|
| #14 | Sep 23 | Rewrite IntervalApp from Apache Cordova to React + TypeScript |
| #23 | Sep 26 | Sync dev into master: overlay fixes, not-allowed cursors, classic app icon, COMPARISON.md |
| #26 | Sep 26 | Sync dev into master: CSS theme-variables refactor |
| #29 | Sep 26 | Sync dev into master: README workflow docs, CLAUDE.md update |
| #36 | Sep 27 | Sync dev into master: legacy-UI links, install page retheme, docs fixes |

---

The source code and the audio/sheet-music assets are kept in a private repository. The live app and the first React release are linked from the [README](README.md).
