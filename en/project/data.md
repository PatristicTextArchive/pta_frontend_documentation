## All data

- [All texts as XML-files](https://github.com/PatristicTextArchive/pta_data)
- [All manuscript descriptions as XML-files](https://github.com/PatristicTextArchive/pta_manuscripts)
- [All metadata used in the frontend and LOD](https://github.com/PatristicTextArchive/pta_metadata)
- [All dictionary data used in the frontend](https://github.com/PatristicTextArchive/pta_lexika)
- [Schema for editions](https://github.com/PatristicTextArchive/Schema)


## Linked Open Data

The [Metadata-Repository](https://github.com/PatristicTextArchive/pta_metadata) contains information to link to the resources in the [Patristic Text Archive (PTA)](https://pta.bbaw.de) at <https://github.com/PatristicTextArchive/pta_metadata/LOD>. 

Currently we provide this information as tables in csv-format, as [BEACON](https://gbv.github.io/beaconspec/beacon.html) and as [RDF](https://www.w3.org/RDF/) files (turtle, rdf/xml, JSON-LD).

### Authors of texts in the PTA
using [Gemeinsame Normdatei](http://d-nb.info/gnd/) and [Wikidata](https://www.wikidata.org/)

- [pta_authors.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors.csv) (columns: GND-ID,Wikidata-Entity,URN)
- [pta_authors_gnd_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_gnd_beacon.txt), [pta_authors_gnd.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_gnd.xml), [pta_authors_gnd.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_gnd.ttl), [pta_authors_gnd.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_gnd.json-ld) (all authors in PTA identified by a GND-ID)
- [pta_authors_wikidata_beacon.txt](pta_authors_wikidata_beacon.txt), [pta_authors_wikidata.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_wikidata.xml), [pta_authors_wikidata.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_wikidata.ttl), [pta_authors_wikidata.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_authors_wikidata.json-ld) (all authors in PTA identified by a Wikidata-ID)

### Works in the PTA
using [Clavis Clavium](https://clavis.brepols.net/clacla) and [Pinakes](https://pinakes.irht.cnrs.fr)

- [pta_works.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works.csv) (columns: CPG no.,BHG no.,Pinakes-Oeuvre no.,URN)
- [pta_works_cpg_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_cpg_beacon.txt), [pta_works_cpg.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_cpg.xml), [pta_works_cpg.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_cpg.ttl), [pta_works_cpg.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_cpg.json-ld) (all works in PTA identified by a Clavis Patrum Graecorum number)
- [pta_works_bhg_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_bhg_beacon.txt), [pta_works_bhg.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_bhg.xml), [pta_works_bhg.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_bhg.ttl), [pta_works_bhg.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_bhg.json-ld) (all works in PTA identified by a Bibliographia Hagriographica Graeca number)
- [pta_works_pinakes-oeuvre_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_pinakes-oeuvre_beacon.txt), [pta_works_pinakes-oeuvre.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_pinakes-oeuvre.xml), [pta_works_pinakes-oeuvre.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_pinakes-oeuvre.ttl), [pta_works_pinakes-oeuvre.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_works_pinakes-oeuvre.json-ld) (all works in PTA identified by a Pinakes Oeuvre number)

### Manuscript descriptions in the PTA
using [Pinakes](https://pinakes.irht.cnrs.fr)

- [pta_manuscripts_diktyon.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_manuscripts_diktyon.csv) (columns: Diktyon-ID,URN)
- [pta_manuscripts_diktyon_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_manuscripts_diktyon_beacon.txt), [pta_manuscripts_diktyon.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_manuscripts_diktyon.xml), [pta_manuscripts_diktyon.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_manuscripts_diktyon.ttl), [pta_manuscripts_diktyon.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_manuscripts_diktyon.json-ld) (all manuscript descriptions identified by a Diktyon-ID)

### Biblical references in the texts of the PTA
Biblical books are abbreviated as follows: 
- Gn, Ex, Lv, Num, Dt, Jos, Judg, Rt, 1Sa, 2Sa, 1Ko, 2Ko, 1Chr, 2Chr, 3Esr, Esr, Est, Jdt, Tob, 1Mak, 2Mak, 3Mak, 4Mak, Ps, Oden, Prov, Eccl, Song, Job, Wis, Sir, PsSal, Hos, Am, Mi, Joel, Ob, Jon, Nah, Hab, Zeph, Hag, Sach, Mal, Is, Jr, Bar, Lam, EpistJer, Hes, Sus, Dn, Bel
- Mt, Mk, Lk, Jn, Act, Rom, 1Cor, 2Cor, Gal, Eph, Phil, Col, 1Th, 2Th, 1Tim, 2Tim, Tt, Phm, Heb, Jak, 1P, 2P, 1Jn, 2Jn, 3Jn, Jud, Rev

#### linking to the texts
- [pta_biblereferences.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_biblereferences.csv) (columns: Quotation-URL,Reference)

#### linking to the index
- [pta_biblereferences_index.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_biblereferences_index.csv) (columns: Reference,Reference in Index)

### Persons mentioned in texts in the PTA
using [Gemeinsame Normdatei](http://d-nb.info/gnd/) and [Wikidata](https://www.wikidata.org/)

#### linking to the texts
- [pta_persons.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons.csv)(columns: GND-ID,Wikidata-Entity,mentioned in)

#### linking to the index
- [pta_persons_index.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index.csv) (columns: GND-ID,Wikidata-Entity,Person in index)
- [pta_persons_gnd_index_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_gnd_index_beacon.txt), [pta_persons_index_gnd.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index_gnd.xml), [pta_persons_index_gnd.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index_gnd.ttl), [pta_persons_index_gnd.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index_gnd.json-ld) (all entries in the persons index identified by a GND-ID)
- [pta_persons_wikidata_index_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_wikidata_index_beacon.txt), [pta_persons_index_wikidata.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index_wikidata.xml), [pta_persons_index_wikidata.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index_wikidata.ttl), [pta_persons_index_wikidata.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_persons_index_wikidata.json-ld) (all entries in the person index identified by a Wikidata-ID)

### Organisations and groups mentioned in texts in the PTA
using [Gemeinsame Normdatei](http://d-nb.info/gnd/) and [Wikidata](https://www.wikidata.org/)

#### linking to the texts
- [pta_orgs.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs.csv)(columns: GND-ID,Wikidata-Entity,mentioned in)

#### linking to the index
- [pta_orgs_index.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index.csv) (columns: GND-ID,Wikidata-Entity,Person in index)
- [pta_orgs_gnd_index_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_gnd_index_beacon.txt), [pta_orgs_index_gnd.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index_gnd.xml), [pta_orgs_index_gnd.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index_gnd.ttl), [pta_orgs_index_gnd.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index_gnd.json-ld) (all entries in the persons index identified by a GND-ID)
- [pta_orgs_wikidata_index_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_wikidata_index_beacon.txt), [pta_orgs_index_wikidata.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index_wikidata.xml), [pta_orgs_index_wikidata.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index_wikidata.ttl), [pta_orgs_index_wikidata.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_orgs_index_wikidata.json-ld) (all entries in the person index identified by a Wikidata-ID)

### Places mentioned in texts in the PTA
using [Pleiades Gazetteer](https://pleiades.stoa.org/)

#### linking to the texts
- [pta_places.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_places.csv) (columns: Place,mentioned in)

#### linking to the index
- [pta_places_index.csv](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_places_index.csv) (columns: Place,Place in index)
- [pta_places_index_beacon.txt](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_places_index_beacon.txt), [pta_places_index.xml](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_places_index.xml), [pta_places_index.ttl](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_places_index.ttl), [pta_places_index.json-ld](https://github.com/PatristicTextArchive/pta_metadata/blob/main/LOD/pta_places_index.json-ld) (all entries in the place index identified by a Pleiades Gazetteer ID)