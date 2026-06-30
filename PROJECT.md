# PROJECT.md — Postdoctoral Research Website

> Living planning document and **source of truth** for the site build.
> Update this at the end of each working session — it's the file we re-read to resume.

**Last updated:** 2026-06-30
**Researcher:** Ágnes Kalivoda (HUN-REN Hungarian Research Centre for Linguistics / ELTE NYTK)
**Existing site:** kagnes.github.io (Hugo / Wowchemy Academic) — *separate from this project; decide whether to reuse the repo or start fresh*
**Current status:** Phase 0 complete (architecture + sitemap set) → next: Phase 1 scaffold

---

## 1. What this site is

A research website with three kinds of content:

- **Static content** — project description, publications, bio, etc.
- **Browseable datasets** — search interfaces over linguistic corpora (largest ≈ 42M KWIC rows).
- **Interactive visualizations** — Plotly charts (incl. animated scatterplots) over aggregated data.

---

## 2. Sitemap & navigation

**Shell:** header (text-logo placeholder · menu bar · EN/HU language switch) — body (page content) — footer (fixed funding + copyright, on every page).

**Theme:** **Congo** (Hugo). Chosen for speed, low maintenance, first-class multilingual + language switcher, and easy raw-HTML embeds for Plotly charts and the search UI.

**Languages:** **English primary, Hungarian secondary.** One file per language per page (`…en.md` / `…hu.md`). **Menu labels are translated to Hungarian too.**

**Logo:** temporary **text placeholder** for now (real logo TBD).

**Menu — 8 flat, top-level items (no dropdowns):**

| # | Page             | Type                 | Contents                                                        |
|---|------------------|----------------------|----------------------------------------------------------------|
| 1 | Welcome          | static (home)        | short project description                                       |
| 2 | Research outputs | summary hub          | overview of main results; links down to 3–6                    |
| 3 | Publications     | list                 | two groups (closely / loosely related) + links                 |
| 4 | Presentations    | list                 | two groups (closely / loosely related) + slide/poster links    |
| 5 | Datasets         | list + interactive   | name, description, repo link, viz + browse links where relevant |
| 6 | Corpora          | list + interactive   | name, description, links to browse interfaces                  |
| 7 | Readings         | list                 | others' work used / enjoyed                                     |
| 8 | About the PI     | external link        | link to personal site (kagnes.github.io)                       |

Items 3–6 are the "detailed outputs" that **Research outputs (2)** summarises and links to. All eight are flat siblings.

---

## 3. Architecture (decided)

Hybrid: static wherever possible, one small dynamic service only where the data forces it.

| Layer            | Choice                              | Hosting              | Cost      |
|------------------|-------------------------------------|----------------------|-----------|
| Static content   | Hugo + Congo                        | GitHub Pages         | free      |
| Visualizations   | Precomputed JSON + Plotly.js        | GitHub Pages (static)| free      |
| Dataset search   | Python API (FastAPI) over SQLite    | Cheap EU VPS         | ~€5–8/mo  |
| Search DB build  | Offline Python pipeline             | local / build-time   | free      |

The frontend (Pages) calls the search API (VPS). **Visualizations need no server.**

### Why these choices
- **Not pure static / Pages-only:** a 42M-row corpus is several GB, and KWIC context search is a full scan — too big and too slow to ship into the browser.
- **Not MySQL:** data is read-mostly with occasional rebuilds, so a single-file DB (build once, ship the file) is simpler and cheaper than running a DB server.
- **SQLite + FTS5:** field lookups (lemma/wordform/POS) via B-tree indexes; whole-word/phrase context search via an external-content FTS5 index.
- **Aggregate-then-plot:** charts are built from precomputed summaries, never from 42M raw points.

### Search design notes
- Query mix: **(c) both**, with **(a) field/prefix lookups more typical** than **(b) context search**.
- (a) → `COLLATE NOCASE` B-tree indexes (fast exact + prefix).
- (b) whole-word/phrase → FTS5 external-content index (`content='kwic'`, no duplicated text).
- (b) true mid-word substring / regex → trigram index + "prefilter then regex" — **only if confirmed needed** (see Open Questions).
- Hungarian diacritics: default `remove_diacritics 0` (keep á≠a etc. distinct); optional folded index for lenient search — **decision pending**.

### Deployment notes (for Phase 4)
- API must be **HTTPS** (Pages is HTTPS; browsers block mixed content) and must allow the `github.io` origin via **CORS**. Caddy in front of FastAPI handles certificates automatically.
- VPS sizing: **≥ 80 GB NVMe** (DB + indexes ≈ 15–30 GB), **4 GB RAM** is enough (SQLite streams from disk). Hetzner CPX22 is the reference box.

---

## 4. Tech stack (summary)

Hugo + Congo · GitHub Pages · Python (build pipelines) · SQLite (FTS5, optional trigram) · DuckDB/pandas (offline aggregation) · FastAPI · Caddy · Plotly.js · Hetzner VPS

---

## 5. Roadmap (phases)

Phases **3 & 4 repeat per dataset** and are independent — the static site and first visualizations can ship while later datasets are still in progress.

- [x] **Phase 0 — Plan & structure.** Architecture, sitemap, this `PROJECT.md`. (Standard pages need no wireframes; the sitemap diagram covers structure.)
- [~] **Phase 1 — Static skeleton + deploy.** Scaffold + nav + stubs **done and building clean locally**; the green Pages deploy is pending the first push to a GitHub repo (workflow is in place). ← *finishing*
- [ ] **Phase 2 — Static content.** Project description, publications, presentations, readings, bio; EN + HU.
- [ ] **Phase 3 — Visualizations** *(per dataset)*. Offline aggregation → JSON → Plotly.js page. No server.
- [ ] **Phase 4 — Search backend** *(per dataset)*. Build pipeline → SQLite → FastAPI on VPS → search UI.
- [ ] **Phase 5 — Polish & domain.** Custom domain (kagnes.net?), styling, performance, accessibility.

---

## 6. Datasets tracker

One row per browseable dataset. Status values: `planned` / `data-ready` / `viz-done` / `search-done`.

| Dataset            | ~Size     | Fields known? | Viz     | Search  | Notes                        |
|--------------------|-----------|---------------|---------|---------|------------------------------|
| Large KWIC corpus  | ~42M rows | no            | planned | planned | the (c)-mix search target    |
| _(add dataset)_    |           |               |         |         |                              |

---

## 7. Open questions / decisions pending

- [ ] Does (b) need true **mid-word substring/regex** in context, or mostly whole-word/phrase? → decides the trigram index.
- [ ] **Diacritics:** strict only, folded only, or both (UI toggle)?
- [ ] **Field list** per dataset (emMorph tags, construction labels, semantic classes, corpus metadata…) → finalizes the schema.
- [ ] **About the PI link:** does the HU page link to a Hungarian version of the personal site, or the same target as EN?
- [ ] **Domain:** buy kagnes.net or stay on github.io?
- [ ] **Repo:** new repo for this project, or extend the existing site repo?
- [ ] Which datasets actually go on the site, and in what order?

**Content to provide (when ready):** Hungarian translations of the 8 menu labels *(provisional placeholders now in `menus.hu.toml` — please confirm/correct: Kezdőlap · Kutatási eredmények · Publikációk · Előadások · Adathalmazok · Korpuszok · Olvasmányok · A kutatóról)* · footer text (funder names, grant numbers, copyright line), EN + HU *(placeholder `[XXXXXX]` grant number in `languages.*.toml`)* · eventual real logo · final site title (placeholder: "Ágnes Kalivoda — Research" / "Kalivoda Ágnes — Kutatás").

**Resolved in Phase 1:** baseURL / project-subpath worry is moot — the Actions workflow injects the real baseURL at build time, so the same config works for a user site or a `/repo/` project path.

---

## 8. Decision log

- **2026-06-30 (c)** — Phase 1 scaffold. **Congo installed as a git submodule** (`themes/congo`, `stable` branch), *not* via Hugo Modules, because Go is not installed and the submodule path needs no extra toolchain. Hugo **Extended v0.163.3** installed (the runner reinstalls it at deploy time, so no local dependency). Config split into `config/_default/` (hugo, languages.en/hu, menus.en/hu, params, markup). Header text-logo = site title; footer = placeholder funding + copyright per language. Deploy = standard **GitHub Pages Actions** workflow (`.github/workflows/hugo.yml`) with `submodules: recursive` and `--baseURL` injected from the Pages config. Site builds clean (0 warnings); EN/HU nav, language switcher, and external About link all verified in the rendered HTML. **Remaining for a green deploy:** create the (new) GitHub repo and push `main`.
- **2026-06-30 (b)** — Finalised the sitemap: 8 flat top-level items (Welcome, Research outputs, Publications, Presentations, Datasets, Corpora, Readings, About the PI), with Research outputs as a summary hub linking to 3–6. Shell = text-logo placeholder + menu + EN/HU switch; fixed funding/copyright footer. **Theme = Congo.** Bilingual EN (primary) / HU (secondary); menu labels translated; one file per language.
- **2026-06-30 (a)** — Settled the hybrid architecture (Hugo + Pages for static content and visualizations; FastAPI/SQLite search on a cheap EU VPS). Chose SQLite FTS5 over MySQL; chose aggregate-then-Plotly.js for visualizations. Confirmed: largest dataset ≈ 42M rows, occasional updates, open to cheap paid hosting, search mix = both with field lookups dominant.

---

## 9. How to resume

Open this file first. Section 5 shows phase status, Section 7 lists what's currently blocking, Section 8 is the history. Update Sections 5–8 at the end of each session.
