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

This project keeps COLOPHON.md, a short record of how it was made.
Agents update it themselves, in the same commit or pull request as their
work: add a row when the tool, model, model setting, or computer changes,
when a new phase of work starts, when you review someone else's work, and
before each release. Never hold up a commit for it. Follow the instructions
at https://colophon.md/instructions.md.
