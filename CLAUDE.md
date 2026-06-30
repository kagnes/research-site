# CLAUDE.md — Research website (Hugo + Congo)

Bilingual (English primary, Hungarian secondary) academic research website built with
Hugo + the Congo theme, deployed to GitHub Pages. Mostly static content now; later it
gains interactive dataset visualizations and a dataset search backend.

## Source of truth — read these first
- `PROJECT.md` — full plan: architecture decisions, sitemap, roadmap, datasets tracker,
  open questions, decision log. **Read it before doing anything**, and update Sections 5–8
  at the end of each session.
- `docs/example-page.md` — the content-handoff format the author uses to supply page
  content. Pages arrive as plain Markdown with a metadata block plus these markers, which
  you convert into proper Hugo:
  - `{{VIZ: ...}}` → an embedded Plotly visualization
  - `{{SEARCH: ...}}` → an embedded dataset search interface
  - `{{IMAGE: file | caption | alt}}` → an image
  - `:::note ... :::` → a callout
  - `<!-- @claude: ... -->` → a private instruction, never rendered

## Stack & deploy
- Hugo **Extended** + **Congo** theme.
- GitHub Pages, built via GitHub Actions on push to `main`.
- Bilingual: one content file per language (`name.en.md` / `name.hu.md`); **menu labels
  are translated to Hungarian too**.

## Sitemap — 8 flat top-level menu items (no dropdowns)
1. Welcome (home) — short project intro
2. Research outputs — summary hub, links down to 3–6
3. Publications — two groups (closely / loosely related) + links
4. Presentations — two groups + slide/poster links
5. Datasets — list + (later) viz & browse links
6. Corpora — list + (later) browse interface links
7. Readings — others' work used/enjoyed
8. About the PI — external link to kagnes.github.io

Header: text-logo placeholder · menu · EN/HU language switch. Footer: fixed funding +
copyright on every page.

## Current task — Phase 1 (scaffold). Deploy a green skeleton BEFORE real content.
1. Verify/install Hugo Extended recent enough for Congo (`hugo version`). The author's old
   site used Hugo 0.97.3 — too old for Congo, so install a current Extended build.
2. Initialise the Hugo site and add Congo. **Judgment call:** the Hugo Modules install path
   needs Go installed; the git-submodule path doesn't. Pick one and note the choice in
   `PROJECT.md`.
3. Configure two languages (en/hu) + a translated menu with the 8 items + language switcher.
4. Create empty stub pages for all 8 sections, in both languages.
5. Text-logo placeholder in the header; placeholder funding/copyright in the footer.
6. Add the GitHub Pages Actions workflow and confirm a successful deploy.

Defer to later phases: real content (Phase 2), visualizations (Phase 3), dataset search
backend — SQLite/FastAPI on a VPS (Phase 4). See `PROJECT.md`.

## Working style (author preferences)
- Give a short roadmap before details.
- Flag judgment calls explicitly so the author can decide.
- Work iteratively, step by step; ask clarifying questions before big moves.
- Author codes Python/bash/Jupyter at an intermediate level — explain non-obvious
  web/Hugo specifics, keep going on the rest.

## Open questions (PROJECT.md §7) — don't block Phase 1, surface when relevant
Trigram/substring need · diacritics handling · per-dataset field lists · domain
(kagnes.net?) · Hungarian target for the About-the-PI link · new repo vs. extend existing
(decided: **new repo**).
