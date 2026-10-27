<!-- @claude: I'd like to have the [TEXT](LINK) kinds of links appear as if they were small buttons, as you can see on this page: https://kagnes.github.io/hu/publication/ - So, the part in [TEXT] has a transparent background and a thin blue border, and the (LINK) opens in a new tab. Links should appear below the publication item, next to each other if there's more than one link. They shouldn't have a bullet point. -->

## Page metadata

```
title: Adatcsomagok
summary: A projekt során készült nyelvi erőforrások: korpuszok, adattáblák.
language: hu
menu: none
order: 0
```

─────────────────────────────────────────────────────────

A projekt során számos nyelvi erőforrás (korpusz és adattábla) készült, amelyeket ez az oldal listáz. Minden erőforrás böngészhető online keresőfelületen keresztül, és az adattáblák forrásfájljai le is tölthetők.

## 1. A Magyar Történeti Szövegtár új, továbbfejlesztett verziója (MTSz)
A [Magyar Történeti Szövegtár](https://www.clarin.eu/resource-families/hungarian-historical-corpus) egy folyamatosan bővülő, jelenleg körülbelül 40 millió tokenből álló referenciakorpusz, amely a mai magyar kort fedi le (1772-től napjainkig). Az eredeti változatában minden szöveg az eredeti, betűhű írásmódjában szerepelt, nyelvi annotáció nélkül. A projekt egyik fő célkitűzése az MTSz olyan továbbfejlesztett változatának létrehozása volt, amely automatikus normalizálással, lemmatizálással és morfológiai elemzéssel is rendelkezik. A korpusz emellett olyan annotációs rétegeket is tartalmaz, amelyek az igekötős igei szerkezetekre összpontosítanak: az elvált igekötőket összekapcsolják a hozzájuk tartozó igékkel, valamint jelölik az igekötők igei tőhöz viszonyított pozícióját.
- [Korpuszlekérdező felület](https://corpus-dev.rilex.nytud.hu/#dashboard?corpname=mtsz)
<!-- @claude: This interface is currently behind a username and a password, but this will change shortly. Here I just want to keep a memo that I'll have to change the URL soon. -->

## 2. Preverb Distributions (PrevDistro)
A PrevDistro 49 szerkezettípus korpuszbeli előfordulásait tartalmazza, minden előfordulás esetében feltüntetve külön az igekötőt és az igelemmát, az igekötő pozícióját az igetőhöz képest, valamint a szerkezetbe beférkőző egyéb szavakat. Emellett elérhető a szerkezetek nagyobb kontextusa, a teljes mondat is. A 41,5 millió rekordból álló adattábla a [Magyar Nemzeti Szövegtár 2](https://clara.nytud.hu/mnsz2-dev) anyagából készült.
- [Zenodo repozitórium](https://zenodo.org/records/6349410)
<!-- @claude: Here we'll have a browse link later. -->

## 3. Preverb Constructions (PrevCons)
A PrevCons adattábla 21 038 igekötős hapaxot tartalmaz azok lehetséges vonzatkeretével együtt. Ezen felül számos metaadat érhető el benne a hapaxok morfológiai szerkezetéről, szemantikájáról és konkrét szövegbeli előfordulásáról. A PrevCons a [Magyar Nemzeti Szövegtár 2](https://clara.nytud.hu/mnsz2-dev) anyagából készült.
- [GitHub repozitórium](https://github.com/kagnes/prevcons)
<!-- @claude: Here we'll have a browse link later, and probably a visualization link, too. -->

## 4. Preverb History (PrevHist)
A PrevHist az ó- és középmagyar kori igekötős szerkezetek olyan adattáblája, amely hozzávetőleg kilenc évszázadot (896–1772) ölel fel. Két történeti korpuszból automatikusan kinyert 68 458 találatot tartalmaz, amelyek számos morfoszintaktikai jellemzővel és metaadattal címkézettek.
- [Zenodo repozitórium](https://zenodo.org/records/19927110)
<!-- @claude: Here we'll have a browse link later, and probably a visualization link, too. -->

## 5. *Agyon* adattábla
Ez a manuálisan ellenőrzött, 22 571 tételből álló adattábla az *agyon* összes korpuszbeli előfordulását tartalmazza grammatikai jellemzőkkel és metaadatokkal együtt. Négy olyan korpusz felhasználásával készült, amelyek együttesen lefedik az ómagyar kortól napjainkig terjedő időszakot. Az adattábla segítségével nyomon követhető az a folyamat, amelynek során az *agyon* ragos főnév igekötői funkciót vett fel.
- [GitHub repozitórium](https://github.com/kagnes/hungarian_preverb_agyon)
<!-- @claude: Here we'll have a browse link later, and probably a visualization link, too. -->

## 6. A felnagyító reflexív áltárgyas szerkezet
Ez az adattábla az ún. felnagyító jelentésű, reflexív áltárgyas szerkezet (pl. *szénné dolgozza magát*, *gennyesre keresem magam*) különféle előfordulásait tartalmazza mai magyar korpuszanyagból (1 443 találat).
- [GitHub repozitórium](https://github.com/kagnes/hungarian_intensifying_fake_reflexive_resultative_construction)
<!-- @claude: Here we'll have a browse link later, and probably a visualization link, too. -->

