---
title: "Adathalmazok"
description: "A projekt során készült nyelvi erőforrások: korpuszok, adattáblák."
---

A projekt során számos nyelvi erőforrás (korpusz és adattábla) készült, amelyeket ez az oldal listáz. Minden erőforrás böngészhető online keresőfelületen keresztül, és az adattáblák forrásfájljai le is tölthetők.

## 1. A Magyar Történeti Szövegtár új, továbbfejlesztett verziója (MTSz)

A [Magyar Történeti Szövegtár](https://www.clarin.eu/resource-families/hungarian-historical-corpus) egy folyamatosan bővülő, jelenleg körülbelül 40 millió tokenből álló referenciakorpusz, amely a mai magyar kort fedi le (1772-től napjainkig). Az eredeti változatában minden szöveg az eredeti, betűhű írásmódjában szerepelt, nyelvi annotáció nélkül. A projekt egyik fő célkitűzése az MTSz olyan továbbfejlesztett változatának létrehozása volt, amely automatikus normalizálással, lemmatizálással és morfológiai elemzéssel is rendelkezik. A korpusz emellett olyan annotációs rétegeket is tartalmaz, amelyek az igekötős igei szerkezetekre összpontosítanak: az elvált igekötőket összekapcsolják a hozzájuk tartozó igékkel, valamint jelölik az igekötők igei tőhöz viszonyított pozícióját.
{{< btns >}}[Korpuszlekérdező felület](https://corpus-dev.rilex.nytud.hu/#dashboard?corpname=mtsz){{< /btns >}}

## 2. Preverb Distributions (PrevDistro)

A PrevDistro 49 szerkezettípus korpuszbeli előfordulásait tartalmazza, minden előfordulás esetében feltüntetve külön az igekötőt és az igelemmát, az igekötő pozícióját az igetőhöz képest, valamint a szerkezetbe beférkőző egyéb szavakat. Emellett elérhető a szerkezetek nagyobb kontextusa, a teljes mondat is. A 41,5 millió rekordból álló adattábla a [Magyar Nemzeti Szövegtár 2](https://clara.nytud.hu/mnsz2-dev) anyagából készült.
{{< btns >}}[Zenodo repozitórium](https://zenodo.org/records/6349410){{< /btns >}}

## 3. Preverb Constructions (PrevCons)

A PrevCons adattábla 21 038 igekötős hapaxot tartalmaz azok lehetséges vonzatkeretével együtt. Ezen felül számos metaadat érhető el benne a hapaxok morfológiai szerkezetéről, szemantikájáról és konkrét szövegbeli előfordulásáról. A PrevCons a [Magyar Nemzeti Szövegtár 2](https://clara.nytud.hu/mnsz2-dev) anyagából készült.
{{< btns >}}[GitHub repozitórium](https://github.com/kagnes/prevcons){{< /btns >}}

## 4. Preverb History (PrevHist)

A PrevHist az ó- és középmagyar kori igekötős szerkezetek olyan adattáblája, amely hozzávetőleg kilenc évszázadot (896–1772) ölel fel. Két történeti korpuszból automatikusan kinyert 68 458 találatot tartalmaz, amelyek számos morfoszintaktikai jellemzővel és metaadattal címkézettek.
{{< btns >}}[Zenodo repozitórium](https://zenodo.org/records/19927110){{< /btns >}}

## 5. *Agyon* adattábla

Ez a manuálisan ellenőrzött, 22 571 tételből álló adattábla az *agyon* összes korpuszbeli előfordulását tartalmazza grammatikai jellemzőkkel és metaadatokkal együtt. Négy olyan korpusz felhasználásával készült, amelyek együttesen lefedik az ómagyar kortól napjainkig terjedő időszakot. Az adattábla segítségével nyomon követhető az a folyamat, amelynek során az *agyon* ragos főnév igekötői funkciót vett fel.
{{< btns >}}[GitHub repozitórium](https://github.com/kagnes/hungarian_preverb_agyon){{< /btns >}}

## 6. A felnagyító reflexív áltárgyas szerkezet

Ez az adattábla az ún. felnagyító jelentésű, reflexív áltárgyas szerkezet (pl. *szénné dolgozza magát*, *gennyesre keresem magam*) különféle előfordulásait tartalmazza mai magyar korpuszanyagból (1 443 találat).
{{< btns >}}[GitHub repozitórium](https://github.com/kagnes/hungarian_intensifying_fake_reflexive_resultative_construction){{< /btns >}}
