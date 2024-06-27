## Editorische Umsetzung

### Handschriften-Transkriptionen und kritische Editionen

-> S. hier: [Editionsrichtlinien](../project/encoding-guidelines)

### Texte
Soweit vorhanden werden für alle Texte Links auf die entsprechenden Werk-Einträge der [Clavis Clavium](https://clavis.brepols.net/clacla/Default.aspx)- und der [Pinakes-](https://pinakes.irht.cnrs.fr/) Datenbank gesetzt; außerdem werden die Autoren-/Werk-IDs des TLG© angezeigt (eine Verlinkung ist nicht möglich).

Die zugrundliegenden Daten sind auf [Github](https://github.com/PatristicTextArchive/pta_data) oder [Zenodo](https://doi.org/10.5281/zenodo.4066796) erhältlich.

Jede Edition ist über einen **Permalink** (unter Verwendung der CTS-URN) erreichbar: z.B. <https://pta.bbaw.de/text/urn:cts:pta:pta0013.pta003.pta-grc1>; seine **versionierte** Fassung, die einen spezifischen Veröffentlichungsstand widerspiegelt, lautet z.B. <https://pta.bbaw.de/text/9970133a/urn:cts:pta:pta0013.pta003.pta-grc1>. Der jeweilige Permalink ist in der Leseoberfläche unter der Rubrik `Nachnutzung` angeführt. Permalinks existieren auch für Autoren/Textgruppen: <https://pta.bbaw.de/text/urn:cts:pta:pta0013> sowie für Werke: <https://pta.bbaw.de/text/urn:cts:pta:pta0013.pta003>.

Eine Übersicht der textbezogenen Funktionalitäten findet sich [hier](../project/help).


### Handschriftendatenbank

Die Handschriftendatenbank umfasst momentan nur rudimentäre Daten zu den Handschriften, die im PTA edierte Werke überliefern.
Die Daten basieren auf den Angaben der [Pinakes-Datenbank](https://pinakes.irht.cnrs.fr/) (= »Entwurf«-Status), die von den jeweiligen Bearbeitern durch Autopsie ergänzt wurden.

Verlinkt sind neben dem jeweiligen Eintrag in der [Pinakes-Datenbank](https://pinakes.irht.cnrs.fr/) (soweit vorhanden) Digitalisate und IIIF-Manifeste sowie für die in der Handschrift überlieferten Texte die Editionen im PTA bzw. der entsprechende Eintrag in der [Clavis Clavium-Datenbank](https://clavis.brepols.net/clacla/Default.aspx) oder der [Database of Byzantine Book Epigrams](https://www.dbbe.ugent.be). Stehen Digitalisate (per IIIF) zur Verfügung kann auf sie im Viewer direkt zugegriffen werden.

Die zugrundliegenden Daten sind auf [Github](https://github.com/PatristicTextArchive/pta_manuscripts) erhältlich.

Jede Handschriftenbeschreibung ist über einen **Permalink** (unter Verwendung der Handschriften-ID) erreichbar: z.B. <https://pta.bbaw.de/de/manuscripts/PTAMS00325>; seine **versionierte** Fassung, die einen spezifischen Veröffentlichungsstand widerspiegelt, lautet z.B. <https://pta.bbaw.de/de/manuscripts/80476827/PTAMS00325>.

### Personen und Personengruppen
In den Editionen vorkommende Personen werden nach Möglichkeit ausgezeichnet und mit weiteren Informationen aus anderen Quellen angereichert. Diese Funktionalität steht erst teilweise zur Verfügung.

Für biblische Personen wird dabei auf die [TIPNR - Translators Individualised Proper Names with all References](https://github.com/tyndale/STEPBible-Data) (bei [commit b83a3cf1 (31. Mai 2024)](https://github.com/STEPBible/STEPBible-Data/commit/b83a3cf1224af5cf72606d86d6be1789adc69541)) zurückgegriffen, für alle übrigen Personen wird ein eigenes Register geführt, in dem – soweit vorhanden – die IDs der GND bzw. von [Wikidata](https://www.wikidata.org) referenziert werden, wobei für GND-IDs auf den Service [lobid-gnd | ein LOD-Dienst des hbz — Hochschulbibliothekszentrum des Landes NRW](https://lobid.org/gnd) zurückgegriffen wird.

Es wird ein [Register](https://pta.bbaw.de/indices/persons) aller annotierten Personen bereitgestellt. Die Quelle, auf der die Beschreibung der Person basiert, ist jeweils abgekürzt angegeben: TIPNR = Translators Individualised Proper Names with all References (s.o.), AW_III_5 = Athanasius Werke III 5, Verzeichnis der Personen (Berlin/Boston 2020), AvS = Annette von Stockhausen, php = Philipp Pilhofer. ACHTUNG: Nicht alle Texte sind (vollständig) annotiert, der Stand der Annotation ist im Reader (bzw. im teiHeader der XML-Datei) einzusehen.

### Orte

In den Editionen vorkommende Orte werden nach Möglichkeit ebenfalls ausgezeichnet und mit weiteren Informationen aus dem [Pleiades-Gazetteer](https://pleiades.stoa.org/) (unter Verwendung von <http://atlantides.org/downloads/pleiades/json/pleiades-places-20240613.json.gz>) bzw. der [Translators Individualized Proper Names with all References](https://github.com/tyndale/STEPBible-Data)-Liste (bei [commit b83a3cf1 (31. Mai 2024)](https://github.com/STEPBible/STEPBible-Data/commit/b83a3cf1224af5cf72606d86d6be1789adc69541)) angereichert.

Es wird ein [Register](https://pta.bbaw.de/indices/places) aller annotierten Orte bereitgestellt. Alle im Register befindlichen Orte und der im Register jeweils ausgewählte Ort werden auf einer Karte dargestellt; dafür wird auf den [Digital Atlas of the Roman Empire (DARE)](https://dh.gu.se/dare/) zurückgegriffen. ACHTUNG: Nicht alle Texte sind (vollständig) annotiert, der Stand der Annotation ist im Reader (bzw. im teiHeader der XML-Datei) einzusehen.

### Bibelstellen

In den Editionen vorkommende Bibelzitate (oder -anspielungen) werden ebenfalls nach Möglichkeit ausgezeichnet.

Die ausgezeichneten Stellen werden in einem Apparat nachgewiesen und zitieren die jeweilige Bibelstelle. Dabei wird für alttestamentliche Stellen auf die Digitalisierung der Septuaginta-Edition von *Rahlfs* und für neutestamentlichen Stellen auf das SBL Greek New Testament (Copyright © 2010 [Society of Biblical Literature](http://www.sbl-site.org) and [Logos Bible Software](http://www.logos.com), markiert mit *[SBLGNT](http://sblgnt.com)*) in der Fassung zurückgegriffen, in der sie unter <https://pta.bbaw.de/text/urn:cts:pta:pta9999> einzusehen sind.

Bei Stellen aus der Hexapla wird die entsprechende Seite von *Frederick Field (ed.): Origenis hexaplorum quae supersunt: sive veterum interpretum Graecorum in totum vetus testamentum fragmenta. Post Flaminium nobilium, Drusium, et Montefalconium, adhibita etiam versione Syro-Hexaplari. 2 vols. Oxford: Clarendon Press, 1875 ([vol. 1: Genesis – Esther](https://archive.org/details/origenhexapla01unknuoft); [vol. 2: Hiob – Maleachi](https://archive.org/details/origenhexapla02unknuoft)* verlinkt, bei Stellen aus der Vulgata auf die online Version von *[Robert Weber/Roger Gryson (edd.), Biblia Sacra iuxta Vulgatam versionem. Editio quinta. Stuttgart: Deutsche Bibelgesellschaft, 2007](https://www.bibelwissenschaft.de/online-bibeln/biblia-sacra-vulgata/lesen-im-bibeltext/)*.

Es wird ein [Register](https://pta.bbaw.de/indices/biblical-references) aller annotierten Bibelstellen bereitgestellt. ACHTUNG: Nicht alle Texte sind (vollständig) annotiert.

### Lexikon

Die Lexikon-Funktion greift zur (automatischen) Lemmatisierung und für die [Wörterbücher](https://cld.bbaw.de/documentation/dictionaries) auf den Service des [Classical Language Dictionary](https://cld.bbaw.de) zurück. Für Syrisch wird die [SEDRA IV API (v1.0.0)](https://sedra.bethmardutho.org/about/openapi) benutzt.

### Analyse mit Hilfe der Voyant Tools

Die XML-Fassung des jeweiligen Textes kann per Klick an die [Voyant Tools](https://voyant-tools.org/) übergeben werden und mit den dort zur Verfügung stehenden Tools analysiert werden. Zu beachten ist, dass die Texte nicht lemmatisiert sind. In Zukunft werden für diese Funktion auch lemmatisierte Texte zur Verfügung gestellt werden.

### Titelbild

Das Titelbild des PTA ist ein Ausschnitt aus [f. 78r der Handschrift Paris, BnF, Grec 510](https://gallica.bnf.fr/ark:/12148/btv1b84522082/f169) (Source gallica.bnf.fr / BnF).

## Technische Umsetzung

### API (ediarum.Web)

Auf die Daten kann über die öffentlich verfügbare API zugegriffen werden. Die API wird mithilfe des ediarum-Moduls [ediarum.WEB](https://github.com/ediarum/ediarum.WEB) bereitgestellt. Die einzelnen Endpoints und Zugriffe werden in einer eXist-db-Applikation und einer zentralen ediarum.WEB kompatiblen Manifestdatei definiert. Siehe dazu auch die entsprechende [Dokumentation](https://github.com/ediarum/ediarum.WEB/blob/master/APPCONF.md).

Es gibt verschiedene Typen von Endpoints (detailliertere Informationen der Endpoints und möglicher Parameter findet sich in der entsprechenden [Dokumentation](https://github.com/ediarum/ediarum.WEB/blob/master/API.md)):

- Unter `/api` erhält man die Manifestdatei (`appconf.xml`), welche die vollständige Definition der Endpoints enthält.
- Die Endpoints für Objektsammlungen `/api/<object-type>` und Endpoints für einzelne Objekte `/api/<object-type>/<object-id>` erlauben den Zugriff auf folgende Objekttypen:
  - `cts` stellt eine [CTS-kompatible Schnittstelle](https://github.com/cite-architecture/cts_spec/blob/master/md/specification.md) zur Verfügung (nur GetPassage ist bisher implementiert)
    - Beispiel für Abruf einer Passage über die CTS-API: <http://pta.bbaw.de/api/cts?request=GetPassage&urn=urn:cts:pta:pta0036.pta001.pta-grc1:2.1.4>.
  - `pta` umfasst die Editionstexte
  - `pta-textgroup` umfasst Metadaten zu den Textgruppen (nach Autoren)
  - `pta-work` umfasst Metadaten zu einzelnen Werken
  - `pta-version` umfasst Metadaten zu Ausgaben der Werke (Editionen, Übersetzungen)
  - `msdesc` umfasst Handschriftenbeschreibungen
  - `msitem` umfasst Informationen zu den in den Handschriftenbeschreibungen enthaltenen Werken
  - `persons` umfasst Personen
  - `places` umfasst Orte
  - `bible-references` umfasst Bibelzitate
- Endpoints für Beziehungen zwischen Objekten
- Endpoints für Suchen; `/api/search/<search-id>` enthält folgende Suchmöglichkeiten:
  - `fulltext` Suche im Volltext ohne Varianten und ohne Anmerkungen
  - `metadata` Suche in den Metadaten der Texte
  - `readings` Suche in den Varianten
  - `notes` Suche in den Anmerkungen

  Die Suche basiert auf der in eXist-db integrierten Lucene-Suche. Die API-Endpoints werden über ediarum.WEB zur Verfügung gestellt. (S.a. die dortige [Dokumentation](https://github.com/ediarum/ediarum.WEB/blob/master/API.md#3-searching))


### Backend (eXist-DB)

Die Daten für die API und die in der Webapplikation verwendete Suche liegen in einer [eXist-db](http://www.exist-db.org/), die durch die eXistdb-App Tuttle aus den [Daten-Repositorien](data.md) befüllt wird; die Daten werden über das [ediarum](https://www.ediarum.org/)-Modul [ediarum.DB](https://github.com/ediarum/ediarum.DB) verwaltet. Auf die Daten kann über die öffentlich verfügbare API zugegriffen werden. Mithilfe einer eXist-db-Applikation werden die einzelnen Endpoints der API definiert (s. oben).

### Frontend

Die PTA Webapplikation ist eine [Vue.js Single Page Application](https://vuejs.org/), die auf einem [Laravel PHP-Backend](https://laravel.com/) aufsitzt. Das Backend stellt zudem verschiedene interne restful Schnittstellen für den Zugriff auf den versionierten Inhalt der genutzten Repositorien ([pta_data](https://github.com/PatristicTextArchive/pta_data), [pta_lexika](https://github.com/PatristicTextArchive/pta_lexika), [pta_manuscripts](https://github.com/PatristicTextArchive/pta_manuscripts), [pta_metadata](https://github.com/PatristicTextArchive/pta_metadata), [pta_frontend_documentation](https://github.com/PatristicTextArchive/pta_frontend_documentation)) bereit. Die Suchfunktionen greifen zum Teil auf die öffentlich verfügbare PTA-API (s.o.) zurück.

#### Module & Plugins
Folgende Zusatzmodule finden Einsatz in der PTA Webapp:

- [Vue Router](https://router.vuejs.org/)
- [Axios](https://github.com/axios/axios)
- [TailwindCSS](https://tailwindcss.com)
- [Matomo](https://matomo.org)
- [CETEIcean.js](https://github.com/TEIC/CETEIcean)
- [vue-leaflet](https://github.com/vue-leaflet)
- [leaflet](https://leafletjs.com/)
- [greek-utils](https://github.com/vbarzokas/greek-utils)


#### Interface-Sprachen
Das Interface ist aktuell in den Sprachen Deutsch und Englisch verfügbar, Italienisch ist in Vorbereitung. Technisch verwaltet werden Übersetzungen im i18n-Standard als JSON-Dateien. In Zukunft sind auch weitere Sprachen für das Interface geplant. Eine aktive [Mitwirkung](../project/contributing) ist sehr willkommen!

