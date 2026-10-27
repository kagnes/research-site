---
title: "Datasets"
description: "Linguistic resources created in the course of the project."
---

During the project, numerous linguistic resources (corpora and datasets) were created, which are listed on this page. All of them can be browsed via an online search interface, and the source files for the datasets are available for download as well.

## 1. A new, upgraded version of the Hungarian Historical Corpus (HHC)

The [Hungarian Historical Corpus](https://www.clarin.eu/resource-families/hungarian-historical-corpus) is a continuously growing reference corpus of currently about 40 million tokens, covering the Modern Hungarian period (1772–). In its original version, all texts were given in their original orthographic form, without any linguistic annotation. One of the central aims of this project was to create an upgraded version of the HHC that is automatically normalized, lemmatized, and morphologically annotated. It now also has annotation layers focusing on preverb-verb constructions: separated preverbs are linked to their respective verbs, and the position of each preverb relative to the verb stem is tagged as well.
{{< btns >}}[Corpus Query Interface](https://corpus-dev.rilex.nytud.hu/#dashboard?corpname=mtsz){{< /btns >}}

## 2. Preverb Distributions (PrevDistro)

PrevDistro is an open-source dataset containing 41.5 million corpus occurrences of 49 preverb-verb construction types. It is primarily designed to account for preverbs—and preverb-like lexical items—their position relative to the verb stem, and the construction types that may host these items. The data in this dataset are extracted from the [Hungarian Gigaword Corpus](https://clara.nytud.hu/mnsz2-dev/en/).
{{< btns >}}[Zenodo repository](https://zenodo.org/records/6349410){{< /btns >}}

## 3. Preverb Constructions (PrevCons)

PrevCons is a dataset presenting 21,038 preverb-verb hapaxes, created from the [Hungarian Gigaword Corpus](https://clara.nytud.hu/mnsz2-dev/en/). This resource makes it possible to explore productive preverb-verb patterns through the accessibility of ‘preverb – derivational suffix – argument frame’ triplets. In addition, it contains a wealth of metadata on the morphological structure and semantics of the hapaxes, as well as their specific occurrences in the text.
{{< btns >}}[GitHub repository](https://github.com/kagnes/prevcons){{< /btns >}}

## 4. Preverb History (PrevHist)

PrevHist is a dataset of preverb-verb constructions from Old and Middle Hungarian, covering a time span of approximately nine centuries (896–1772). It contains 68,458 records extracted automatically from two historical corpora and annotated for a wide range of morphosyntactic features and metadata.
{{< btns >}}[Zenodo repository](https://zenodo.org/records/19927110){{< /btns >}}

## 5. *Agyon* dataset

This dataset lists all occurrences (22,571 records) of the Hungarian lexical item *agyon* across four historical corpora. It can be used to explore how *agyon*, initially a case-marked noun, turned into a preverb over time.
{{< btns >}}[GitHub repository](https://github.com/kagnes/hungarian_preverb_agyon){{< /btns >}}

## 6. The intensifying fake reflexive construction in Hungarian

This dataset presents various occurrences of the so-called intensifying fake reflexive resultative construction in Present-day Hungarian (1,443 records). This construction is characterized by the form `[N/Adj+Transl/Subl V REFL.PRON+Acc]`, with the schematic meaning ‘to V oneself excessively’.
{{< btns >}}[GitHub repository](https://github.com/kagnes/hungarian_intensifying_fake_reflexive_resultative_construction){{< /btns >}}
