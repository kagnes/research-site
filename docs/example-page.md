<!--
============================================================
  HOW TO USE THIS TEMPLATE  (delete everything above the ───── line when you adapt it)
============================================================

Give me ONE file like this per page, named after the page in kebab-case
(e.g. research-hatnek.md, publications.md, about.md).

You write plain content. I convert it into proper Hugo pages — you never
have to touch Hugo front matter or shortcodes yourself.

MARKERS you can drop anywhere in the text (I turn each into the right output):

  {{VIZ: ...}}      An interactive chart goes here. Describe what it shows and
                    which dataset/columns. I build it with Plotly.
  {{SEARCH: ...}}   A dataset search box goes here. Name the dataset.
  {{IMAGE: file | caption | alt-text}}
                    An image. Drop the file in an images/ folder next to the
                    page, or just describe it and I'll leave a placeholder.
  :::note ... :::   A highlighted callout / aside.
  <!-- @claude: ... -->
                    A private instruction to ME. Never appears on the page.

Everything else is normal Markdown: ## headings, - lists, [links](url),
**bold**, *italic*, > blockquotes.

LANGUAGES: one file per language, same structure, translated content —
  research-hatnek.en.md  +  research-hatnek.hu.md
If a page is English-only, just say so (or only send the .en version).

METADATA: fill the fields in the block below; I translate them to Hugo.
============================================================
-->

─────────────────────────────────────────────────────────

## Page metadata

```
title:     The -hAtnék Impulsative Construction
summary:   A corpus-based study of a productive Hungarian desiderative pattern.
language:  en
menu:      Research        # which nav menu this page sits in, or "none"
order:     2               # position in that menu (lower number = earlier)
```

─────────────────────────────────────────────────────────

## Overview

*(Example text — replace with your own.)* The Hungarian impulsative *-hAtnék*
construction expresses a sudden, often bodily, urge to do something. This project
investigates its productivity using large-scale corpus data, building on the idea
that **expressivity drives productivity**.

We approach the construction from three angles: its semantic range, the lifecycle
of its matrix verbs, and its collostructional profile.

<!-- @claude: this page should link to the ICCG 2026 talk and the dataset page once those exist. -->

## Semantic categories of base verbs

*(Example text — replace.)* The base verbs that feed the construction fall into
several recurring semantic groups:

- Emotional release
- Motion & escape
- Bodily processes
- Speech
- (… and others)

{{IMAGE: bubble-overview.png | Semantic categories of base verbs | Bubble chart grouping base verbs into semantic categories}}

:::note
This page is part of a larger project; the figures below are generated from the
HPLT 3.0 corpus pipeline. *(Replace or delete this aside as you like.)*
:::

## Matrix verb lifecycle

*(Example text — replace.)* The matrix verbs that host the construction appear to
move through distinct temporal stages. The chart below tracks their relative
frequency over time.

{{VIZ: Animated scatterplot of matrix-verb frequency across four temporal stages.
Data = matrix_verb_lifecycle.csv (columns: verb, stage, freq). One bubble per verb,
size = freq, animation frame = stage. Replace with your real file when ready.}}

## Explore the data

*(Example text — replace.)* You can browse the full concordance below.

{{SEARCH: Large KWIC corpus — let visitors filter by lemma, POS, and construction,
with optional word search in the context window.}}

## Related publications

*(Example — replace with real entries, or tell me "pull these from publications.md".)*

- Kalivoda, Á., Ackerman, F., & Malouf, R. (2026). *Title here.* Venue.
- [Project repository](https://github.com/your-handle/your-repo)
