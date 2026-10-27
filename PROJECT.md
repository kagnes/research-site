# PROJECT.md — Postdoctoral Research Website

> Living planning document and **source of truth** for the site build.
> Update this at the end of each working session — it's the file we re-read to resume.

**Last updated:** 2026-10-27
**Researcher:** Ágnes Kalivoda (HUN-REN Hungarian Research Centre for Linguistics / ELTE NYTK)
**Existing site:** kagnes.github.io (Hugo / Wowchemy Academic) — *separate from this project; research-site repo*
**Current status:** Phase 2 static content done (EN + HU) → next: Phase 3 visualizations

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

**Menu — 4 flat, top-level items (no dropdowns):**

| # | Page          | HU label      | Type                 | Contents                                                        |
|---|---------------|---------------|----------------------|----------------------------------------------------------------|
| 1 | Project       | Projekt       | static (home)        | short project description                                       |
| 2 | Publications  | Publikációk   | list                 | two groups (closely / loosely related) + links                 |
| 3 | Presentations | Előadások     | list                 | two groups (closely / loosely related) + slide/poster links    |
| 4 | Datasets      | Adathalmazok  | list + interactive   | name, description, repo link, viz + browse links where relevant |

All four are flat siblings + an EN/HU language switcher.

**Trimmed 2026-06-30 (e)** — from the original 8: **Welcome → renamed "Project"**; **Research outputs** (summary hub), **Corpora**, and **About the PI** removed from the menu. Research-outputs & corpora stub pages were deleted. Corpora may return as a section in a later phase (still tracked in §6 datasets/corpora plans); the About-the-PI link will be placed elsewhere on the site, TBD.

**Trimmed 2026-10-27 (f)** — **Readings / Olvasmányok removed** (page + both content files + both menu entries deleted) at the researcher's request.

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
- [x] **Phase 1 — Static skeleton + deploy.** Scaffold + nav (5 items, EN/HU) + stubs + language switcher, **deployed green** to GitHub Pages. Live: https://kagnes.github.io/research-site/ (repo `research-site`, project subpath). ← *done*
- [x] **Phase 2 — Static content.** Project, Publications, Presentations, Datasets; EN + HU. ← *done 2026-10-27* (Readings dropped; bio/About-PI placement still open — see §7).
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
- [ ] **About the PI placement:** now off the menu (trimmed in §2 (e)), where does the external link to kagnes.github.io live — footer, the Project home page, or both? *(currently TBD)*
- [ ] **About the PI link:** does the HU page link to a Hungarian version of the personal site, or the same target as EN?
- [ ] **Domain:** buy kagnes.net or stay on github.io?
- [x] **Repo:** new repo for this project, or extend the existing site repo?
- [ ] Which datasets actually go on the site, and in what order?
- [ ] **Datasets HU term:** page title set to **"Adathalmazok"** (matches the menu label); the researcher's Phase-2 content draft used **"Adatcsomagok"**. Kept consistent with the menu for now — switch both if she prefers "Adatcsomagok".
- [ ] **MTSz/HHC corpus link:** the Corpus Query Interface (`corpus-dev.rilex.nytud.hu/#dashboard?corpname=mtsz`) is currently behind a username/password; URL to be updated once it is public (memo kept in `docs/datasets.*.md`).
- [ ] **Logo:** researcher's idea = two jigsaw-puzzle pieces almost fitting (preverb + verb). Deferred to a later phase; header still uses the site title as a text-logo.

**Content to provide (when ready):** eventual real logo (jigsaw concept, see above).

**Resolved in Phase 2 (2026-10-27):** final **site titles** (EN/HU) and **footer** funding + copyright lines are in `languages.*.toml` (no more `[XXXXXX]` placeholder; grant = OTKA PD 142317). HU menu labels confirmed. All four pages have real EN + HU content sourced from `docs/*.md`.

**Resolved in Phase 1:** baseURL / project-subpath worry is moot — the Actions workflow injects the real baseURL at build time, so the same config works for a user site or a `/repo/` project path.

---

## 8. Decision log

- **2026-10-27 (f)** — **Phase 2 static content.** Wrote real EN + HU content for all four pages (Project home, Publications, Presentations, Datasets) from the researcher's `docs/*.md` sources. **Readings removed** entirely (content files + both menu entries). Final **site titles** and **footer** funding/copyright set in `languages.*.toml`. New **`{{< btns >}}` shortcode** (`layouts/_shortcodes/btns.html`) + `.btn-row` CSS in `assets/css/custom.css` render the publication/presentation/dataset links as small, thin **blue-bordered outline buttons** on their own line below each item, no bullet, opening in a new tab (per the `@claude` note in the docs). American-English spelling/grammar lightly corrected on the two EN pages that carried the `@claude` request (Project, Datasets); Hungarian text left verbatim. Planning-memo HTML comments from the docs were **not** carried into `content/` (they stay in `docs/`). Builds clean (0 warnings); verified titles, footer, menu (no Readings), button markup + `target="_blank"`, and bundled CSS. Logo deferred per the researcher. **Deploy:** push `main` to publish via the existing Pages workflow.
- **2026-06-30 (d)** — Phase 1 **deployed green** at https://kagnes.github.io/research-site/ (new repo `research-site`, project subpath). First CI run failed at `configure-pages` because Pages wasn't enabled; fixed by adding `enablement: true` so the workflow turns Pages on itself. Verified on the live site: subpath-correct asset URLs (no `example.org` leak), all 8 EN/HU nav items, EN↔HU language switcher, external About link, and footer funding/copyright line. URL slugs stay English in both languages (only menu *labels* are translated) — e.g. HU corpora is at `/hu/corpora/`. *(Note: the menu was later trimmed to 5 items in (e); the "8 nav items" / `/hu/corpora/` references above describe the original Phase-1 deploy and predate that trim.)*
- **2026-06-30 (c)** — Phase 1 scaffold. **Congo installed as a git submodule** (`themes/congo`, `stable` branch), *not* via Hugo Modules, because Go is not installed and the submodule path needs no extra toolchain. Hugo **Extended v0.163.3** installed (the runner reinstalls it at deploy time, so no local dependency). Config split into `config/_default/` (hugo, languages.en/hu, menus.en/hu, params, markup). Header text-logo = site title; footer = placeholder funding + copyright per language. Deploy = standard **GitHub Pages Actions** workflow (`.github/workflows/hugo.yml`) with `submodules: recursive` and `--baseURL` injected from the Pages config. Site builds clean (0 warnings); EN/HU nav, language switcher, and external About link all verified in the rendered HTML. **Remaining for a green deploy:** create the (new) GitHub repo and push `main`.
- **2026-06-30 (b)** — Finalised the sitemap: 8 flat top-level items (Welcome, Research outputs, Publications, Presentations, Datasets, Corpora, Readings, About the PI), with Research outputs as a summary hub linking to 3–6. Shell = text-logo placeholder + menu + EN/HU switch; fixed funding/copyright footer. **Theme = Congo.** Bilingual EN (primary) / HU (secondary); menu labels translated; one file per language.
- **2026-06-30 (a)** — Settled the hybrid architecture (Hugo + Pages for static content and visualizations; FastAPI/SQLite search on a cheap EU VPS). Chose SQLite FTS5 over MySQL; chose aggregate-then-Plotly.js for visualizations. Confirmed: largest dataset ≈ 42M rows, occasional updates, open to cheap paid hosting, search mix = both with field lookups dominant.

---

## 9. How to resume

Open this file first. Section 5 shows phase status, Section 7 lists what's currently blocking, Section 8 is the history. Update Sections 5–8 at the end of each session.
