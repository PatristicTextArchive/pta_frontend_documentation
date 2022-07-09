## Alle Daten

- [Alle Texte als XML-Dateien](https://github.com/PatristicTextArchive/pta_data)
- [Alle Handschriftenbeschreibungen als XML-Dateien](https://github.com/PatristicTextArchive/pta_manuscripts)
- [Alle im Frontend verwendeten Metadaten](https://github.com/PatristicTextArchive/pta_metadata)
- [Alle im Frontend verwendeten Lexikon-Daten](https://github.com/PatristicTextArchive/pta_lexika)
- [Schema für Editionen](https://github.com/PatristicTextArchive/Schema)


## Linked Open Data

Das [Metadata-Repositorium](https://github.com/PatristicTextArchive/pta_metadata) enthält die vorhandenen LOD-Informationen des [Patristic Text Archive (PTA)](https://pta.bbaw.de) unter <https://github.com/PatristicTextArchive/pta_metadata/LOD>. 

Zur Zeit stellen wir diese Informationen als Tabellen im CSV-Format, als [BEACON-Dateien](https://gbv.github.io/beaconspec/beacon.html) und als [RDF-Dateien](https://www.w3.org/RDF/) (turtle, rdf/xml, JSON-LD) zur Verfügung.

### Autoren der Werke im PTA
unter Verwendung der [Gemeinsamen Normdatei](http://d-nb.info/gnd/) und von [Wikidata](https://www.wikidata.org/)

- [pta_authors.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors.csv) (Spalten: GND-ID,Wikidata-Entity,URN)
- [pta_authors_gnd_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_gnd_beacon.txt), [pta_authors_gnd.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_gnd.xml), [pta_authors_gnd.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_gnd.ttl), [pta_authors_gnd.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_gnd.json-ld) (Alle Autoren im PTA, die durch eine GND-ID identifiziert sind)
- [pta_authors_wikidata_beacon.txt](pta_authors_wikidata_beacon.txt), [pta_authors_wikidata.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_wikidata.xml), [pta_authors_wikidata.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_wikidata.ttl), [pta_authors_wikidata.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_wikidata.json-ld) (Alle Autoren im PTA, die durch eine Wikidata-ID identifiziert sind)

### Werke im PTA
unter Verwendung von [Clavis Clavium](https://clavis.brepols.net/clacla) und [Pinakes](https://pinakes.irht.cnrs.fr)

- [pta_works.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works.csv) (Spalten: CPG no.,BHG no.,Pinakes-Oeuvre no.,URN)
- [pta_works_cpg_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_cpg_beacon.txt), [pta_works_cpg.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_cpg.xml), [pta_works_cpg.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_cpg.ttl), [pta_works_cpg.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_cpg.json-ld) (Alle Werke im PTA, die durch eine Clavis Patrum Graecorum ID identifiziert sind)
- [pta_works_bhg_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_bhg_beacon.txt), [pta_works_bhg.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_bhg.xml), [pta_works_bhg.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_bhg.ttl), [pta_works_bhg.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_bhg.json-ld) (Alle Werke im PTA, die durch eine Bibliographia Hagriographica Graeca ID identifiziert sind)
- [pta_works_pinakes-oeuvre_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_pinakes-oeuvre_beacon.txt), [pta_works_pinakes-oeuvre.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_pinakes-oeuvre.xml), [pta_works_pinakes-oeuvre.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_pinakes-oeuvre.ttl), [pta_works_pinakes-oeuvre.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_pinakes-oeuvre.json-ld) (Alle Werke im PTA, die durch eine Pinakes Oeuvre ID identifiziert sind)

### Handschriftenbeschreibungen im PTA
unter Verwendung von [Pinakes](https://pinakes.irht.cnrs.fr)

- [pta_manuscripts_diktyon.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_manuscripts_diktyon.csv) (Spalten: Diktyon-ID,URN)
- [pta_manuscripts_diktyon_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_manuscripts_diktyon_beacon.txt), [pta_manuscripts_diktyon.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_manuscripts_diktyon.xml), [pta_manuscripts_diktyon.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_manuscripts_diktyon.ttl), [pta_manuscripts_diktyon.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_manuscripts_diktyon.json-ld) (Alle Handschriften, die durch eine Diktyon-ID identifiziert sind)

### Biblische Referenzen in den Texten des PTA
Folgende Editionen werden verwendet: Hexapla, LXX = Septuagint, NA = Greek New Testament, Vg = Vulgata

Die biblischen Bücher werden folgendermaßen abgekürzt: 
- Gn, Ex, Lv, Num, Dt, Jos, Judg, Rt, 1Sa, 2Sa, 1Ko, 2Ko, 1Chr, 2Chr, 3Esr, Esr, Est, Jdt, Tob, 1Mak, 2Mak, 3Mak, 4Mak, Ps, Oden, Prov, Eccl, Song, Job, Wis, Sir, PsSal, Hos, Am, Mi, Joel, Ob, Jon, Nah, Hab, Zeph, Hag, Sach, Mal, Is, Jr, Bar, Lam, EpistJer, Hes, Sus, Dn, Bel
- Mt, Mk, Lk, Jn, Act, Rom, 1Cor, 2Cor, Gal, Eph, Phil, Col, 1Th, 2Th, 1Tim, 2Tim, Tt, Phm, Heb, Jak, 1P, 2P, 1Jn, 2Jn, 3Jn, Jud, Rev

#### Links zu den entsprechenden Stellen in den Texten
- [pta_biblereferences.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_biblereferences.csv) (Spalten: Quotation-URL,Edition,Reference)

#### Links zum Bibelstellenindex
- [pta_biblereferences_index.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_biblereferences_index.csv) (Spalten: Edition,Reference,Reference in Index)

### Personen in den Texten des PTA
unter Verwendung der [Gemeinsamen Normdatei](http://d-nb.info/gnd/) und von [Wikidata](https://www.wikidata.org/)

#### Links zu den entsprechenden Stellen in den Texten
- [pta_persons.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons.csv) (Spalten: GND-ID,Wikidata-Entity,mentioned in)

#### Links zum Personenindex
- [pta_persons_index.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index.csv) (Spalten: GND-ID,Wikidata-Entity,Person in index)
- [pta_persons_gnd_index_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_gnd_index_beacon.txt), [pta_persons_index_gnd.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index_gnd.xml), [pta_persons_index_gnd.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index_gnd.ttl), [pta_persons_index_gnd.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index_gnd.json-ld) (Alle Personen im Index, die durch eine GND-ID identifiziert sind)
- [pta_persons_wikidata_index_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_wikidata_index_beacon.txt), [pta_persons_index_wikidata.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index_wikidata.xml), [pta_persons_index_wikidata.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index_wikidata.ttl), [pta_persons_index_wikidata.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index_wikidata.json-ld) (Alle Personen im Index, die durch eine Wikidata-ID identifiziert sind)

### Organisationen und Gruppen in den Texten des PTA
unter Verwendung der [Gemeinsamen Normdatei](http://d-nb.info/gnd/) und von [Wikidata](https://www.wikidata.org/)

#### Links zu den entsprechenden Stellen in den Texten
- [pta_orgs.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs.csv) (columns: GND-ID,Wikidata-Entity,mentioned in)

#### Links zum Gruppenindex
- [pta_orgs_index.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index.csv) (Spalten: GND-ID,Wikidata-Entity,Person in index)
- [pta_orgs_gnd_index_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_gnd_index_beacon.txt), [pta_orgs_index_gnd.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index_gnd.xml), [pta_orgs_index_gnd.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index_gnd.ttl), [pta_orgs_index_gnd.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index_gnd.json-ld) (Alle Einträge im Gruppenindex, die durch eine GND-ID identifiziert sind)
- [pta_orgs_wikidata_index_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_wikidata_index_beacon.txt), [pta_orgs_index_wikidata.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index_wikidata.xml), [pta_orgs_index_wikidata.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index_wikidata.ttl), [pta_orgs_index_wikidata.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index_wikidata.json-ld) (Alle Einträge im Gruppenindex, die durch eine Wikidata-ID identifziert sind)

### Ort in den Texten des PTA
unter Verwendung des [Pleiades Gazetteer](https://pleiades.stoa.org/)

#### Links zu den entsprechenden Stellen in den Texten
- [pta_places.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_places.csv) (Spalten: Place,mentioned in)

#### Links zum Ortindex
- [pta_places_index.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_places_index.csv) (Spalten: Place,Place in index)
- [pta_places_index_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_places_index_beacon.txt), [pta_places_index.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_places_index.xml), [pta_places_index.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_places_index.ttl), [pta_places_index.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_places_index.json-ld) (Alle Einträge im Ortsindex, die durch eine Pleiades Gazetteer ID identifziert sind)