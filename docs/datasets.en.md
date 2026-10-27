<!-- @claude: While processing this .md file, please check the content in terms of correct American English spelling and grammar, and feel free to fix the mistakes. -->
<!-- @claude: I'd like to have the [TEXT](LINK) kinds of links appear as if they were small buttons, as you can see on this page: https://kagnes.github.io/hu/publication/ - So, the part in [TEXT] has a transparent background and a thin blue border, and the (LINK) opens in a new tab. Links should appear below the publication item, next to each other if there's more than one link. They shouldn't have a bullet point. -->

## Page metadata

```
title: Datasets
summary: Linguistic resources created in the course of the project.
language: en
menu: none
order: 0
```

─────────────────────────────────────────────────────────

During the project, numerous linguistic resources (corpora and datasets) were created, which are listed on this page. All resources can be browsed via an online search interface. The source files for the datasets are available for download as well.

## 1. A new, upgraded version of the Hungarian Historical Corpus (HHC)
The [Hun­garian Historical Corpus](https://www.clarin.eu/resource-families/hungarian-historical-corpus) is a continuously growing, currently 40 million-token large reference corpus covering the Modern Hungarian period (1772–). In its original version, all texts were provided in their original orthographic form, and no linguistic annotation was applied. One of the central aims of this project was to create an upgraded version of the HHC which is automatically normalized, lemmatized and morphologically annotated. Now it has also annotation layers focusing on preverb-verb constructions: separated preverbs are connected with their respective verbs, and the position of the preverbs relative to the verb stem is tagged as well.
- [Corpus Query Interface](https://corpus-dev.rilex.nytud.hu/#dashboard?corpname=mtsz)
<!-- @claude: This interface is currently behind a username and a password, but this will change shortly. Here I just want to keep a memo that I'll have to change the URL soon. -->

## 2. Preverb Distributions (PrevDistro)
PrevDistro is an open-source dataset containing 41.5 million corpus occurrences of 49 preverb-verb construction types. It is primarily designed to account for preverbs – and preverb-like lexical items –, their position relative to the verb stem, and the construction types which may host these items. The data appearing in this dataset are extracted from the [Hungarian Gigaword Corpus](https://clara.nytud.hu/mnsz2-dev/en/).
- [Zenodo repository](https://zenodo.org/records/6349410)
<!-- @claude: Here we'll have a browse link later. -->

## 3. Preverb Constructions (PrevCons)
PrevCons is a dataset presenting 21,038 preverb-verb hapaxes, created from the [Hungarian Gigaword Corpus](https://clara.nytud.hu/mnsz2-dev/en/). This resource makes it possible
to explore productive preverb-verb patterns by the accessibility of ‘preverb – derivational suffix – argument frame’ triplets. In addition, it contains a wealth of metadata regarding the morphological structure and semantics of the hapaxes, as well as their specific occurrences within the text.
- [GitHub repository](https://github.com/kagnes/prevcons)
<!-- @claude: Here we'll have a browse link later, and probably a visualization link, too. -->

## 4. Preverb History (PrevHist)
PrevHist is a dataset of preverb-verb constructions from Old and Middle Hungarian, covering a time span of approximately nine centuries (896–1772). It contains 68,458 records extracted automatically from two historical corpora and is annotated for a wide range of morphosyntactic features and metadata.
- [Zenodo repository](https://zenodo.org/records/19927110)
<!-- @claude: Here we'll have a browse link later, and probably a visualization link, too. -->

## 5. *Agyon* dataset
This dataset lists all occurrences (22,571 records) of the Hungarian lexical item *agyon* across four historical corpora. It can be used to explore how *agyon*, initially a case-marked noun, turned into a preverb over time.
- [GitHub repository](https://github.com/kagnes/hungarian_preverb_agyon)
<!-- @claude: Here we'll have a browse link later, and probably a visualization link, too. -->

## 6. The intensifying fake reflexive construction in Hungarian
This dataset displays various occurrences of the so-called intensifying fake reflexive resultative construction in Present-day Hungarian (1,443 records). This construction is characterized by the form `[N/Adj+Transl/Subl V REFL.PRON+Acc]` with the schematic meaning `to V oneself excessively`.
- [GitHub repository](https://github.com/kagnes/hungarian_intensifying_fake_reflexive_resultative_construction)
<!-- @claude: Here we'll have a browse link later, and probably a visualization link, too. -->

