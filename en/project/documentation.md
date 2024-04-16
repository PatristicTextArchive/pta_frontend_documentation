## Editorial Implementation

### Transcription of manuscripts and (critical) editions

-> Look here: [Encoding guidelines](../project/encoding-guidelines) (only German at the moment)

### Texts
Where available, each text is linked to the matching entries in the databases of [Clavis Clavium](https://clavis.brepols.net/clacla/Default.aspx) and of [Pinakes](https://pinakes.irht.cnrs.fr/); IDs of the TLG© for authors and works are also shown (no linking is possible).

The data is available on [Github](https://github.com/PatristicTextArchive/pta_data) or [Zenodo](https://doi.org/10.5281/zenodo.4066796).

Each edition of a text is accessible through a **permalink** (using the CTS-URN): for example <https://pta.bbaw.de/text/urn:cts:pta:pta0013.pta003.pta-grc1>; the **versioned permalink** reflects a specific  state of publication, for example <https://pta.bbaw.de/text/9970133a/urn:cts:pta:pta0013.pta003.pta-grc1>. The respective permalink is to found in the reader under `Reuse`. Permalinks are also available for authors/textgroups: <https://pta.bbaw.de/text/urn:cts:pta:pta0013>, as well as for works: <https://pta.bbaw.de/text/urn:cts:pta:pta0013.pta003>.

For all features look [here](../project/help).

### Manuscripts

At the moment, the database of manuscripts contains only rudimentary data on manuscripts which are edited in the PTA. That data is widely based on the data provided by [Pinakes](https://pinakes.irht.cnrs.fr/) (= “draft” status) and amended with observations by the respective editor of the description.

The entry in the [Pinakes database](https://pinakes.irht.cnrs.fr/) is linked as well as digitized versions and IIIF manifests (where available). For the texts transmitted in the manuscript, the edition in the PTA, the entry in the [Clavis Clavium database](https://clavis.brepols.net/clacla/Default.aspx) or in the [Database of Byzantine Book Epigrams](https://www.dbbe.ugent.be) is linked. If digitized images of the manuscripts are available (via IIIF), they are accessible in the inline viewer.

The data is available on [Github](https://github.com/PatristicTextArchive/pta_manuscripts).

Each manuscript description is accesible through a **permalink** (using the internal manuscript-ID): for example  <https://pta.bbaw.de/de/manuscripts/PTAMS00325>; the **versioned permalink** reflects a specific  state of publication, for example <https://pta.bbaw.de/de/manuscripts/80476827/PTAMS00325>.
### People
People mentioned in the editions are encoded and enriched by other sources as far as possible. This functionality is partially available.

For Biblical persons the [TIPNR - Translators Individualised Proper Names with all References](https://github.com/tyndale/STEPBible-Data) are used, all other persons are referenced via the project's person index, which references GND IDs and [Wikidata](https://www.wikidata.org) IDs where available. For GND Ids the service [lobid-gnd | ein LOD-Dienst des hbz — Hochschulbibliothekszentrum des Landes NRW](https://lobid.org/gnd) is used.

An [Index](https://pta.bbaw.de/indices/persons) of all annotated persons is provided. The description given is based on the following sources: TIPNR = Translators Individualised Proper Names with all References (see above), AW_III_5 = Athanasius Werke III 5, Verzeichnis der Personen (Berlin/Boston 2020), AvS = Annette von Stockhausen. CAVEAT: Not all text are (fully) annotated.

### Places

As far as possible, places mentioned in the editions are encoded and enriched by data from the [Pleiades-Gazetteer](https://pleiades.stoa.org/) and the [Translators Individualized Proper Names with all References](https://github.com/tyndale/STEPBible-Data) list.

An [Index](https://pta.bbaw.de/indices/places) of all annotated places is provided. All places as well as the  place selected are shown on a map; for this we make use of the [Digital Atlas of the Roman Empire (DARE)](https://dh.gu.se/dare/). CAVEAT: Not all text are (fully) annotated.

### Biblical quotes

Biblical quotes (and allusions) are also encoded as far as possible.

The references for the encoded quotes are  (not for Eusebius' Commentary on the Psalms) shown in an apparatus, which also shows the respective quote from the Bible. For the Old Testament the digitized version of *Rahlfs'* edition of the Septuagint is used, for the New Testament the SBL Greek New Testament (Copyright © 2010 [Society of Biblical Literature](http://www.sbl-site.org) and [Logos Bible Software](http://www.logos.com), marked as *[SBLGNT](http://sblgnt.com)*), as provided at <https://pta.bbaw.de/text/urn:cts:pta:pta9999>.

For references to the Hexapla links to *Frederick Field (ed.): Origenis hexaplorum quae supersunt: sive veterum interpretum Graecorum in totum vetus testamentum fragmenta. Post Flaminium nobilium, Drusium, et Montefalconium, adhibita etiam versione Syro-Hexaplari. 2 vols. Oxford: Clarendon Press, 1875 ([vol. 1: Genesis – Esther](https://archive.org/details/origenhexapla01unknuoft); [vol. 2: Hiob – Maleachi](https://archive.org/details/origenhexapla02unknuoft)* and for references to the Vulgata links to the online version of *[Robert Weber/Roger Gryson (edd.), Biblia Sacra iuxta Vulgatam versionem. Editio quinta. Stuttgart: Deutsche Bibelgesellschaft, 2007](https://www.bibelwissenschaft.de/online-bibeln/biblia-sacra-vulgata/lesen-im-bibeltext/)* are provided.


An [Index](https://pta.bbaw.de/indices/biblical-references) of all annotated biblical references is provided. CAVEAT: Not all text are (fully) annotated.

### Dictionary

The dictionary function uses the service of the [Classical Language Dictionary](https://cld.bbaw.de) for (automatic) lemmatization and its [dictionaries](https://cld.bbaw.de/documentation/dictionaries).

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
  - `cts` provides a [CTS compatible API](https://github.com/cite-architecture/cts_spec/blob/master/md/specification.md) (only GetPassage is currently implemented)
    - Example for getting a passage via the CTS API: <http://pta.bbaw.de/api/cts?request=GetPassage&urn=urn:cts:pta:pta0036.pta001.pta-grc1:2.1.4>.
  - `pta` provides the editions
  - `pta-textgroup` provides metadata to the textgroups (authors)
  - `pta-work` provides metadata to the works
  - `pta-version` provides metadata to editions of the works (editions, translations)
  - `msdesc` provides manuscript transcriptions
  - `msitem` provides information on the works in the manuscripts transcriptions
  - `persons` provides an index of persons
  - `places` provides an index of places 
  - `bible-references` provides biblical quotes
- endpoints for relations between objects
- endpoints for search; `/api/search/<search-id>` has the following searches:
  - `fulltext` search in full text without variants and notes
  - `metadata` search in the metadata of the texts
  - `readings` search in variants
  - `notes` search in notes

The search is based on the lucene search integrated into eXist-db. endpoints of the API are made available through ediarum.WEB  (please refer to the [documentation](https://github.com/ediarum/ediarum.WEB/blob/master/API.md#3-searching)).

### Backend (eXist-DB)

The data for the API and for the search used by the web application are stored in a [eXist-db](http://www.exist-db.org/), which fetches the data with the eXistdb-App Tuttle from the [data repositories](data.md) befüllt wird; the database is administered by the [ediarum](https://www.ediarum.org/) module [ediarum.DB](https://github.com/ediarum/ediarum.DB). It is possible to access data through the public API (see above).


### Frontend 

The PTA Web application ist a [Vue.js Single Page Application](https://vuejs.org/) on top of a [Laravel PHP backend](https://laravel.com/). The backend provides serveral internal restful APIs for including the versioned data in the repositories used ([pta_data](https://github.com/PatristicTextArchive/pta_data), [pta_lexika](https://github.com/PatristicTextArchive/pta_lexika), [pta_manuscripts](https://github.com/PatristicTextArchive/pta_manuscripts), [pta_metadata](https://github.com/PatristicTextArchive/pta_metadata), [pta_frontend_documentation](https://github.com/PatristicTextArchive/pta_frontend_documentation)). The search functions use (amongst others) the public PTA API (see above).


#### Modules & plugins
The PTA webapp uses the following additional modules and plugins:

- [Vue Router](https://router.vuejs.org/)
- [Axios](https://github.com/axios/axios)
- [TailwindCSS](https://tailwindcss.com)
- [Matomo](https://matomo.org)
- [CETEIcean.js](https://github.com/TEIC/CETEIcean)
- [vue-leaflet](https://github.com/vue-leaflet)
- [leaflet](https://leafletjs.com/)
- [greek-utils](https://github.com/vbarzokas/greek-utils)


#### Languages of the interface
The interface is currently available in German and English, Italian is work in progress. The translations are in json format according to i18n standard. More languages are planned. We happily accept [contributions](../project/contributing)!
