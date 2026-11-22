# AGENTS.md

Guidance for AI coding agents working on this repository.

## Project

**Laws & Effects** is a curated reference website — a centralized directory of mental models, systemic rules, and psychological quirks. It is a play on "cause and effect": mapping the hidden rules of systems and the quirks of human nature.

## Architecture

- `index.html` is the entire app: a self-contained, single-page, mobile-responsive site with **no build step, no dependencies, and no frameworks**. Keep it that way unless the owner explicitly requests a migration.
- All entries live in the `ENTRIES` array inside `index.html` (search for `var ENTRIES`). Each entry has exactly five fields:
  - `title` (string) — large bold card title
  - `type` (string) — one of: `Law`, `Effect`, `Principles`, `Concept`, `Paradox`
  - `domain` (string) — one of: `Mind & Behavior`, `Systems & Tech`, `Politics & Society`, `Science & Physics`, `Media & Society`, `Philosophy & Logic`
  - `definition` (string) — concise 1–2 sentence definition
  - `source` (string) — trusted external URL opened in a new tab by the "Authoritative Source" button
- Filtering model: a fixed header holds a real-time fuzzy search input plus two filter axes (Type and Domain). Search and both filters combine. The fuzzy match is substring-first, then subsequence.

## Conventions

- **Adding an entry:** append to the `ENTRIES` array keeping alphabetical order by title (apostrophes are ignored, so “Occam's Razor” precedes “O'Sullivan's Laws”); use the exact `type` and `domain` strings above so filters and tag colors continue to work; keep definitions to 1–2 sentences; link a genuinely authoritative source (encyclopedia, primary paper, or the originator's own writing).
- **Style tokens** are CSS custom properties in `:root` (`--ink`, `--accent`, `--law`, `--effect`, `--principles`, `--concept`, `--paradox`, etc.) and the `.tag.type[data-type=...]` and `.tag.domain[data-domain=...]` rules. Change colors only via these tokens. All color pairs must maintain WCAG 2.2 AA contrast (4.5:1) — the current palette passes; re-verify before changing any color. The Paradox tag is white text on `--paradox` (`#92400E`).
- **Accessibility is not optional:** preserve the skip link, `aria-pressed` filter buttons, `aria-live` result counter, labeled search input, visible focus styles, and new-tab links with `rel="noopener noreferrer"`.

## Definition of done

1. `index.html` opens directly in a browser with zero console errors.
2. Search + both filter axes still work and combine correctly.
3. No color contrast regressions (WCAG AA).
4. Commit messages are short, imperative, and describe the user-visible change.

## Colophon

This project keeps COLOPHON.md at the root: a short, honest record of which
tools and models built it, where they ran, and who directed and reviewed it.

- Update COLOPHON.md in the same commit or pull request as your work, only when
  the tool, model, model setting, or computer changes, a new phase starts, you
  review another tool's work, or before a release. Most PRs leave it alone.
- Never hold up a commit for it. Match the file's style and timezone, put new
  rows at the top of Builder history, and combine same-day rows per builder.
- Write Unknown instead of guessing. Record exact model, setting, mode, and
  source (shown by the tool, configured, or self-reported). Never cite a commit
  hash that doesn't exist yet.
- Keep secrets, private links, computer names, usernames, and local paths out.
- If you can't edit COLOPHON.md, end your reply with a Colophon note (tool,
  model/setting + source, mode, surface, times + timezone, work done, files).
