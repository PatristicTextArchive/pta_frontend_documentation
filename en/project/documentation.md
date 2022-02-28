## Editorial Implementation

### Transcription of manuscripts and (critical) editions

-> Look here: [Encoding guidelines](../project/encoding-guidelines) (only German at the moment)

### Texts
Where available, each text is linked to the matching entries in the databases of [Clavis Clavium](https://clavis.brepols.net/clacla/Default.aspx) and of [Pinakes](https://pinakes.irht.cnrs.fr/); IDs of the TLG© for authors and works are also shown (no linking is possible).

The data is available on [Github](https://github.com/PatristicTextArchive/pta_data) or [Zenodo](https://doi.org/10.5281/zenodo.4066796).

Each edition of a text is accessible through a **permalink** (using the CTS-URN): for example <https://pta.bbaw.de/text/urn:cts:pta:pta0013.pta003.pta-grc1>. The respective permalink is to found in the reader under `Reuse`. Permalinks are also available for authors/textgroups: <https://pta.bbaw.de/text/urn:cts:pta:pta0013>, as well as for works: <https://pta.bbaw.de/text/urn:cts:pta:pta0013.pta003>.

### Rendering of textual phenomena in the reader

#### Transcriptions

| Rendering | Meaning |
|----|-----|
| new line | new line |
| <span style="color:gray;">[1r/v]</span> | new folio/page with number 1 (recto/verso) (if available linked to digital facsimile)|
| <span style="color:gray;">[col.]</span> | new column |
| <span style="color:gray;">[note: place] text (hand)</span> | marginal note with text in place (by hand, if available) |
| <span style="color:red;">text</span> | rubricated text |
| <span style="text-decoration:overline;">text</span> | line above text (often: nomen sacrum) |
| <span style="font-size: 110%;font-weight:bold;padding-right:.1rem;">T</span>ext | ekthesis |
| <span style="font-size: 2rem;font-weight:bold;padding:.3rem;margin:0 .3rem 0 0;float:left;line-height:1;">T</span>ext | initial |
| ⸢deleted added (hand)⸣ | substitution of deleted with added text (by hand, if available) |
| text<sup>del.</sup> (Hand) | deleted text (without any marking; by hand, if available)|
| text* (hand)| deleted text (marked with a sign; by hand, if available) |
| <span style="text-decoration: line-through;">text</span> (hand) | deleted text (strikethrough; by hand, if available) |
| <span style="text-decoration: underline; text-decoration-style: dotted;">text</span> (hand) | deleted text (expunged; by hand, if available) |
| <span style="text-decoration: line-through; text-decoration-style: double;">text</span> (hand) | deleted text (overwritten; by hand, if available) |
| <span style="color:gray;">text</span> (hand) | deleted text (erased; by hand, if available) |
| ⟨text (hand)⟩ | added text (in line; by hand, if available) |
| text<span style="font-size: 80%; vertical-align: super;">⟨text (hand)⟩</span> | text added to text (over the line; by hand, if available) |
| _⟨hand in mg. text⟩_ |  text added in the margin (by hand, if available) |
| {text} | suppletion of lost text |
| <span style="text-decoration: underline wavy;">text</span> | unclear reading |
| > | diple |
| >> | double diple |
| ⸏ | paragraphos |
| * | asteriskos |
| <span style="color:gray; font-size: 80%;">[[illegible (1 line)]]</span> | illegible text (of length, if available) |
| <span style="color:gray; font-size: 80%;">[[damage (1 character)]]</span> | physical damage (of length, if available)  |
| <span style="color:gray; font-size: 80%;">[[fenestra (1 character)]]</span> | fenestra (of length, if available) |
| <span style="color:gray; font-size: 80%;">(1.1 edition)</span> | reference to division of text in edition |

#### Editions

| Rendering | Meaning |
|----|-----|
| <span style="color:darkred;font-style:italic;">»text«</span> | quoted lemma |
| »text_, insertion,_ text« | quote (with inserted text) |
| ›text‹ | pseudo-quote (or quote in quote or quote in direct speech) |
| „text ‚text‘ text“ | direct speech |
| _text_ | alluion |
| ⟨text⟩ | text added |
| [text] | text to be deleted | 
| †text† | crux interpretum |
| <span style="color:gray; font-size: 80%;">[[lacunam (1 line) ind. editor/source]]</span> | Lacuna, of estimated lenght (if available), by editor/source (if available) |
| <span style="color:gray;">[1 (edition/manuscript)]</span> | new page with number 1 (in edition/manuscript) |

### Manuscripts

At the moment, the database of manuscripts contains only rudimentary data on manuscripts which are edited in the PTA. That data is widely based on the data provided by [Pinakes](https://pinakes.irht.cnrs.fr/) (= “draft” status) and amended with observations by the respective editor of the description.

The entry in the [Pinakes database](https://pinakes.irht.cnrs.fr/) is linked as well as digitized versions and IIIF manifests (where available). For the texts transmitted in the manuscript, the edition in the PTA, the entry in the [Clavis Clavium database](https://clavis.brepols.net/clacla/Default.aspx) or in the [Database of Byzantine Book Epigrams](https://www.dbbe.ugent.be) is linked.

The data is available on [Github](https://github.com/PatristicTextArchive/pta_manuscripts).

Each manuscript description is accessible through a **permalink** (using the internal manuscript ID of PTA): for example <https://pta.bbaw.de/manuscripts/PTAMS00001>.
### People
People mentioned in the editions are encoded and enriched by other sources as far as possible. This functionality is partially available.

For Biblical persons the [TIPNR - Translators Individualised Proper Names with all References](https://github.com/tyndale/STEPBible-Data) are used, all other persons are referenced via the project's person index, which references GND IDs where available. For that the service [lobid-gnd | ein LOD-Dienst des hbz — Hochschulbibliothekszentrum des Landes NRW](https://lobid.org/gnd) is used.

An [Index](https://pta.bbaw.de/indices/persons) of all annotated persons is provided. The description given is based on the following sources: TIPNR = Translators Individualised Proper Names with all References (see above), AW_III_5 = Athanasius Werke III 5, Verzeichnis der Personen (Berlin/Boston 2020), AvS = Annette von Stockhausen.

### Places

As far as possible, places mentioned in the editions are encoded and enriched by data from the [Pleiades-Gazetteer](https://pleiades.stoa.org/) and the [Translators Individualized Proper Names with all References](https://github.com/tyndale/STEPBible-Data) list.

An [Index](https://pta.bbaw.de/indices/places) of all annotated places is provided. The place selected is shown on a map; for this we make use of the [Digital Atlas of the Roman Empire (DARE)](https://dh.gu.se/dare/).

### Biblical quotes

Biblical quotes (and allusions) are also encoded as far as possible.

The references for the encoded quotes are  (not for Eusebius' Commentary on the Psalms) shown in a popup, which also shows the respective quote from the Bible. For the Old Testament the digitized version of *Rahlfs'* edition of the Septuagint, provided by http://ccat.sas.upenn.edu/gopher/text/religion/biblical (via [The Unbound Bible](http://unbound.biola.edu/index.cfm) – not online anymore), is used, for the New Testament the SBL Greek New Testament (Copyright © 2010 [Society of Biblical Literature](http://www.sbl-site.org) and [Logos Bible Software](http://www.logos.com), marked as *[SBLGNT](http://sblgnt.com)*).

An [Index](https://pta.bbaw.de/indices/biblical-references) of all annotated biblical references is provided.
### Dictionary
The dictionary function is still in development. At the moment, it is also only provided for Greek texts (but not for transcriptions due to the high variability in spelling).

This function is based on an automatic (i.e. not free from errors) lemmatization done with the help of [Clérice, T. (2021). Pie Extended, an extension for Pie with pre-processing and post-processing (Version 0.0.39) [Computer software]](https://doi.org/10.5281/zenodo.3883589).

For the lexical data the following dictionaries are used: *Liddell-Scott-Jones, Greek-English Lexicon (9th ed., 1940)*, *Pape, Griechisch-deutsches Handwörterbuch (3. Aufl., 1914)*, in the digital versions provided by [Chaeréphon (André Charbonnet)](http://chaerephon.e-monsite.com/medias/files/bailly.html) (through [biblissima/eulexis](http://outils.biblissima.fr/resources/eulexis/data.tar.gz)), and *Translators Brief lexicon of Extended Strongs for Greek*, which is based on *Abbot-Smith, A Manual Greek Lexicon of the New Testament (1922)* as provided by [StepBible.org (licensed CC BY)](https://github.com/STEPBible/STEPBible-Data/blob/master/TBESG%20-%20Translators%20Brief%20lexicon%20of%20Extended%20Strongs%20for%20Greek%20-%20STEPBible.org%20CC%20BY.txt)

### Analyse text with Voyant Tools

You can forward the XML of the current text to [Voyant Tools](https://voyant-tools.org/) and analyse it with the tools provided there. 
Please note that the texts are not lemmatised. We'll make lemmatized texts available for the feature in the future.

### Cover picture

The cover picture of PTA is a detail of [f. 78r der Handschrift Paris, BnF, Grec 510](https://gallica.bnf.fr/ark:/12148/btv1b84522082/f169) (Source gallica.bnf.fr / BnF).


## Technical Implementation

### API (ediarum.Web)

Data can be accessed through a public API. The API is provided by [ediarum.WEB](https://github.com/ediarum/ediarum.WEB). The endpoints are defined by a eXist-db application and a central manifest file compatible with ediarum.WEB. For further reference see the [ediarum.WEB documentation](https://github.com/ediarum/ediarum.WEB/blob/master/APPCONF.md).

There are several types of endpoints (more information on endpoints and parameters is to be found in the [ediarum.WEB documentation](https://github.com/ediarum/ediarum.WEB/blob/master/API.md)):

- via `/api` you get the manifest file (`appconf.xml`), which has the definition of endpoints.
- The endpoints for object types (`/api/<object-type>`) and endpoints for objects (`/api/<object-type>/<object-id>`) provide access to the following object types:
  - `cts` provides a [CTS compatible API](https://github.com/cite-architecture/cts_spec/blob/master/md/specification.md) (only GetPassage is implemented)
    - Example for getting a passage via the CTS API: <http://pta.bbaw.de/api/cts?request=GetPassage&urn=urn:cts:pta:pta0036.pta001.pta-grc1:2.1.4>.
  - `pta` provides the editions
  - `pta-textgroup` provides metadata to the textgroups (authors)
  - `pta-work` provides metadata to the works
  - `pta-version` provides metadata to editions of the works (editions, translations)
  - `msdesc` provides manuscript transcriptions
  - `msitem` provides information on the works in the manuscripts transcriptions
  - `author` provides an index of authors
  - `persons` provides an index of persons
  - `places` provides an index of places 
  - `pta-other-work` provides metadata of works not yet available in the PTA
  - `bible-quotation` provides biblical quotes
  - `pta-lexicon-grc` provides dictionary entries to lemmata exstant in texts in the PTA
  - `wordlemma-grc` provides lemmatisation data to word forms extant in texts in the PTA
- endpoints for relations between objects
- endpoints for search; `/api/search/<search-id>` has the following searches:
  - `fulltext` search in full text without variants and notes
  - `metadata` search in the metadata of the texts
  - `readings` search in variants
  - `notes` search in notes

### Backend (eXist-DB)

The data for the web application are stored in a [eXist-db](http://www.exist-db.org/) and are administered by the [ediarum](https://www.ediarum.org/) module [ediarum.DB](https://github.com/ediarum/ediarum.DB). It is possible to access data through the public API (see aboive).


### Frontend (Nuxt.js)

The web app is based on the Vue.js framework [Nuxt.js](https://nuxtjs.org/). It is statically rendered (static site generator) and therefore only needs a web server as infrastructure. Backend data is fetched using the publicly available API.

#### Modules & plugins
The PTA webapp uses the following additional modules and plugins:

- [Vuex](https://vuex.vuejs.org): state management
- [TailwindCSS](https://tailwindcss.com): CSS framework
- [Nuxt Content](https://content.nuxtjs.org): headless CMS
- [Nuxt i18n](https://i18n.nuxtjs.org): interface translation
- [Nuxt Axios](https://axios.nuxtjs.org/): AJAX requests
- [Nuxt Optimized Images](https://github.com/juliomrqz/nuxt-optimized-images): auto-optimizing image data
- [Matomo](https://matomo.org): user statistics
- [CETEIcean.js](https://github.com/TEIC/CETEIcean): TEI rendering
- [V-RuntimeTemplate](https://github.com/alexjoverm/v-runtime-template): runtime compilation of Vue templates
- [V-Tooltip](https://akryum.github.io/v-tooltip/#/): tooltip library
- [Nuxt Leaflet](https://github.com/schlunsen/nuxt-leaflet): map rendering

#### Rendering and annotating TEI XML
TEI XML data is displayed without the need of XSLT transformations by using native browser features (Web Components, Custom Elements). This functionality is offered by the Javascript library [CETEIcean.js](https://github.com/TEIC/CETEIcean).

CETEIcean does not only allow the unmodified display of TEI directly in the browser, one can also modify the resulting HTML in an intermediate step. For instance, the reader interface makes use of this by injecting HTML code of a Vue component which, once rendered, displays contents of text annotations (persons, places, bible quotations).

The TEI rendering process can be summed up in these three steps:

1. Fetch TEI XML data via public API
2. Display TEI data using CETEIcean.js, while injecting custom Vue code (e.g. to display text annotations)
3. Pre-render the resulting HTML string via VRuntimeTemplate plugin


#### Texts
All other texts in the PTA are encoded in markdown format and administered via the headless CMS ([Nuxt Content](https://content.nuxtjs.org)).

#### Languages of the interface
The interface is currently available in German and English, Italian is work in progress. The transaltions are in json format according to i18n standard. More languages are planned. We happily accept [contributions](../project/contributing)!

### Search (eXist-DB)

There are several enpoints for search in the API (see above):

  - `/api/search/fulltext` search in full text without variants and notes
  - `/api/search/metadata` search in the metadata of the texts
  - `/api/search/readings` search in variants
  - `/api/search/notes` search in notes

The search is based on the lucene search integrated into eXist-db. endpoints of the API are made available through ediarum.WEB  (please refer to the [documentation](https://github.com/ediarum/ediarum.WEB/blob/master/API.md#3-searching)).

#### Search with regular expressions

Search all forms of ἥλιος:

`/api/search/fulltext?type=regex&q=[ἡἥ]λ[ίι].{1,3}`

#### Search for phrases within a distance

Search for two word which appear within a certain distance (`slop`) in the texts:

`/api/search/fulltext?type=phrase&slop=20&q=θεὸς ἄνθρωπον`

#### Search with lucene syntax expressions

More complicated search expressions can be built using [Lucene syntax](https://lucene.apache.org/core/2_9_4/queryparsersyntax.html). Possible are for example searches with:

- Wildcards (not in search for phrases unfortunately) `?`, `*`
  - for example `te?t` or `te*t`
- Fuzzy search using Levenshtein distance with `~`
  - for example `text~`
- search for phrases / search within distance by providing the distince (with `~`)
  - for example `"text lang"~10`
- combination of these searches using `AND`, `NOT` and grouping `(`, `)`
  - for example `(edition OR translation) AND digital`

