Die Editionsrichtlinien für das PTA sind in einem [Schema](https://doi.org/10.5281/zenodo.3737666 ) festgehalten, das die umfassenden und häufig redundanten Regelungen des TEI TEI-konform eingrenzt und das auch die Grundlage der folgenden Regeln und Beispiele ist.
  
> Diese Editionsrichtlinien sind eine leicht gekürzte, aber auf Version 3.0 des Schemas hin aktualisierte Fassung von [Annette v. Stockhausen, Die Modellierung kritischer Editionen im digitalen Zeitalter, ZAC 24 (2020), 123–160](https://nbn-resolving.org/urn:nbn:de:kobv:b4-opus4-35237 ). Dieses Schema hat seinen Ursprung in den Epidoc Guidelines, hat diese aber erheblich erweitert und verändert. 
  
Durch die Wahl der Auszeichnungssprache TEI-XML für die Kodierung der digitalen kritischen Edition ist ein fundamentaler Unterschied zur klassischen kritischen Edition, wie wir sie aus unseren gedruckten Ausgaben kennen, markiert, nämlich die Unterscheidung zwischen der Kodierung der Edition im digitalen Format und ihrer Präsentation im Druck, im Internet, als E-Book, etc. Die Edition im eigentlichen Sinn sind die in TEI-XML kodierten Daten, von denen zu erwarten ist, dass sie langzeitverfügbar und rezipierbar bleiben, während es sich bei ihrer Präsentation im Druck oder auch im Internet um im Informationsgehalt reduzierte (oder auch angereicherte) Erscheinungsformen dieser Daten handelt, die zumal im Falle der Online-Präsentation dem fortwährenden Wandel der Technologie unterworfen sind.
  
Festzuhalten sind auf jeden Fall die Vorteile einer kritischen digitalen Edition, wie sie im Folgenden definiert und exemplifiziert wird:
  
1.  Die Erstellung von Volltext-Transkriptionen (anstelle der Aufzeichnung nur von Lesarten in einer Kollationstabelle) und die Publikation auch dieser Forschungsdaten als Teil der digitalen Edition erhöhen die Nachvollziehbarkeit der von der Editorin gefällten textkritischen Entscheidungen und ermöglichen überhaupt erst eine umfängliche Überprüfung, die weit über das in der Praefatio einer gedruckten Edition an Varianten Präsentierte hinausgeht, da es dort ja immer um die Konzentration von Information auf möglichst knappen Raum geht.
  
2.  Die der *constitutio textus* zugrunde liegenden Entscheidungen können durch textkritische Kommentare *in situ* erläutert werden. Auch dies erhöht die Transparenz der Edition.
  
3.  Durch die gleichzeitige Bereitstellung von Handschriftentranskription *und* kritischer Edition bleibt die Edition für unterschiedliche editionsphilologische Ansätze offen.
  
4.  Durch die strikte Trennung von Daten (mit dem Fokus auf Vollständigkeit) und Präsentation der Daten (in einer für das jeweilige Medium und den jeweiligen Zweck bzw. die jeweilige Fragestellung getroffenen Auswahl an präsentierten Phänomenen) können auf Basis eines Datensatzes ganz unterschiedliche Darstellungsweisen gewählt werden, die zusätzlich durch weitere Daten anderer Herkunft noch angereichert werden können.
  
## Aufbau einer digitalen Edition nach TEI
  
> In diesen Richtlinien werden folgende Schreibkonventionen verwendet: Mit `<element>` sind XML-Elemente gemeint, mit `@attribut` XML-Attribute und mit `Wert` die den Attributen zugeschriebenen Werte; `#` in einem Wert bedeutet, dass es sich um einen an anderer Stelle in der TEI-Datei, normalerweise dem `<teiHeader>`, definierten Identifikator handelt, auf den an dieser Stelle verwiesen wird.
  
TEI-Dateien sind grundsätzlich zweigeteilt: Sie enthalten einen Abschnitt [`<teiHeader>`](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-teiHeader.html ) mit allen Metadaten und einen Abschnitt [`<text>`](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-text.html ) mit der Edition.
  
Alle Dateien (Transkriptionen, Editionen oder Übersetzungen) enthalten im `<teiHeader>` die folgenden Metadaten:
  
```xml
  <teiHeader>
    <fileDesc>
      <titleStmt>
        <title xml:lang="la">Epistula synodalis (Ms Ps)</title>
        <author key="#pta0013" ref="https://lobid.org/gnd/118648888">Amphilochius Iconiensis</author>
        <respStmt>
          <resp>transkribiert von</resp>
          <persName xml:id="AvS" ref="https://lobid.org/gnd/124321291">Annette von Stockhausen</persName>
        </respStmt>
      </titleStmt>
      <publicationStmt>
        <authority>Berlin-Brandenburgische Akademie der Wissenschaften</authority>
        <distributor>Patristic Text Archive</distributor>
        <availability>
          <licence target="https://creativecommons.org/licenses/by-sa/4.0/">Available under a Creative Commons Attribution ShareAlike 4.0 International License</licence>
        </availability>
        <date>2019</date>
        <idno type="PTA">pta0013.pta003</idno>
        <idno type="CPG">3243; 8596</idno>
        <idno type="BHG"/>
        <idno type="Aldama"/>
        <idno type="Pinakes-Oeuvre">5717</idno>
      </publicationStmt>
      <sourceDesc>
       ...
      </sourceDesc>
    </fileDesc>
    <encodingDesc>
      <refsDecl n="CTS">
        <cRefPattern n="section" matchPattern="(.+)" replacementPattern="#xpath(/tei:TEI/tei:text/tei:body/tei:div[@type='edition']/tei:div[@n='$1'])"/>
      </refsDecl>
      <schemaRef key="v3" url="https://raw.githubusercontent.com/PatristicTextArchive/Schema/master/tei-pta.rng"/>
    </encodingDesc>
    <profileDesc>
      <creation>
          <date><!--Date of creation--></date>
          <placeName><!--Place or region of creation--></placeName>
      </creation>
      <textClass>
        <keywords scheme="#comphistsem">
           <term><!--Genre missing--></term>
        </keywords>
        <keywords scheme="#editionstatus">
           <term><!--Edition status missing--></term>
        </keywords>
     </textClass>
    </profileDesc>
    <revisionDesc>
      <change who="#AvS" when="2019-02-05">Transkription des Textes anhand des Mikrofilms im Besitz des CNRS</change>
    </revisionDesc>
  </teiHeader>
```  
  
  
Der Abschnitt `<fileDesc>` enthält die bibliographischen Angaben zur Datei, insbesondere Angaben 
- zum Titel (`<titleStmt>`)
- zur Veröffentlichung (`<publicationStmt>`). Anzupassen sind in diesem Abschnitt vor allem die IDs (`<idno>`) (u.a. CPG, CPL, BHG, Pinakes-Oeuvre), da dadurch die Austauschbarkeit und Verlinkung der Daten ernmöglicht wird. 
- zu den Quellen (`<sourceDesc>`). 
  
In diesem Abschnitt unterscheiden sich die Angaben in den drei Arten von Dateien (Transkription, kritische Edition, Übersetzung) signifikant. 
  
Der Abschnitt `<encodingDesc>` bietet alle Angaben, die die Kodierung der Datei betreffen, und enthält in jedem Fall ein Element `<refsDecl>`, das die Gliederungsstruktur der Datei entsprechend den [„CapiTainS Guidelines“](http://capitains.org/ ) ([s. unten](#dateien-struktur-jeder-edition )) definiert. Dieser Abschnitt endet mit dem Element `<schemaRef>`, das auf die verwendete Version des PTA-Schemas verweist.
  
Informationen zur Datierung (`<date>`) und Verortung (`placeName`) des Textes werden im Element `<creation>` und zur Gattung (unter Verwendung der Texttypenklassifikation von <https://www.comphistsem.org/46.html>) im Element `<textClass>` innerhalb des Abschnittes `<profileDesc>` geboten. 
  
Da es sich bei digitalen Editionen im Gegensatz zu gedruckten Editionen um potentiell sehr fluide Daten handeln kann, ist es von großer Bedeutsamkeit, dass im Abschnitt `<revisionDesc>` alle signifikanten Änderungen an der Datei und ihre Urheber festgehalten werden, und so die Versionsgeschichte der einzelnen Dateien auch losgelöst vom [Git-Repositorium des PTA](https://github.com/PatristicTextArchive/pta_data/ ) nachvollziehbar bleibt. 
  
## Transkription der Überlieferungsträger
  
Handschriften sind Zeugen eines spezifischen Überlieferungsstadiums eines Textes. Im Gegensatz zum klassischen „Lachmannschen“ Ansatz, bei dem in der Praxis nur die Varianten zu einem Vorlagentext notiert werden, ist es für digitale Editionen – durchaus auch unter Aufnahme des Grundgedankens der „New Philology” einer Wertschätzung jedes einzelnen Überlieferungsträgers – angebracht und zudem auch arbeitsökonomisch durchaus sinnvoll, jeweils den gesamten Text zu transkribieren und dann in einem zweiten Schritt die Kollation der Zeugen mit Hilfe des Computers durchzuführen. 
  
> Im Berliner Akademienvorhaben „Die alexandrinische und antiochenische Bibelexegese in der Spätantike“, dessen digitale Publikationsplattform das PTA ist, wird dafür das Programm [CollateX](https://collatex.net/ ) verwendet, wobei die Transkriptionsdateien mit Hilfe eines Python-Skripts (<https://github.com/PatristicTextArchive/collator>) in das für CollateX nötige Eingabeformat konvertiert werden. Kleinere Fehler bei der Ausrichtung der Kollationstabelle können dabei nachträglich manuell korrigiert werden.
  
Auch die Transkriptionen sind somit Editionen und das Ergebnis von Interpretation. Sie unterscheiden sich von der kritischen Edition (s.u.) aber dadurch, dass sie einem diplomatischen (dokumentarischen) Editionsparadigma folgen: Die in der Handschrift vorfindlichen Phänomene wie Schreibung der Worte, Akzentsetzung, Interpunktion und Worttrennung werden bei der Transkription grundsätzlich nicht normalisiert, d.h. nicht ggfs. korrigiert. Außerdem werden Seiten-, Columnen- und Zeilenumbrüche, Initialen und Ektheseis, Marginalien, Abkürzungen, Markierungen, Rubriken, Tilgungen, Hinzufügungen – auch in diachroner Betrachtung (sc. im Blick auf Schreiberwechsel) – aufgenommen, dabei aber nicht entsprechend ihrer visuellen Erscheinung, sondern entsprechend ihrer Semantik ausgezeichnet und das heißt einer Deutung unterzogen. Auch Phänomene, die nicht gedeutet werden können, wie z.B. nicht zu entziffernder Text, werden als solche markiert und damit auch Unsicherheiten nicht verdeckt.
  
Ggfs. können in den Metadaten der Transkriptionen (im Element `<editorialDecl>` im Abschnitt `<encodingDesc>`) nähere Angaben gemacht werden, inwieweit Phänomene aufgenommen werden oder nicht. 
  
### Metadaten der Transkription
  
Der Header der Transkriptionsdatei enthält zusätzlich zu den oben
genannten Metadaten innerhalb des Abschnittes `<sourceDesc>` im Element
`<msDesc>` kurze Angaben zur Handschrift, die mindestens das Element
`<msIdentifier>` umfassen. Das Element erhält eine eigene `@xml:id`, die z.B. für die Identifikation der Handschrift bei der Kollation ausgelesen wird. 
Lassen sich in einer Handschrift mehrere
Schreiber feststellen, so ist es außerdem sinnvoll, in einem weiteren
Abschnitt `<physDesc>`, der der Beschreibung der physischen
Beschaffenheit der Handschrift dient, diese Schreiber im Element
`<handNote>` innerhalb eines Unterabschnittes `<handDesc>` kurz zu
beschreiben. Das Attribut `@xml:id` wird dabei in der Edition als Identifikator referenziert und ist auf jeden Fall zu setzen; daneben stehen noch weitere Attribute zur Verfügung, z.B. kann das Attribut  `@scribe` verwendet werden, wenn der Schreiber namentlich bekannt ist.
  
Handelt es sich bei der Handschrift z.B. um eine
Randkatene, so kann das Layout im selben Abschnitt in der `<objectDesc>`
innerhalb des Elements `<layoutDesc>` beschrieben werden.
  
```xml
<sourceDesc>
<msDesc>
 <msIdentifier xml:id="Athen_253">
  <settlement>Athen</settlement>
  <repository>Ethnikê Bibliothêkê tês Hellados (EBE)</repository>
  <idno>253</idno>
  <altIdentifier type="diktyon">
   <idno>2549</idno>
  </altIdentifier>
 </msIdentifier>
 <physDesc>
    <objectDesc>
        <layoutDesc>
            <layout columns="3">
                <p>Der Text setzt sich aus kommentiertem Text, einer inneren und einer äußerem Kommentarspalte zusammen.</p>
            </layout>
        </layoutDesc>
    </objectDesc>
    <handDesc hands="3">
        <handNote xml:id="m1">Schreiber</handNote>
        <handNote xml:id="m2">Erster Korrektor</handNote>
        <handNote xml:id="mr">Manus recentior</handNote>
    </handDesc>
 </physDesc>
</msDesc>
</sourceDesc>
```  
  
### Edition der Transkription
  
Die gesamte Transkription steht im `<text>`-Teil der Datei in einem
Abschnitt `<div>`. Das Element hat die folgenden Attrribute: 
- `@type="edition"`
- `@xml:lang` mit der Angabe der Sprache des edierten Textes unter Verwendung von [ISO 639-2](https://www.loc.gov/standards/iso639-2/php/code_list.php ).
- `@n` mit der URN der Datei, s. [unten](#dateien-struktur-jeder-edition ).
  
#### Auszeichnung der Textstruktur
  
Innerhalb dieses Abschnittes ist zumindest ein Unterabschnitt `<div>`
vom `@type="textpart"` zu verwenden, wobei das Attribut `@subtype`
folgende Werte annehmen darf: `section` für Fließtexte, `fragment` für
fragmentarisch Überlieferungen, `commented` und `commentary` für
Kommentare oder vergleichbare Texte, bei denen zwischen einem
kommentierten und einem kommentierenden Text unterschieden wird.
  
Im Fall einer Katene kann das z.B. folgendermaßen aussehen:
  
```xml
<div type="edition" xml:lang="grc" n="urn:cts:pta:pta0013.pta003.pta-MsPs">
  <pb n="112v"/>
  <div type="textpart" subtype="commented" n="Gen:1:1–2">
   <seg xml:id="alpha">
    <g type="obelos"/> Εν ἀρχῇ ἐποίησεν ὁ θεὸς τὸν
       οὐρανὸν καὶ τὴν γῆν.</seg>
   <seg xml:id="beta">ἡ δὲ γῆ ἦν ἀόρατος καὶ ἀκατασκεύαστος, καὶ 
       σκότος ἐπάνω τῆς <w xml:id="a">ἀβύσσου</w>, καὶ 
       πνεῦμα θεοῦ ἐπεφέρετο ἐπάνω τοῦ ὕδατος.</seg>
   <div type="textpart" subtype="commentary" n="A" ana="marginal">
      <head>
       <title type="lemma">Εὐσεβίου·</title>
      </head>
      <p corresp="#alpha">
       <g type="obelos"/>Kommentar</p>
      <p corresp="#beta">Kommentar</p>
   </div>
   <div type="textpart" subtype="commentary" n="B" ana="hexaplaric">
      <seg corresp="#a">Worterklärung</seg>
   </div>
  </div>
</div>
```  
  
Der Text wird dabei durch das Element `<seg>` (ggfs. bei einzelnen Worten auch durch `<w>`) weiter unterteilt, dem jeweils auch eine @xml-id zugewiesen wird, um mit Hilfe des Attributes `@corresp` im referenzierenden Element (`<seg>` oder `<p>`) die Bezüge zwischen den korrespondieren Teilen (Text, Kommentar) auszeichnen zu können.
  
Zusätzlich kann bei Kommentaren (= `@subtype='commentary'`) das Attribut `@ana` verwendet werden, um Angaben zur Lokalisierung des entsprechenden Kommentarteils auf der Seite bzw. zu seiner  Kategorisierung zu machen. Mögliche Werte sind: `marginal`, `interlinear`, `intercolumn`, `scholia`, `hexaplaric`; andere Werte sind bei Bedarf erlaubt.
  
Bei der Transkription kann mit Hilfe des Elementes `<milestone>` auf Gliederungen des Textes (angegeben mit Hilfe der Attribute `@unit` und `@n`) durch Editionen (angegeben mit `@edRef`) verwiesen werden: 
  
```xml
<div type="textpart" subtype="section" n="1">
  <p>
  <milestone unit="section" edRef="#Whittaker" n="1"/>Text
  </p>
</div>
```  
  
Bei Editionen, die im PTA vorhanden sind, ist der Wert des Attributes `@edRef` die URN der Edition (also z.B. `urn:cts:pta:pta0001.pta028.pta-grcBibex`), ansonsten sollte auf die `@xml:id` einer im `<teiHeader>` bibliographierten Edition verwiesen werden.
  
Die Gliederung des Textes in der Transkription folgt aber in jedem Fall den Gliederungselementen der Handschrift und nicht denen moderner Editionen.
  
#### Zeichensetzung
  
Die Interpunktion wird – ohne explizite Auszeichnung – der Handschrift
entsprechend transkribiert.
  
#### Titel und titelähnliche Elemente
  
Titel werden mit dem Element `<title>` innerhalb des Elementes
`<head>` ausgezeichnet:
  
```xml
<head>
 <title>Τοῦ αὐτοῦ ὁμιλία</title>
</head>
```  
  
Überschriftsähnliche Elemente, wie z.B. die Zuschreibung eines Zitates zu einem am Rand angeführten oder im Text hervorgehobenen Autors, werden mit dem Element `<label>` ausgezeichnet, das ein Attribut `@type` mit dem Wert `attribution` erhält.
  
```xml
<p><label type="attribution">
    <persName key="PTA_P00001">Χρυσοστόμου</persName>.
</label> Προκαταλαμβάνει τὸν ἀκροατὴν τοῖς ἐπαίνοις· 
ὥστε μηδὲ ἄκοντα ἀποστῆναι. </p>
```  
  
#### Zeilen-, Spalten-, Seiten-, Bogenanfänge
  
Zeilenanfänge werden mit `<lb/>`, Spaltenanfänge mit `<cb/>`, 
Seitenanfänge mit `<pb/>` und Bogenanfänge mit `<gb/>` ausgezeichnet.
  
Befindet sich ein Umbruch innerhalb eines Wortes, erhält das jeweilige Element das Attribut `@break` mit dem Wert `no`. Am Ende des Wortteiles steht kein Leerzeichen.
  
Beim Seiten- (ggfs. auch beim Bogenanfang) erhält das Element das Attribut `@n` für die Eingabe der Seitennummerierung und – wo vorhanden – das Attribut `@facs` für die Eingabe der URL eines digitalen Faksimiles. 
  
```xml
<lb/>θησαυροὶ, ψυχὰς εὐφραίνοντες· 
<lb/>ἐννοίας φωτίζοντες· τὴν οἰ
<lb break="no"/>κουμένην ἐπιστρέφοντες πᾶσαν·
<pb n="227r" 
facs="https://digitalcollections.nlg.gr/iiif/3001/EBE0253455.tif/full/full/0/default.jpg"/>
<cb/> 
<lb/>τοῦ ἀδὰμ τὴν πτωχείαν πλουτί
<lb break="no"/>ζοντες· εἰς πολλὴν γὰρ κατηνέ
<lb break="no"/>χθη ταπείνωσιν, τὸ πρωτότυπον 
```  
  
Wo möglich sollte wie im Beispiel auf eine per [IIIF](https://iiif.io/ ) zur Verfügung gestellte URL des Bildes in voller Auflösung zurückgegriffen werden. Hier handelt es sich um Folio 227r des Codex Atheniensis 253, dessen Digitalisat von der EBE unter https://digitalcollections.nlg.gr/nlg-repo/dl/en/browse/3001 zur Verfügung gestellt wird; f. 227r ist image 455, dessen Vollbild-URL https://digitalcollections.nlg.gr/iiif/3001/EBE0253455.tif/full/full/0/default.jpg z.B. leicht mit Hilfe des Browser-Plugins [Dezoomify](https://dezoomify.ophir.dev/ ), das die IIIF-Image API Adresse https://digitalcollections.nlg.gr/iiif/3001/EBE0253455.tif/info.json ausgibt, herausgefunden werden kann. Die Bild URL erhalt man dann durch Ersetzen von `info.json` durch die Angabe von [{region}/{size}/{rotation}/{quality}.{format}](https://iiif.io/api/image/3.0/#4-image-requests ), im angegebenen Fall also `full/full/0/default.jpg`. Manche Bibliotheken wie die BNF z.B. stellen in ihren [IIIF-Viewern](https://gallica.bnf.fr/view3if/ ) die Bild-URL über die Export-Funktion auch selbst zur Verfügung.
  
Stellt die besitzende Bibliothek Digitalisate nur in einem eigenen Reader zur Verfügung (wie z.B. die BML Firenze oder die British Library London), so ist, soweit vorhanden, die entsprechende URL des Faksimiles einer Seite zu verlinken.
  
#### Absätze
  
Absätze werden – soweit sie in der Handschrift (z.B. durch eine Lücke) markiert sind – mit dem Element `<p>` ausgezeichnet. Jede Transkription besteht aus mindestens einem Absatz.
  
#### Listen
  
Listen (z.B. von Namen oder Inhaltsverzeichnisse) werden, wenn sie in der Handschrift als solche dargestellt sind, mit dem Element `<list>`, die einzelnen Listeneinträge mit dem Element `<item>` ausgezeichnet. Hat eine Liste eine hervorgehobene Überschrift, so wird diese mit Hilfe des Elementes `<head>` ausgezeichnet. 
  
#### Initialen und Ektheseis
  
Initialen und Ektheseis werden mit dem Element `<hi>` ausgezeichnet. Im Attribut `@rend` wird angegeben, ob es sich um eine (mehrere Zeilen übergreifende) Initiale (`initial`) oder um eine Ekthesis (`ekthesis`) handelt.
  
```xml
<hi rend="ekthesis">θ</hi>ησαυροὶ, ψυχὰς εὐφραίνοντες·
```  
  
#### Andere Hervorhebungen
  
*Rubrizierter* Text wird ebenfalls mit dem Element `<hi>` ausgezeichnet; das Attribut `@rend` erhält den Wert `rubricated`.
  
Mit einer *Linie über* dem Buchstaben oder Wort hervorgehobener Text wird mit `<hi rend="overline">` markiert.
  
*Unterstrichener* Text wird mit `<hi rend="underline">` markiert.
  
Durch Verwendung von *Großbuchstaben* hervorgehobener Text (z.B. Lemmata in Kommentaren) wird mit `<hi rend="majuscule">` markiert.
  
#### Marginalien
  
Marginalien werden in der Transkription als `<note>` ausgezeichnet, wobei das Element im Text möglichst nahe zu der Stelle eingeführt wird, an der sich die Marginalie befindet.
  
Die Position der Marginalie wird im Attribut `@place` angegeben. Erlaubte Werte sind `top` (ggfs. näher spezifiert: `top_inner`, `top_center`, `top_outer`), `bottom` (`bottom_inner`, `bottom_center`, `bottom_outer`), `margin_inner`, `margin_outer` und `intercolumn`.
  
Stammt eine Marginalie nicht vom Schreiber, kann dies durch das Attribut `@hand` angegeben werden, wobei die Korrektoren (`#m2`, `#m3`, … – allgemein `#mr` für *manus recentior*; zur Angabe der Hände in den Metadaten s. [oben](#metadaten-der-transkription )) unterschieden werden sollten. Ist nicht zu entscheiden, von welcher Hand eine Marginalie geschrieben worden ist, wird dem Attribut der Wert `unknown` zugewiesen.
  
```xml
<note place="margin_outer">ΓΡ ἐδέχθησαν:-</note>
<note place="margin_outer" hand="#m2">οὕτω διὰ τῆς σωτῆρος
υἱοῦ τοῦ θεοῦ καὶ λόγου <lb/> συγκαταβάσεως ἐπλουτίσθη</note>
<note hand="#m3" place="margin_outer">ὡρ<expan>αῖον</expan></note>
  
<note place="top_inner" hand="#mr">λόγος <num>ΚΔ'</num><lb/>
περὶ φύσεως νόμου</note>
<title>Τοῦ αὐτοῦ ὁμιλία εἰς τὸν περι φύσεως νόμον</title>
<note place="margin_outer"><num>ΚΓ</num></note>
```  
  
#### Getilgter Text
  
Vom Schreiber oder einem späteren Korrektor getilgter Text wird mit `<del>` ausgezeichnet. Die Art der Tilgung wird im Attribut `@rend` angegeben. Erlaubte Werte sind `erasure` (ausradiert), `strikethrough` (durchgestrichen), `overwrite` (durch Überschreiben) und `expunction` (durch Auspunktieren).
  
Stammt eine Tilgung nicht vom Schreiber, kann dies durch das Attribut `@hand` angegeben werden, wobei die Korrektoren (`#m2`, `#m3`, … – allgemein `#mr` für *manus recentior*; zur Angabe der Hände in den Metadaten s. [oben](#metadaten-der-transkription )) unterschieden werden sollten. Ist nicht zu entscheiden, von welcher Hand eine Korrektur vorgenommen worden ist, wird dem Attribut der Wert `unknown` zugewiesen.
  
```xml
γηΐ<del rend="erasure" hand="#m2">ω</del>νων
```  
  
#### Korrekturen
  
Korrekturen (von Worten, aber auch einzelnen Buchstaben) werden mit dem Element `<subst>` gekennzeichnet.
  
Stammt eine Korrektur nicht vom Schreiber, kann dies durch das Attribut `@hand` angegeben werden, wobei die Korrektoren (`#m2`, `#m3`, … – allgemein `#mr` für *manus recentior*, zur Angabe der Hände in den Metadaten s. [oben](#metadaten-der-transkription )) unterschieden werden sollten. Ist nicht zu entscheiden, von welcher Hand eine Korrektur vorgenommen worden ist, wird dem Attribut der Wert `unknown` zugewiesen.
  
Innerhalb dieses Elementes wird der *getilgte Text* mit `<del>`
ausgezeichnet. Die Art der Tilgung wird im Attribut `@rend` angegeben.
Erlaubte Werte sind `unmarked` (der zu ersetzende Text ist überhaupt nicht explizit markiert), `marker` (der zu ersetzende Text ist mit einem Zeichen, z.B. einem Obelus o.ä., markiert), `erasure` (ausradiert), `strikethrough` (durchgestrichen), `overwrite` (durch Überschreiben) und `expunction` (durch Auspunktieren).
  
Der *hinzugefügte Text* wird mit `<add>` ausgezeichnet. Der Ort der Hinzufügung wird mit Hilfe des Attributes `@place` angegeben. Erlaubte Werte sind `above` (darüber), `below` (darunter), `inline` (in der Zeile) und `margin` (am Rand).
  
```xml
<subst hand="#m2">
 <del rend="erasure">ἀναλόγως</del>
 <add place="above">παραλόγως</add>
</subst>
```  
  
Handelt es sich bei der Korrektur um die Hinzufügung von Diakritika zu Buchstaben, so wird der Buchstabe vor der Hinzufügung mit `<del>` und dem Attribut `@rend` mit dem Wert `repurposed` ausgezeichnet, nach der Hinzufügung mit `<add>` und dem Attribut `@rend` mit dem Wert `inline`.
  
```xml
<subst>
    <del rend="repurposed">α</del>
    <add rend="inline">ά</add>
</subst>
```  
  
Handelt es sich bei der Korrektur um ein Überschreiben bzw. Nachzeichnen des ursprünglichen Textes ohne Korrektur (Änderung des Textes), so ist besser das Element `<retrace>` zu verwenden:
  
```xml
ἴσως ἂν ἐνομίσθη <retrace>παρέλκον. ἀνάγραπτον</retrace> τούτων ποιεῖσθαι
```  
  
#### Hinzugefügter Text
  
Hinzugefügter Text, der nicht mit einer Korrektur einhergeht, wird mit dem Element `<add>` ausgezeichnet. Der Ort der Hinzufügung wird im Attribut `@place` angegeben. Erlaubte Werte sind `above` (darüber), `below` (darunter), `inline` (in der Zeile) und `margin` (am Rand).
  
Stammt eine Korrektur nicht vom Schreiber, kann dies durch das Attribut `@hand` angegeben werden, wobei die Korrektoren (`#m2`, `#m3`, … – allgemein `#mr` für *manus recentior*; zur Angabe der Hände in den Metadaten s. [oben](#metadaten-der-transkription )) unterschieden werden sollten. Ist nicht zu entscheiden, von welcher Hand eine Korrektur vorgenommen worden ist, wird dem Attribut der Wert `unknown` zugewiesen.
  
```xml
<add place="above" hand="#m2">hinzugefügter Text</add>
```  
  
#### Nicht lesbarer Text
  
Nicht lesbarer Text wird mit dem selbstschließenden Element `<gap>` angegeben (für andere Anwendungsfälle dieses Elementes vgl. [den nächsten Eintrag](#lücke-im-text )). Dem Attribut `@reason` wird der Wert `illegible` (nicht lesbar) zugewiesen. Der (geschätzte) Umfang (`@quantity`) wird in Buchstaben (`@unit="character"`), ggfs. Zeilen (`@unit="line"`) angegeben.
  
```xml
<gap reason="illegible" quantity="10" unit="character"/>
```  
  
#### Lücke im Text
  
Eine Lücke im Text wird ebenfalls mit dem Element `<gap>` angebeben. Dem Attribut `@reason` wird in diesem Fall der Wert `damage` (physische Beschädigung) oder `fenestra` (vom Schreiber freigelassen) zugewiesen. Der (geschätzte) Umfang (`@quantity`) wird in Buchstaben, Zeilen oder Seiten (`@unit` mit Wert `character`, `word`, `line` oder `page`) angegeben.
  
```xml
<gap reason="fenestra" quantity="10" unit="character"/>
```  
  
Ist eine Lücke jedoch durch die Zerstörung von Text durch den Schreiber (sc. Rasur: `@rend="erasure"`) entstanden, so wird diese mit dem Element `<del>` ausgezeichnet; ggfs. ist im Falle der Zerstörung durch eine andere Hand das Attribut `@hand` anzugeben, wobei die Korrektoren (`#m2`, `#m3`, … – allgemein `#mr` für *manus recentior*; zur Angabe der Hände in den Metadaten s. [oben](#metadaten-der-transkription )) unterschieden werden sollten. Ist nicht zu entscheiden, von welcher Hand eine Korrektur vorgenommen worden ist, wird dem Attribut der Wert `unknown` zugewiesen.
  
```xml
<del rend="erasure" hand="#m2">
 <gap reason="illegible" quantity="10" unit="character"/>
</del>
```  
  
#### Unsichere Lesung
  
Ist ein Text nicht sicher zu entziffern, wird er mit dem Element
`<unclear>` markiert. Das Attribut `@reason` gibt den Grund für die unsichere Lesung durch die Werte `damage` (physische Beschädigung), `illegible` (nicht lesbar) oder `retraced` (Text nachgezeichnet) an. Wie sicher die Lesung ist, wird mit Hilfe des Attributs `@cert` angegeben, das die Werte `low` und `high` annehmen kann.
  
```xml
<unclear reason="illegible" cert="high">ἄνθρωπον</unclear>
```  
  
#### Wechsel des Schreibers
  
Wechselt der Schreiber im Text, so wird an der Position des Wechsels das Element `<handShift/>` eingefügt. Die Schrift kann mit Hilfe der Attribute `@medium` (Charakteristik der Tinte oder des Schreibmaterials), `@scribeRef` oder `@scriptRef`, wobei bei den letzteren Attributen auf die entsprechenden `@xml:id` im `<teiHeader>` (`<handDesc>`, s. [oben](#metadaten-der-transkription )) zu verweisen ist.
  
```xml
<pb n="228r"/>
<handShift scribeRef="#m2"/>ὃς φησὶ πρὸς αὐτόν· κορ<lb break="no"/>νήλιε·
```  
  
#### Nomina sacra
  
Nomina sacra *können* ausgezeichnet werden. Dafür wird innerhalb eines `<choice>`-Elementes das Kürzel mit `<abbr>` mit dem Attribut `@type` vom Wert `nomSac` aufgenommen und die aufgelöste Form im Element `<expan>` notiert.
  
```xml
<choice>
    <expan>πνεύματι</expan>
    <abbr type="nomSac">
       <hi rend="overline">πνι</hi>
    </abbr>
</choice>
```  
  
#### Andere Abkürzungen
  
 Andere Abkürzungen werden analog zu den Nomina sacra notiert. Dafür wird innerhalb eines `<choice>`-Elementes das Kürzel mit `<abbr>` mit dem Attribut `@type` vom Wert `suspension` aufgenommen und die aufgelöste Form im Element `<expan>` notiert.
  
> Andere Abkürzungen werden an der BBAW aus Gründen des dafür anzusetzenden Zeitaufwandes nur in Ausnahmefällen kodiert.
  
```xml
<choice>
    <expan>εὐλόγησον</expan>
    <abbr type="suspension">
        <hi rend="overline">εὐ
            <hi rend="superscript">ο</hi>
        </hi>
    </abbr>
</choice>
```  
  
#### Zahlen
  
Zahlen werden mit dem Element `<num>` ausgezeichnet.
  
```xml
<num>ΛΓ</num>
```  
  
#### Diple und Paragraphos
  
Zitate werden in Handschriften oft mit einer Diple (einfach oder
doppelt) am Rand markiert. Sie werden in der Transkription mit Hilfe von `<g type="diple"/>` bzw. `<g type="doubled_diple"/>` vermerkt. (Das Element `<quote>` findet in der Transkription *keine* Verwendung!)
  
```xml
<lb/><g type="diple"/>προσέχετε φησὶ λαός μου τῶι νόμωι μου· κλίνατε τὸ οὖς ὑμῶν εἰς τὰ ῥήματα
<lb/><g type="diple"/>τοῦ στόματός μου· ἀνοίξω ἐν παραβολαῖς τὸ στόμα μου φθέγξομαι προβλήματα
<lb/><g type="diple"/>ἀπ αρχῆς· εἶτα διδάσκων πόθεν ταῦτα μεμάθηκεν· ὅσα ἠκούσαμεν φησὶ καὶ
```  
  
In der Handschrift mit einem Paragraphos am Rand markierte Zeilen werden mit Hilfe von `<g type="paragraphos"/>` vermerkt.
  
## Kritische Edition
  
### Metadaten der kritischen Edition
  
#### Handschriftliche Zeugen und frühere Editionen
  
Der Header der Editionsdatei enthält zusätzlich zu den [oben genannten Metadaten](#aufbau-einer-digitalen-edition-nach-tei ) innerhalb des Abschnittes `<sourceDesc>` in einem Unterabschnitt `<listWit>` eine Auflistung der verwendeten Handschriften. Die Informationen zu den einzelnen Handschriften werden mit Hilfe des Elementes `<witness>` zur Verfügung gestellt. Dabei sollte die Transkription der Handschrift (in Form ihrer URN, s. [unten](#dateien-struktur-jeder-edition )) im Attribut `@corresp` verlinkt werden.
  
Alle Einträge erhalten eine maschinenlesbare ID im Attribut `@xml-id`, der im `<witness>` untergeordneten Element `<abbr type="siglum">` eine menschlesbare Sigle, die auch weitere Formatierungen (wie z.B. hochgestellte Ziffern) enthalten kann, korrespondiert.
  
Handelt es sich bei der Handschrift um die Abschrift einer anderen Handschrift, so wird auf die `xml:id` dieser Handschrift im Attribut `@source` verlinkt. Dadurch ist es möglich, eine so markierte Handschrift (und alle von ihr bezeugten Textvarianten) z.B. für die Präsentation, aber auf für die Analyse durch ein Transformationsskript zu eliminieren.
  
Der übliche lateinische Name der Handschrift wird im Element `<name>` angegeben, die Datierung der Handschrift im Element `<origDate>` (ggfs. zusätzlich maschinenlesbar mit Hilfe der Attribute `@notBefore` und `@notAfter` bzw. `@when`), und die Folia bzw. Seiten, auf denen sich der edierte Text befindet, werden im Element `<locus>` (ggfs. maschinenlesbar mit Hilfe der Attribute `@from` and `@to`) angegeben.
  
Ist eine ausführlichere Beschreibung der Handschrift nötig oder
erwünscht, weil z.B. eine Werkausgabe eines Autors erarbeitet wird und Handschriften aus diesem Grund für mehrere Texte relevant sind, so ist es sinnvoll, diese in eine eigene Datei und unter möglichst vollständiger Ausschöpfung der in den [TEI-Richtlinien im Kapitel „Manuscript Description“](https://tei-c.org/release/doc/tei-p5-doc/en/html/MS.html ) beschriebenen Elemente auszulagern und auf diese dann im Attribut `@key` des Elements `<name>` zu verweisen. 
  
> Für die an der BBAW erstellten Editionen werden solche (auf den Inhalt fokussierte) Handschriftenbeschreibungen standardmäßig angelegt, die unter eindeutigen Handschriften-IDs auf <https://pta.bbaw.de/manuscripts/> angeführt werden; diese IDs werden als Wert von `@key` verwendet.
  
Handschriftenfamilien und Hyparchetypen können innerhalb des Abschnittes `@listWit` in einem eigenen Unterabschnitt `<listWit>` mit eigenem Element `<head>` zusammengefaßt werden, der im Attribut `@xml:id` eine eigene maschienenlesbare ID für die Familie bekommt (und analog im Element `<abbr type="siglum">` eine menschenlesbare Sigle). Diese können auch im Attribut `@wit` einer Lesart verwendet werden; um falsche Angaben zu vermeiden, wird aber angeraten, jeweils alle einzelnen Handschriften anzuführen (und die Anzeige von Gruppensiglen bei der Weiterverarbeitung für den Druck oder die Webpräsentation zu berücksichtigen).
  
Auch die indirekte Überlieferung oder alte wie moderne Übersetzungen sollten auf diese Art vermerkt werden, wenn auf sie in den Apparat-Einträgen der Edition verwiesen werden soll.
  
```xml
<listWit>
 <listWit xml:id="a">
  <head>Hyparchetyp <abbr type="siglum">α</abbr>
  </head>
  <witness xml:id="La" corresp="pta0013.pta003.pta-MsLa.xml">
    <abbr type="siglum">La</abbr>
    <name key="PTAMS00566">Laurentianus Plut. IV 12</name>
    <origDate notBefore="1401" notAfter="1500">s. XV</origDate>
    <locus>f. 131v–133v</locus>
  </witness>
  <witness xml:id="Vi" source="#La" corresp="pta0013.pta003.pta-MsVi.xml">
    <abbr type="siglum">Vi</abbr>
    <name key="PTAMS00569">Vindobonensis theol. gr. 190</name>
    <origDate notBefore="1451" notAfter="1500">s. XV (2. H.)</origDate>
    <locus>f. 113r–115r</locus>
  </witness>
 </listWit>
 <listWit xml:id="b">
  <head>Hyparchetyp <abbr type="siglum">β</abbr>
  </head>
  <witness>...</witness>
 </listWit>
</listWit>
```  
  
Entsprechend der Auflistung der Handschriften in einem Unterabschnitt `<listWit>` innerhalb des Abschnittes `<sourceDesc>` werden frühere Editionen in einem Unterabschnitt `<listBibl>` jeweils im Element `<bibl>` (oder `<biblStruct>`) angeführt:
  
```xml
<listBibl>
 <bibl xml:id="Sav" facs="http://mdz-nbn-resolving.de/urn:nbn:de:bvb:12-bsb10870413-4">
     <abbr type="siglum">Sav.</abbr>
     <editor>Henry Savile</editor>
     <title>Chrysostomi Opera tom. V</title>
     <pubPlace>Eton</pubPlace>
     <publisher>Ioannes Norton</publisher>
     <date when="1612">1612</date>
 </bibl>
</listBibl>
```  
  
Konjektoren, die nicht im obigen Sinne bibliographiert werden können, weil z.B. die Konjekturen mündlich übermittelt wurden oder sie in einer anderen Edition zitiert werden, werden folgendermaßen aufgenommen:
  
```xml
<listPerson>
<person xml:id="AvS">
 <persName ref="http://d-nb.info/gnd/124321291">
  <abbr type="siglum">AvS</abbr>
  <forename>Annette</forename>
  <surname>von Stockhausen</surname>
 </persName>
 <!-- ggfs. angeben -->
 <note>Zitiert in <ref target="#Sav">Savile</ref>.</note>
</person>
</listPerson>
```  
  
Die Person sollte durch Angabe eines Normdatenlinks ([GND](https://explore.gnd.network/ ), [ORCID](https://orcid.org/ ), [LCCN](https://lccn.loc.gov/ ), o.ä.) im Attribut `@ref` des `<persName>`-Elementes eindeutig identifiziert werden.
  
#### Kodierung von Bibelstellenangaben
  
Im Abschnitt `<encodingDesc>` wird in einem weiteren Element
`<refsDecl>` mit dem Attribut `@xml:id` vom Wert `biblical` maschinen- und menschenlesbar angegeben, nach welchem System Bibelstellen referenziert werden und wie diese Referenzen aufgelöst werden können.
  
```xml
<refsDecl xml:id="biblical">
  <cRefPattern matchPattern="(.+):(.+):([0-9]+):([0-9]+)[\-\.]*[0-9]*"
               replacementPattern="https://www.bibelwissenschaft.de/bibelstelle/$2$3,$4/$1">
     <p>For references to the Septuagint LXX is used as abbreviation, 
      for references to the New Testament NA is used as abbreviation 
      for the version.</p>
     <p>Noted are references to a biblical book, chapter, verse, sc. LXX:Gn:1:1; 
      also possible: LXX:Gn:1:1-3 for a sequence of verses or LXX:Gn:1:1.3 
      for two verses not following each other.</p>
     <p>The following abbreviations are used: Gn, Ex, Lv, Num, Dt, Jos, Judg, 
      Rt, 1Sa, 2Sa, 1Ko, 2Ko, 1Chr, 2Chr, 3Esr, Esr, Est, Jdt, Tob, 1Mak, 2Mak, 
      3Mak, 4Mak, Ps, Oden, Prov, Eccl, Song, Job, Wis, Sir, PsSal, Hos, Am, Mi, 
      Joel, Ob, Jon, Nah, Hab, Zeph, Hag, Sach, Mal, Is, Jr, Bar, Lam, EpistJer, 
      Hes, Sus (Sus-LXX), Dn (Dn-LXX), Bel (Bel-LXX); Mt, Mk, Lk, Jn, Act, Rom, 
      1Cor, 2Cor, Gal, Eph, Phil, Col, 1Th, 2Th, 1Tim, 2Tim, Tt, Phm, Heb, Jak, 
      1P, 2P, 1Jn, 2Jn, 3Jn, Jud, Rev.</p>
  </cRefPattern>
  <cRefPattern matchPattern="(.+):(.+):([0-9]+)[\-\.]*[0-9]*"
               replacementPattern="https://www.bibelwissenschaft.de/bibelstelle/$2$3/$1">
     <p>Noted are references to a biblical book and chapter, sc. LXX:Gn:1; also 
      possible: LXX:Gn:1-3 for a sequence of chapters or LXX:Gn:1.3 for two chapters 
      not following each other.</p>
  </cRefPattern>
  <cRefPattern matchPattern="(.+):(.+)"
               replacementPattern="https://www.bibelwissenschaft.de/bibelstelle/$2/$1">
     <p>Noted are references to a biblical book, sc. LXX:Gn.</p>
  </cRefPattern>
</refsDecl>
```  
  
Die im PTA verwendeten Abkürzungen für die Bücher des Alten Testamentes sind:
  
```txt
Gn, Ex, Lv, Num, Dt, Jos, Judg, Rt, 1Sa,
2Sa, 1Ko, 2Ko, 1Chr, 2Chr, 3Esr, Esr,
Est, Jdt, Tob, 1Mak, 2Mak, 3Mak, 4Mak,
Ps, Oden, Prov, Eccl, Song, Job, Wis,
Sir, PsSal, Hos, Am, Mi, Joel, Ob, Jon,
Nah, Hab, Zeph, Hag, Sach, Mal, Is, Jr,
Bar, Lam, EpistJer, Hes, Sus (Sus-LXX), 
Dn (Dn-LXX), Bel (Bel-LXX).
  
```  
  
Bei der Septuaginta (LLX) wird bei Sus, Dn, Bel zwischen der Septuaginta-Version (mit »-LXX«) und der Theodotion-Version unterschieden.
  
Die im PTA verwendeten Abkürzungen für die Bücher des Neuen Testamentes sind:
  
```txt
Mt, Mk, Lk, Jn, Act, Rom, 1Cor, 2Cor,
Gal, Eph, Phil, Col, 1Th, 2Th, 1Tim,
2Tim, Tt, Phm, Heb, Jak, 1P, 2P, 1Jn,
2Jn, 3Jn, Jud, Rev.
```  
  
Die Stellenangaben werden folgendermaßen gebildet:
Bibl. Korpus (LXX, PES [= Peshitta], Hexapla, Vg [= Vulgata] oder NA [= Neues Testament = Nestle-Aland]):Buch:Kapitel:Vers (z.B.: 1,1-2,1.4), z.B. `LXX:Gn:1:1-3`.
  
#### Angabe der ausgezeichneten Phänomene
  
Ebenfalls noch im Abschnitt `<encodingDesc>` wird anschließend im
Abschnitt `<editorialDecl>` innerhalb des Unterabschnittes
`<interpretation>` ausgeführt, welche Phänomene im Text ausgezeichnet
wurden und in welchem Ausmaß. Dadurch können Nutzer der Edition schnell erkennen, was sie von der Edition zu erwarten haben. Anpassungen des Wertes von `@ana` und des Textes sind vorzunehmen.
  
```xml
<editorialDecl>
  <interpretation>
    <p>This file is encoded according to the guidelines of the Patristic Text Archive (PTA). See https://pta.bbaw.de/project/encoding-guidelines and https://doi.org/10.5281/zenodo.3737666.</p>
    <p xml:id="biblical-quotations"
       ana="fully/partially/not-annotated fully/partially/not-identified">Biblical quotations are fully/partially annotated and/but not fully/partially referenced. References follow the scheme declared <ref target="#biblical">above</ref>. 
             </p>
    <p xml:id="other-quotations"
      ana="not-annotated not-identified">Other quotations are not annotated and not referenced. References follow the scheme declared as <ref target="#pta">pta</ref> or as <ref target="#perseus">perseus</ref> above.</p>
    <p xml:id="places"
       ana="fully/partially/not-annotated fully/partially/not-identified">Places are fully/partially annotated and/but not fully/partially referenced with <ref target="https://pleiades.stoa.org/">Pleiades Gazetteer</ref> IDs.</p>
    <p xml:id="persons"
       ana="fully/partially/not-annotated fully/partially/not-identified">Persons are fully/partially annotated and/but not fully/partially referenced with IDs according to the <ref target="https://github.com/PatristicTextArchive/tipnr_data">TIPNR - Tyndale Individualised Proper Names with all References</ref> list for biblical persons and IDs of <ref target="https://github.com/PatristicTextArchive/pta_metadata/blob/main/pta_persons.json">PTA persons index</ref> for all other persons.</p>
    <p xml:id="groups"
       ana="fully/partially/not-annotated fully/partially/not-identified">Groups of persons and organisations are fully/partially annotated and/but not fully/partially referenced with IDs according to the IDs of <ref target="https://github.com/PatristicTextArchive/pta_metadata/blob/main/pta_groups.json">PTA groups index</ref> for all other groups.</p>
    <p xml:id="text-analysis" 
       ana="automatically/manually/not-tagged automatically/manually/not-analyzed">Words are automatically/manually/not tagged and automatically/manually/not analyzed.</p>
 </interpretation>
  ...
</editorialDecl>
```  
  
Alle verwendeten Kategorien werden innerhalb des `<classDecl>`-Elements in einem `<taxonomy>`-Element mit `@xml:id="annotationstatus"` und `@xml:id="analysisstatus"` definiert. 
  
```xml
<classDecl>
    ...
    <taxonomy xml:id="annotationstatus">
       <bibl>Patristic Text Archive Status of annotation</bibl>
       <category xml:id="fully-annotated">
          <catDesc>All instances of a phenomenon (e.g. biblical quotations, persons, places) are encoded with the respective element.</catDesc>
       </category>
       <category xml:id="partially-annotated">
          <catDesc>Some instances of a phenomenon (e.g. biblical quotations, persons, places) are encoded with the respective element.</catDesc>
       </category>
       <category xml:id="fully-identified">
          <catDesc>All encoded instances of a phenomenon (e.g. biblical quotations, persons, places) are identified with the respective norm data.</catDesc>
       </category>
       <category xml:id="partially-identified">
          <catDesc>Some encoded instances of a phenomenon (e.g. biblical quotations, persons, places) are identified with the respective norm data.</catDesc>
       </category>
       <category xml:id="not-identified">
          <catDesc>No encoded instances of a phenomenon (e.g. biblical quotations, persons, places) are identified with the respective norm data.</catDesc>
       </category>
    </taxonomy>
    <taxonomy xml:id="analysisstatus">
       <bibl>Patristic Text Archive Status of linguistic analysis</bibl>
       <category xml:id="automatically-tagged">
          <catDesc>Words are automatically tagged.</catDesc>
       </category>
       <category xml:id="manually-tagged">
          <catDesc>Words are manually tagged.</catDesc>
       </category>
       <category xml:id="not-tagged">
          <catDesc>Words are not tagged.</catDesc>
       </category>
       <category xml:id="automatically-analyzed">
          <catDesc>Words are automatically analyzed.</catDesc>
       </category>
       <category xml:id="manually-analyzed">
          <catDesc>Words are manually analyzed.</catDesc>
       </category>
       <category xml:id="not-analyzed">
          <catDesc>Words are not analyzed.</catDesc>
       </category>
    </taxonomy>
 </classDecl>
```  
  
Der Status der Annotationen ist folgendermaßen definiert:
  
- `fully-annotated`: Alle Fälle eines Phänomens (z.B. Bibelzitate, Personen, Orte) werden mit dem entsprechenden Element markiert.
- `partially-annotated`: Einige Fälle eines Phänomens (z.B. biblische Zitate, Personen, Orte) werden mit dem entsprechenden Element markiert.
- `not-annotated`: Kein Fall eines Phänomens (z.B. biblische Zitate, Personen, Orte) ist mit dem entsprechenden Element markiert.
  
Der Umfang der Identifikation mit Normdaten ist folgendermaßen definiert:
  
- `fully-identified`: Alle markierten Fälle eines Phänomens (z.B. biblische Zitate, Personen, Orte) werden mit den entsprechenden Normdaten identifiziert.
- `partially-identified`: Einige markierte Fälle eines Phänomens (z.B. biblische Zitate, Personen, Orte) werden mit den entsprechenden Normdaten identifiziert.
- `not-identified`: Keine markierten Fälle eines Phänomens (z.B. Bibelzitate, Personen, Orte) werden mit den entsprechenden Normdaten identifiziert.
  
Der Status der sprachlichen Analyse ist folgendermaßen definiert:
  
- `automatically-tagged`: Worte sind automatisch ausgezeichnet.
- `manually-tagged`: Worte sind manuell ausgezeichnet.
- `not-tagged`: Worte sind nicht ausgezeichnet.
- `automatically-analyzed`: Worte sind automatisch analysiert.
- `manually-analyzed`: Worte sind manuell analysiert.
- `not-analyzed`: Worte sind nicht analysiert.
  
Normalerweise werden Worte im Zuge der Publikation im Webfrontend des PTA automatisch ausgezeichnet und analysiert.
  
#### Normalisierung
  
Innerhalb des Abschnittes `<editorialDecl>` wird in den Unterabschnitten `<normalization>` und `<punctuation>` beschrieben, inwieweit der handschriftlich überlieferte Text in der kritischen Edition normalisiert worden ist. Anpassungen sind vorzunehmen.
  
```xml
<editorialDecl>
  ...
  <normalization>
    <p>Usage of capitalisation, ν-ephelkystikon, σ: οὕτως, Iota subscriptum/adscriptum, 
      Trema, Enclitics, apostroph/elisions, number signs, splitting of words, 
      nomina sacra, ...</p>
 </normalization>
 <punctuation>
    <p>Usage (and/or normalisation) of full stop, comma, semicolon, question mark, 
      dash and parenthesis</p>
 </punctuation>
</editorialDecl>
```  
  
#### Art der Auszeichnung der Varianten
  
Als letztes Element im Abschnitt `<encodingDesc>` wird die Art der Auszeichnung der textkritischen Varianten angegeben. Der Eintrag *muss* lauten:
  
```xml
<variantEncoding method="parallel-segmentation" location="internal"/>
```  
  
#### Art der Edition
  
Die Art der Edition wird innerhalb des Abschnittes `<profileDesc>` im Unterabschnitt `<textClass>` unter `<keywords scheme="#editionstatus">` angegeben. Das Element `<term>` kann folgende Inhalte annehmen:
  
-   `critical-edition` für eine kritische Edition, bei der die textkritischen Varianten kodiert worden sind. Das sollte der Normalfall für Neueditionen sein, die dem hier vorgestellten Modell folgen.
  
-   `critical-edition-no-app` für eine kritische Edition, bei der die textkritischen Varianten nicht kodiert worden sind, z.B. weil es sich um die Retrodigitalisierung einer gedruckten kritischen Edition handelt und aus urheberrechtlichen Gründen der Apparat in die Retrodigitalisierung nicht einbezogen werden kann.
  
-   `critical-edition-outdated` für eine Edition, die zwar textkritische Varianten vermerkt, aber z.B. den handschriftlichen Befund nicht umfassend einbezieht.
  
-   `pre-critical-edition` für vormoderne Editionen (z.B. in der
    Patrologia Graeca oder Latina).
  
Die Kategorien sind innerhalb des `<classDecl>`-Elements in einem `<taxonomy>`-Element mit `@xml:id="editionstatus"` definiert:
  
```xml
<classDecl>
    ...
    <taxonomy xml:id="editionstatus">
       <bibl>Patristic Text Archive Status of edition</bibl>
       <category xml:id="critical-edition">
          <catDesc>Critical edition in which the text-critical variants have been encoded.</catDesc>
       </category>
       <category xml:id="critical-edition-no-app">
          <catDesc>Critical edition in which the text-critical variants have not been encoded, e.g. because it is a retro-digitisation of a printed critical edition and for copyright reasons the apparatus cannot be included in the retro-digitisation.</catDesc>
       </category>
       <category xml:id="critical-edition-outdated">
          <catDesc>Edition which notes text-critical variants, but does not, for example, comprehensively include the manuscripts.</catDesc>
       </category>
       <category xml:id="pre-critical-edition">
          <catDesc>Pre-modern editions (e.g. editions in the Patrologia Graeca or Latina)</catDesc>
       </category>
    </taxonomy>
    ...
 </classDecl>
```  
  
Ein Sonderfall ist `metacritical-edition-with-app`, das für die [SBLGNT-Edition](https://www.sblgnt.com/ ) des neuen Testamentes Verwendung findet.
  
#### Status der Edition
  
Schließlich erhält das Element `<revisionDesc>` ein Attribut `@status`, in dem der Status der Edition angegeben wird. Möglich sind dabei folgende Werte:
  
- `draft`: Entwurf, Edition in Arbeit
- `unfinished`: Noch in Bearbeitung, zum Beispiel fehlen noch Annotationen
- `final`: Finale, (noch) nicht freigegebene Version
- `approved`: Freigegebene, finale Version
  
### Edition
  
Die gesamte kritische Edition steht im `<text>`-Teil der Datei. Sie besteht mindestens aus einem Element `<div>`, das den edierten Text enthält. Das Element hat die folgenden Attribute: 
- `type="edition"`
- `@xml:lang` mit der Angabe der Sprache des edierten Textes unter Verwendung von [ISO 639-2](https://www.loc.gov/standards/iso639-2/php/code_list.php ).
- `@n` mit der URN der Datei, s. [unten](#dateien-struktur-jeder-edition ).
  
```xml
<div type="edition" xml:lang="grc" n="urn:cts:pta:pta0007.pta010.pta-grcBibex">
<!-- Text der Edition -->
</div>
```  
  
Bei Neueditionen sollte der Edition ein Abschnitt `<div type="praefatio">` mit der Praefatio vorangehen.
  
#### Praefatio
  
Die Praefatio bietet in einem Fließtext alles, was zum Verständnis des folgenden Textes und seiner Überlieferung notwendig ist. Vor allem sollte der kritische Wert der Handschriften und ihr gegenseitigen Verhältnis zueinander dargelegt, antike Übersetzungen und die sonstige indirekte Überlieferung sowie früheren Ausgaben und Übersetzungen in moderne Sprachen genannt und in ihrem kritischen Wert gewürdigt werden.
  
Grundsätzlich ist es dabei sinnvoll, die Angaben, die im `<teiHeader>` gemacht wurden, mit Hilfe von Verweisen (mit dem Element `<ref>` und dem Attribut `@target`) zu verlinken.
  
Unterabschnitte können mit Hilfe von `<div type="section" n="1">` (und 
diesem untergeordnet `<div type="subsection" n="1">`) eingerichtet werden, 
die im Element `<head>` auch eigene Überschriften enthalten können.
  
```xml
<div type="praefatio" xml:lang="deu">
    <div type="section" n="1">
        <head>Vorbemerkung</head>
        <p>Text</p>
        <div type="subsection" n="1">
            <head>Überschrift</head>
            <p>Text</p>
        </div>
    </div>
</div>
```  
  
Für Fußnoten wird das Element `<note>` verwendet. Bibliographische Angaben, die nicht im `<teiHeader>` definiert sind, können an Ort und Stelle mit Hilfe des Elements `<bibl>` (das Attribut `@xml:id` kann verwendet werden, um Verweise auf solche Titel zu ermöglichen) ausgezeichnet werden. Es sind auch Verweise auf den Text (bzw. Varianten) möglich, wenn eine `@xml:id` beim entsprechenden Element (z.B. `<w>`, `<seg>`, `<app>` oder `<rdg>`) gesetzt ist. Listen dürfen ebenfalls verwendet werden.
  
```xml
<p>
Daneben gibt es Sonderfehler von <ref target="#Pg">Pg</ref>
gegenüber allen anderen Handschriften, aber keinen von
<ref target="#Vi">Vi</ref>, so dass <ref target="#Pg">Pg</ref>
als Abschrift von <ref target="#Vi">Vi</ref> anzusehen ist, 
die wiederum selbst eine Abschrift von <ref target="#La">La</ref>
ist.<note>Diese Abhängigkeitsverhältnisse konnten auch <bibl>Kotter, 
Die Schriften des Johannes von Damaskos IV, Patristische Texte und 
Studien 22, Berlin/New York 1981, 345 f.348</bibl> und 
<ref target="#Savvidis">Savvidis, 396 f.</ref> anhand der von 
ihnen jeweils edierten Texte aufzeigen.</note>
</p>
```  
  
#### Text
  
##### Auszeichnung der Textstruktur
  
Innerhalb des Elements `<div type="edition">` wird die vom Editor rekonstruierte Textstruktur (entsprechend den Angaben in der `<refsDecl n="CTS">` im `<teiHeader>`) mit Hilfe von (auch ineinander geschachtelten) Unterabschnitten `<div>` vom `@type="textpart"` ausgezeichnet, wobei folgende Werte für das Attribut `@subtype` möglich sind:
  
-   Teil: `<div type="textpart" subtype="part" n="1">`
  
-   Buch: `<div type="textpart" subtype="book" n="1">`
  
-   Homilie: `<div type="textpart" subtype="homily" n="1">`
  
-   Kapitel:
    `<div type="textpart" subtype="chapter" n="1">`
  
-   Unterdokument: `<div type="textpart" subtype="subdok" n="1">`
  
-   Praefatio (nicht-nummeriertes Vorwort im Text): `<div type="textpart" subtype="praefatio" n="praefatio">`
  
-   Abschnitt:
    `<div type="textpart" subtype="section" n="1">`
  
-   Fragment:
    `<div type="textpart" subtype="fragment" n="1">`
  
-   Testimonium:
    `<div type="textpart" subtype="testimonium" n="1">`
  
-   Kommentierter Text: `<div type="textpart" subtype="commented" n="Gen_1_1">` 
  
-   Kommentierung:
    `<div type="textpart" subtype="commentary" n="Gen_1_1">` (vgl. auch die Ausführungen [oben](#auszeichnung-der-textstruktur ))
  
Das Attribute `@n` enthält die Stellenreferenz, normalerweise eine Zahl, sie kann aber auch Text wie „pr”, „hypopsalmos”, „hypothesis”, „perioche” usw. enthalten. Sie darf aber kein Leerzeichen enthalten, sondern nur Buchstaben, Zahlen, Symbole und Interpunktionszeichen. 
  
Absätze innerhalb dieser Unterabschnitte werden mit Hilfe des Elements `<p>` ausgezeichnet. Jedes Element `<div>` enthält mindestens ein Element `<p>`. Listen sind ebenfalls erlaubt: Sie werden (anstelle von `<p>`) mit dem Element `<list>`, die einzelnen Listeneinträge mit dem Element `<item>` ausgezeichnet. Hat eine Liste eine Überschrift, so wird diese mit Hilfe des Elementes `<head>` ausgezeichnet. 
  
#### Titel und titelähnliche Elemente
  
Titel werden mit dem Element `<title>` innerhalb des Elementes `<head>` ausgezeichnet:
  
```xml
<head>
 <title>Τοῦ αὐτοῦ ὁμιλία</title>
</head>
```  
  
Überschriftsähnliche Elemente, wie z.B. die Zuschreibung eines Zitates zu einem am Rand angeführten oder im Text hervorgehobenen Autors, werden mit dem Element `<label>` ausgezeichnet, das ein Attribut `@type` mit dem Wert `attribution` erhält. (Für die Auszeichnung von Sprechern in Dialogen siehe [unten](#auszeichnung-von-dialogen ).)
  
```xml
<p><label type="attribution">
    <persName key="PTA_P00001">Χρυσοστόμου</persName>.
</label> Προκαταλαμβάνει τὸν ἀκροατὴν τοῖς ἐπαίνοις· 
ὥστε μηδὲ ἄκοντα ἀποστῆναι. </p>
```  
  
  
##### Auszeichnung weiterer struktureller Elemente
  
Die Seitenumbrüche in den Handschriften und früheren Editionen werden nach Bedarf mit Hilfe des Elementes `<pb>` angegeben; die Seitenangabe steht im Attribut `@n` und auf die Handschrift bzw. die Edition wird im Attribut `@edRef` verwiesen:
  
```xml
<pb n="126r" edRef="#La"/>
```  
  
##### Auszeichnung von Bibel- und anderen Zitaten (und Anspielungen)
  
Zitate werden mit Hilfe des Elementes `<quote>` ausgezeichnet und können ein Attribut `@type` erhalten, so dass zwischen markierten (`marked`) und nicht-markierten (`unmarked`) Zitaten unterschieden werden kann; für paraphrasierende Zitate – soweit sie überhaupt als Zitat markiert werden – kann der Wert `paraphrasis` verwendet werden. Bei Editionen biblischer Kommentare erhalten Lemma-Zitate den Wert `lemma`, um sie von anderen Zitaten zu differenzieren.
  
Explizite Zitate unter Anführung des Autors des Zitates werden mit dem Element `<cit>` ausgezeichnet und die das Zitat anführende Phrase darin mit dem Element `<ref>`. Einschübe im Zitat (wie z.B. „sagte“) werden mit Hilfe von `<seg type="insertion">` innerhalb des Zitates ausgezeichnet.
  
Anspielungen (z.B. auf biblische Geschichten und Ereignisse) werden mit Hilfe von `<seg type="allusion">` ausgezeichnet.
  
Pseudo-Zitate können mit Hilfe von `<seg type="psq">` ausgezeichnet werden.
  
Bei Bibelzitaten wird die jeweilige Bibelstelle innerhalb des Elementes `<ref>` mit Verweis auf die Spezifikationen im `<teiHeader>` (`@decls="#biblical"`) im Attribut `@cRef` angegeben.
  
```xml
<p>Καὶ ὥσπερ ἐκεῖ εἴρηται· 
<quote type="marked">Καὶ προσκολληθήσεται πρὸς τὴν 
γυναῖκα αὐτοῦ, καὶ ἔσονται οἱ δύο εἰς σάρκα μίαν
<ref decls="#biblical" cRef="LXX:Gn:2:24"/></quote>, 
οὕτως ἡ ψυχὴ ἑνουμένη τῷ θεῷ λόγῳ βοᾷ· 
<quote type="marked">Ἐκολλήθη ἡ ψυχή μου ὀπίσω σου· 
ἐμοῦ δὲ ἀντελάβετο ἡ δεξιά σου.
<ref decls="#biblical" cRef="LXX:Ps:62:9"/></quote> 
Εἶχεν οὖν ἡ παλαιὰ συναγωγὴ ἄνδρα τὸν νόμον, ὡς 
μαρτυρεῖ Ἡσαΐας σήμερον διὰ τοῦ ἀποστόλου φθεγξάμενος· 
<cit><ref decls="#biblical" cRef="NA:Gal:4:27">Τῇ γὰρ 
προφητικῇ κατεχρήσατο φωνῇ Παῦλος λέγων·</ref>
<quote type="marked">Καθὼς γέγραπται ὅτι πολλὰ τὰ τέκνα 
τῆς ἐρήμου μᾶλλον ἢ τῆς ἔχούσης τὸν ἄνδρα.</quote></cit>
</p>
```  
  
Werden nicht-biblische Texte zitiert, so wird die Stellenreferenz ebenfalls mit Hilfe des Elements `<ref>` angegeben: Ist der referenzierte Text im Patristischen Textarchiv vorhanden, so wird die PTA-URN mit Verweis auf die Spezifikationen im `<teiHeader>` (`@decls="#pta"`) im Attribut `@cRef` angegeben. Ist der referenzierte Text in der [Perseus Digital Library](https://scaife.perseus.org/ ) vorhanden, so wird die CTS-URN mit Verweis auf die Spezifikationen im `<teiHeader>` (`@decls="#perseus"`) im Attribut `@cRef` angegeben. Ist der referenzierte Text in keinem der beiden Repositorien vorhanden, so wird die Stellenangabe für den referenzierten Text im Attribut `@source` in der Form „Autorkürzel_Werkkürzel_Stelle“ angegeben; antike griechische Autoren sollten dabei nach den Verzeichnissen von [H. G. Liddell/R. Scott/H. S. Jones, A Greek — English Lexicon, Oxford ^9^1968](https://lsj.gr/wiki/Index:AuthorsWorks/All ) und G. W. H. Lampe, A Patristic Greek Lexicon, Oxford ^3^1987 abgekürzt werden, für lateinische sollten die Abkürzungen des Thesaurus Linguae Latinae (cf. [Index librorum scriptorum inscriptionum ex quibus exempla afferuntur](https://thesaurus.badw.de/en/tll-digital/index/ )) verwendet werden, wobei Punkte in den Abkürzungen ersatzlos gestrichen werden.
  
```xml
<p>ἐν δὲ <bibl>τῷ Ποιμένι</bibl> γέγραπται,
ἐπειδὴ καὶ τοῦτο καίτοι μὴ ὂν ἐκ τοῦ
κανόνος προφέρουσι· <quote>πρῶτον πάντων
πίστευσον, ὅτι εἷς ἐστιν ὁ θεός, ὁ τὰ
πάντα κτίσας καὶ καταρτίσας καὶ
ποιήσας ἐκ τοῦ μὴ ὄντος εἰς τὸ εἶναι
τὰ πάντα.
<ref decls="#pta" cRef="urn:cts:pta:pta0038.pta001.pta-grc1:mandatum.1.1"/>
</quote></p>
<p>ἔγραψε τοῖς ἰδίοις διαβεβαιούμενος, ὅτι
<quote>καὶ τῶν παλαιῶν τινας λογίους καὶ 
ἐπιφανεῖς ἐπισκόπους καὶ συγγραφέας ἔγνωμεν 
ἐπὶ τῆς τοῦ πατρὸς καὶ υἱοῦ θεότητος τῷ τοῦ 
ὁμοουσίου χρησαμένους ὀνόματι.
<ref source="Eus_epCaes_13"/>
</quote></p>
```  
  
##### Auszeichnung von Similia und Quellen
  
Similia werden mit Hilfe von `<seg type="similar">`, Quellen (soweit kein Zitat vorliegt) mit Hilfe von `<seg type="source>` ausgezeichnet. Die Fundstelle wird innerhalb des `<seg>`-Elementes in einem `<ref>`-Element angegeben. Bei den Stellenangaben wird wie bei den Zitaten vorgegangen.
  
```xml
<seg type="similar">
ἵνα εἰς βάθος διαδῷ τὴν οἰκείαν ἐνέργειαν ἡ βαφή
<ref decls="#pta" cRef="urn:cts:pta:pta0022.pta003.pta-grc1:12.1"/>
</seg>
```  
  
##### Auszeichung direkter Rede
  
Direkte Rede wird mit Hilfe des Elementes `<said>` ausgezeichnet.
  
```xml
<p>
καὶ μή μοι λέγε· 
<said>οὐκ ἔσχε καιρὸν πολιτεύσασθαι καλῶς.</said>
</p>
```  
  
##### Auszeichnung von Dialogen
  
Dialoge werden mit Hilfe des Elementes `<sp>` (anstelle von `<p>`) ausgezeichnet. Die jeweils sprechenden Personen werden mit Hilfe des Elementes `<speaker>` ausgezeichnet, das Gesprochene mit Hilfe von `<p>`.
  
```xml
<sp>
    <speaker>ΠΑΛΛΑΔΙΟΣ.</speaker>
    <p> Ἀληθές. </p>
</sp>
<sp>
    <speaker>ΚΥΡΙΛΛΟΣ.</speaker>
    <p> Δέλτιον δὲ δή σοι τουτὶ τὸ ἐν χεροῖν, ὅ τι; </p>
</sp>
```  
  
##### Auszeichnung von Personen, Organisationen und Orten
  
**Personen** werden mit Hilfe des Elementes `<persName>` ausgezeichnet. Im Fall von biblischen Personen wird das Attribut `@type` mit dem Wert `biblical` verwendet, alle anderen Personen erhalten kein Attribut `@type`. 
Im Attribut `@key` wird die `person_id` der [PTA-Personen-Liste](https://github.com/PatristicTextArchive/pta_metadata/blob/main/pta_persons.json ) angegeben, die ihrerseits auf die  Liste [„Translators Individualised Proper Names with all References”](https://github.com/tyndale/STEPBible-Data ) sowie ein eigenes Register der nicht-biblischen Personen zurückgreift. 
Nicht-biblische Personen, die im PTA-Register fehlen, können nach [Rücksprache](mailto:annette.von_stockhausen@bbaw.de ) ergänzt werden.
  
**Institutionen (wie Synoden oder theologische Gruppierungen), Völker und sonstige Gruppen** werden mit Hilfe des Elementes `<orgName>` ausgezeichnet.
Im Attribut `@key` wird die `org_id` der [PTA-Oranganisationen-Liste](https://github.com/PatristicTextArchive/pta_metadata/blob/main/pta_orgs.json ) angegeben. Organisationen, die im PTA-Register fehlen, können nach [Rücksprache](mailto:annette.von_stockhausen@bbaw.de ) ergänzt werden.
  
**Orte** werden mit Hilfe des Elementes `<placeName>` ausgezeichnet, im Attribut `@ref` wird auf die ID des [Pleiades-Gazetteers](https://pleiades.stoa.org/ ) (in Form der kompletten URL) verwiesen.
  
```xml
<p>
ἐπίσκοπον <persName key="PTA_P00012">Βασίλειον</persName> 
καὶ <orgName key="PTA_O00001">τὴν ἁγίαν σύνοδον τῶν πατέρων τῶν 
ἐν <placeName ref="https://pleiades.stoa.org/places/511268">Νικαίᾳ</placeName> 
σύνοδον</orgName>. 
τοίνυν ὁ <persName type="biblical" key="Adam_Gen.2.19">Ἀδὰμ</persName>
</p>
```  
  
  
##### Bezeugung des Textes
  
Die handschriftliche Bezeugung des Textes wird im Element `<app>`, das ein Attribut `@type` mit dem Wert `witnesses` erhält, dokumentiert. Das Element erhält im Attribut `@xml:id` einen eindeutigen Identifikator, im optionalen Attribut `@prev` bzw. `@next` wird auf den korrespondierenden Eintrag (`<witStart/>`/`<lacunaStart/>` -> `<witEnd/>`/`<lacunaEnd/>` und umgekehrt) verwiesen. Gegegebenenfalls kann im Attribut `@corresp` auf eine entsprechende textkritische Variante oder Lesart verwiesen werden, die dann ebenfalls einen eindeutigen Identifikator benötigt.
Das Element enthält nur das Element `<rdg>` mit dem Attribut `@wit`, in dem eines der selbst-schließenden Elemente `<witStart/>` (= Beginn eines Zeugen), `<witEnd/>` (= Ende eines Zeugen), `<lacunaStart/>` (= Beginn einer Lücke) oder `<lacunaEnd/>` (= Ende einer Lücke) eingefügt wird. Das Element enthält keinen Text, sondern wird (vergleichbar mit einem Milestone-Element wie `<pb>`) an der passenden Stelle im Text eingefügt: In Fall von `<witStart>` und `<lacunaEnd>` steht es vor dem ersten Wort, das im Zeugen vorhanden ist bzw. nachdem die Lücke zu Ende ist, im Fall von `<witEnd>` und `<lacunaStart>` steht es nach dem letzten Wort, das im Zeugen vorhanden ist bzw. vor dem die Lücke beginnt. 
  
```xml
<app type="variants">
    <lem wit="#Pt #Pc #Pb #Pd #My #Ma #Ha #Va #Ab">ἀπαστράπτει</lem>
    <rdg wit="#Pa #Be" xml:id="lac-Pa">ἀ</rdg>
    <witDetail wit="#Pa" target="#lac-Pa">Blattausfall.</witDetail>
</app> 
<app type="witnesses" xml:id="x1" next="#x2" corresp="#lac-Pa">
    <rdg wit="#Pa #Be"><lacunaStart/></rdg>
</app> ... καθʼ ἑαυτὴν ἔσωσεν. 
<app type="witnesses" xml:id="x2" prev="#x1" corresp="#lac-Pa">
    <rdg wit="#Pa #Be"><lacunaEnd/></rdg>
</app>
<app type="witnesses" xml:id="x3" next="#x4">
    <rdg wit="#Ecl114"><witStart/></rdg>
</app> μεμαρτύρητο ...
```  
  
(Diese etwas umständliche Art der Notation ist nötig, weil nach den [TEI-Richtlinien](https://tei-c.org/Vault/P5/2.0.0/doc/tei-p5-doc/en/html/ref-model.rdgPart.html ) die Elemente `<witStart/>`, `<lacunaStart/>`, `<witEnd/>`, `<lacunaEnd/>` nur innerhalb eines `<rdg>` oder `<lem>` in einem `<app>` stehen dürfen und der sinvolle [Änderungswunsch, diese Elemente auch außerhalb im Text zuzulassen, vom TEI Technical Council zurückgewiesen wurde](https://github.com/TEIC/TEI/issues/301 ).)
  
##### Auszeichnung der Varianten
  
Die Auszeichnung der Varianten spiegelt die im Editionsprozess erfolgten editorischen Entscheidungen, insbesondere die Beurteilung der Varianten und der stemmatischen Zusammenhänge, wieder und ist *keine* neutrale Beschreibung des Überlieferungsbestandes, sondern eine Interpretation desselben.
  
An jeder Stelle im Text, die in unterschiedlichen Fassungen überliefert ist, werden die Varianten innerhalb des Elementes `<app>` angegeben, das ein Attribut `@type` mit dem Wert `variants` erhält. Innerhalb dieses Elementes `<app>` wird der rekonstruierte Text mit dem Element `<lem>` ausgezeichnet, die als sekundär eingeschätzten Varianten mit dem Element `<rdg>`, wobei dieses innerhalb eines `<app>`-Eintrages im Gegensatz zu `<lem>` mehrfach vorkommen darf. 
Alle im folgenden beschriebenen Arten von varianter Überlieferung setzen eine Einschätzung der einzelnen Varianten als primär (`<lem>`) oder sekundär (`<rdg>`) voraus.
  
*Alle* Variantenträger werden im `<lem>`- und in den `<rdg>`-Elementen im Attribut `@wit` angegeben, wenn die Variante in einer Handschrift steht, im Attribut `@source` oder `@resp`, wenn die Variante auf eine Konjektur in einer Edition oder einer Person zurückgeht.
  
Bei einer gedruckten Edition würde man also von einem positiven Apparat sprechen, mit der Besonderheit, dass im Fall der digitalen kritischen Edition auch die Lesarten von codices descripti angegeben werden. Der Schritt der Elimination bzw. die Reduktion des positiven Apparates auf einen negativen Apparat kann, muss aber nicht, bei der Aufbereitung der Daten für die Präsentation (im Druck oder online) durchgeführt werden. In dieser Unterscheidung von vollständiger Datenaufnahme, die die Nachvollziehbarkeit und die Überprüfbarkeit der editorischen Entscheidungen in viel höherem Maße als bisher ermöglicht, und ggfs. selektiver Präsentation besteht der kategoriale Unterschied zwischen der überkommenen kritischen Edition im Druck und der kritischen digitalen Edition.
  
Die Werte der Elemente `@wit`, `@source` und `@resp` verweisen dabei auf die im Element `<sourceDesc>` (im `<teiHeader>`, [s.o.](#handschriftliche-zeugen-und-frühere-editionen )) jeweils angegebenen Werte des Attributs `@xml:id` des Elementes `<witness>`, `<bibl>` oder `<person>`.
  
Zur Erhöhung der Lesbarkeit für menschliche Rezipienten der Edition sollten alle Variantenträger innerhalb des Attributes `@wit` in einer einheitlichen Reihenfolge (und ggfs. unter Berücksichtigung stemmatischer Zusammenhänge) präsentiert werden.
  
Bei mehreren Varianten innerhalb eines `<app>`-Elementes sollen die verschiedenen `<rdg>`-Einträge so gereiht werden, dass sie desto früher angeführt werden, je näher sie stemmatisch (nach Einschätzung des Editors) der `<lem>`-Variante stehen.
  
In ihrer Genese oder auch sonst als zusammengehörig eingeschätzte Varianten (`<lem>` und `<rdg>` oder mehrere `<rdg>`-Einträge) können zur Verdeutlichung in einem Element `<rdgGrp>` zusammengefaßt werden.
  
Der Text der Variante ist immer in seinem vollen Wortlaut anzugeben und unter keinen Umständen abzukürzen.
  
  
##### Analyse der Gründe für die Variation
  
Varianten können ein Attribut `@cause` erhalten, mit dessen Hilfe die Editorin dem Rezipienten der Edition eine Erklärung für die Entstehung der Variante zur Verfügung stellt. Dadurch sind solche Varianten für die Präsentation auch leicht zu filtern. Folgende Werte dieses Attributes sind möglich:
  
-   `orthographic`, wenn eine Variante vom Editor als nur die Schreibweise betreffende, d.h.  beispielsweise bei griechischen   Handschriften mit großer  Wahrscheinlichkeit auf Itazismus beruhende Variante interpretiert wird.
-   `homoioteleuton` oder `homoiarkton` oder `saut_du_meme`, wenn eine Variante nach Einschätzung der Editorin auf Homoioteleuton oder Homoiarkton oder einen saut du même au même zurückzuführen ist.
-   `dittography`, wenn eine Variante als Dittographie gedeutet wird.
  
```xml
<app type="variants">
  <lem source="#Sav" type="conjecture">νομογράφῳ</lem>
  <rdgGrp>
    <rdg wit="#Be #Ab">τῷ νόμῳ γράφει</rdg>
    <rdg wit="#Pt #Pa #Pb #Pd #Ma #Ha #Va" cause="orthographic">τῷ νομῳ γράφει</rdg>
  </rdgGrp>
  <rdgGrp>
    <rdg wit="#Pc">τὸν νόμον γράφει</rdg>
    <rdg wit="#My" cause="orthographic">τὸν νόμων γράφει</rdg>
  </rdgGrp>
</app>
```  
  
##### Typisierung von Varianten
  
Die Ergebnisse der Analyse von Gründen für Varianten werden im Attribut
`@type` angegeben.
  
###### Hinzufügungen
  
Hinzufügungen, auch Dittographien und andere Wiederholungen, werden im
Element `<rdg>` als `<@type="addition">` ausgezeichnet. Das Element
`<lem>` bliebt dabei ohne Textinhalt („self-closing“).
  
```xml
<app type="variants">
 <lem wit="#Pt #Pc #Pd #Ma #My"/>
 <rdg wit="#Ha #Pa #Be" type="addition">καὶ περὶ τοῦ ἁγίου πνεύματος</rdg>
 <rdg wit="#Pb #Va" type="addition">λόγος πάνυ ὠφέλιμος</rdg>
</app>
```  
  
###### Auslassungen
  
Auslassungen werden als `<@type="omission">` ausgezeichnet. Das Element
`<rdg>` bleibt ohne Textinhalt („self-closing“).
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha">ἀπεικάζεται καὶ</lem>
 <rdg wit="#Pt #Pc #Pd #Ma #My #Ab" type="omission"/>
</app>
```  
  
###### Löschungen
  
Löschungen werden als `<@type="deletion">` ausgezeichnet, wobei (im Gegensatz zur Transkription) nicht mehr differenziert wird, wie der Text gelöscht worden ist, da diese Information jederzeit der Transkriptions-Datei zu entnehmen ist.
  
Löschungen werden von Auslassungen analytisch dadurch unterschieden, dass sie auf einen bewussten Eingriff des Schreibers der jeweiligen Handschrift zurückzuführen sind. 
Das Element `<rdg>` ist wiederum ohne Textinhalt („self-closing“).
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">καὶ</lem>
 <rdg wit="#Pb" type="deletion"/>
</app>
```  
  
###### Nicht lesbarer Text
  
Nicht lesbarer Text wird als `<@type="illegible">` ausgezeichnet. Das Element `<rdg>` ist ohne Textinhalt („self-closing“).
  
```xml
<app type="variants">
 <lem wit="#Pt #Pc #Pa #Be #Pb #Pd #Ma #My #Va #Ab">καὶ</lem>
 <rdg wit="#Ha" type="illegible"/>
</app>
```  
  
###### Lücke im Text einer Handschrift
  
Eine Lücke im Text einer Handschrift wird entsprechend den Transkriptionsregeln als `<@type="damage">` (Beschädigung) als `<@type="fenestra">` (freigelassen) oder als `<@type="deletion">` (Tilgung) ausgezeichnet. Das Element `<rdg>` ist ohne Textinhalt („self-closing“).
  
###### Umstellungen
  
Umstellungen werden als `<@type="transposition">` ausgezeichnet. Im Element `<rdg>` wird der umgestellte Text in seinem vollen Wortlaut (sc. nicht abgekürzt) wiedergegeben.
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha">τὰ τοῦ θεοῦ</lem>
 <rdg wit="#Pt #Pc #Pd #Ma #My #Ab" type="transposition">τοῦ
   θεοῦ τὰ</rdg>
</app>
```  
  
Umstellungen, die längere Textpassagen betreffen, werden – besonders wenn sie sich über strukturelle Einheiten hinweg erstrecken – als Auslassung und Hinzufügung ausgezeichnet, wobei beide `<app>`-Elemente jeweils ein Attribut `@xml:id` erhalten und auf das jeweils andere mit Hilfe der Attribute `@prev` und `@next` verwiesen wird.
  
```xml
<div type="textpart" subtype="section" n="1">
    <p>οὐδὲ γἁρ 
    <app type="variants" xml:id="app1-1" next="#app1-2">
        <lem wit="#Pt #Pb #My #Ha #Va #Ab">καλόν ἐστι</lem>
        <rdg wit="#Pc #Pd Ma" type="omission"/>
    </app>
    </p>
</div>
<div type="textpart" subtype="section" n="2">
    <p>τὸ ἔξω τοῦ οἴκου τοῦ θεοῦ πολιτεύεσθαι
    <app type="variants" xml:id="app1-2" prev="#app1-1">
        <lem wit="#Pt #Pb #My #Ha #Va #Ab"/>
        <rdg wit="#Pc #Pd #Ma" type="addition">καλόν ἐστι</rdg>
    </app>
      </p>
</div>
```  
  
###### Korrekturen durch Schreiber
  
Korrekturen des Textes durch den Schreiber oder einen späteren Korrektor werden so ausgezeichnet, dass im Element `<rdg>` mit Hilfe des Attributes `@varSeq` die Reihenfolge der verschiedenen Stadien der Überlieferung angegeben wird.
  
Das Element `<rdg>` kann zusätzlich das Attribut `@hand` enthalten, wobei der Schreiber (`#m1`) und die Korrektoren (`#m2`, `#m3`, … – allgemein `#mr` für *manus recentior*) unterschieden werden sollten. Ist nicht zu entscheiden, von welcher Hand eine Korrektur vorgenommen worden ist, erhält das Attribut den Wert `unknown`.
  
Der Ort der Korrektur wird mit Hilfe der entsprechenden Elemente für Löschung, Hinzufügung, etc. mit ihren jeweiligen Attributen wiedergegeben, [siehe oben in den Transkriptionsregeln](#edition-der-transkription ).
  
  
```xml
<app type="variants">
    <rdgGrp>
        <lem wit="#Pa #Pb #Ha #Va">ὁ γενναῖος ἐκεῖνος</lem>
        <rdg wit="#Be" varSeq="2" hand="m2"><add place="above">ὁ γενναῖος ἐκεῖνος</add></rdg>
    </rdgGrp>
    <rdg wit="#Be" varSeq="1" type="transposition">ἐκεῖνος ὁ γενναῖος</rdg>
</app>
<app type="variants">
    <lem wit="#Ax #Be #Eb #Is #Kc #Ox #Pa #Pu #Sm #Sn #To"/>
    <rdg wit="#Ad #Af #Ap #Ga #Hb #Ka #Mp #Mz #Oe #Pb #Pc #Pd #Pt #St #Vf #Vl" type="addition">τὴν</rdg>
    <rdg wit="#Pi" varSeq="2">
        <subst>
            <del type="strikethrough">τῆς</del>
            <add place="above">τὴν</add>
        </subst>
    </rdg>
    <rdg wit="#Pi" varSeq="1">τῆς</rdg>
    <rdg wit="#Mo"><gap reason="illegible" unit="character" quantity="6"/></rdg>
</app> 
```  
  
Auch mikroskopische Textersetzungen (wie z.B. die Ersetzung einzelner Buchstaben innerhalb eines Wortes) werden entsprechend dem Vorgehen bei der Handschriftentranskription innerhalb eines `<subst>`-Elementes mit dem Element `<del>` (ersetzter Text) und dem Element `<add>` (ergänzter Text) ausgezeichnet. Das Element `<subst>` erhält in diesem Fall das Attribut `@hand`. 
Wird bei einer Korrektur nur Text hinzugefügt oder getilgt, so wird nur das Element `<add>` bzw. `<del>` verwendet und das Attribut `@hand` diesem Element beigefügt.
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">ἔχωμεν</lem>
 <rdg wit="#Ha" varSeq="2">ἔχ<subst hand="#m2">
   <del>ο</del>
   <add place="above">ω</add>
  </subst>μεν</rdg>
 <rdg wit="#Ha" varSeq="1">ἔχομεν</rdg>
</app>
```  
  
###### Konjekturen durch Editoren
  
Konjekturen werden mit `<@type="conjecture">` ausgezeichnet: Erfolgt dies im Element `<lem>`, so handelt es sich um eine Emendation des Editors (oder um eine ältere Emendation, der sich der Editor anschließt), erfolgt dies im Element `<rdg>`, so handelt es sich um eine vom Editor nicht übernommene Konjektur anderen Ursprunges.
  
Korrekturen kleinerer Fehler (bzw. orthographische Normalisierungen), die nicht die Höhe einer Konjektur erreichen, werden mit `<@type="correction">` ausgezeichnet.
  
```xml
<app type="variants">
 <lem resp="#AvS" type="correction">οὐκ</lem>
 <rdg wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">οὐχ</rdg>
</app>
```  
  
Vorschläge von Konjekturen (*proposuit* oder *dubitanter*) werden im Element `<rdg>` als `<@type="proposition">` ausgezeichnet. Ggfs. kann der Wahrscheinlichkeitsgrad des Zutreffens im Attribut `@cert` festgehalten werden; mögliche Werte sind: `low`, `medium`, `high`.
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">ψευδόμενος</lem>
 <rdg resp="#AvS" type="proposition" cert="low">ἀδικῶν</rdg>
</app>
```  
  
Vom Editor getilgter Text wird mit `<@type="deletion">` im Element `<lem>` ausgezeichnet. Soll der getilgt Text angeführt werden, so wird er mit Hilfe des Elementes `<surplus>` ausgezeichnet; ansonsten bleibt das Element ohne Textinhalt („self-closing“). Tilgungen durch andere Editoren werden ebenfalls als `<@type="deletion">` ausgezeichnet, der getilgte Text wird mit Hilfe des Elements `<surplus>` ausgezeichnet. 
  
```xml
<app type="variants">
 <lem resp="#AvS" type="deletion"/>
 <rdg wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">οὐκ</rdg>
</app>
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">οὐκ</lem>
 <rdg source="#Sav" type="deletion"><surplus>οὐκ</surplus></rdg>
</app>
```  
  
Durch Emendation hinzugefügter Text wird mit `<@type="addition">` ausgezeichnet.  Die handschriftlich überlieferte Varianten werden im Element `<rdg>` mit `@type="omission"` ausgezeichnet; das Element `<rdg>` bleibt ohne Textinhalt („self closing“). 
  
Der hinzugefügte Text wird mit Hilfe des Elementes `<supplied>` ausgezeichnet, um den Umfang der Hinzufügung deutlich zu machen, wenn in der handschriftlichen Überlieferung vorhandener Text ergänzt wird; in diesem Fall wird statt `<@type="addition">` besser `<@type="conjecture">` verwendet.
  
```xml
<app type="variants">
<lem resp="#AvS" type="addition">οὐκ</lem>
<rdg source="#Schwartz" type="addition">μὴ</rdg>
 <rdg wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab"
  type="omission"/>
</app>
  
<app type="variants">
    <lem resp="#AvS" type="conjecture">Σευηρι<supplied>αν</supplied>οῦ</lem>
    <rdg wit="#P">Σευηρίου</rdg>
</app>
```  
  
Auf den Autor einer Konjektur, Emendatio oder Korrektur wird im Attribut `@resp` bzw. im Falle einer aus einer Edition übernommenen Konjektur im Attribut `@source` verwiesen (im Gegensatz zum Attribut `@wit` für Handschriften).
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">ψευδόμενος</lem>
 <rdg source="#Savile1612" type="conjecture">ἀδικῶν</rdg>
 <rdg resp="#Ac" type="conjecture">ψευσάμενος</rdg>
</app>
```  
  
###### Lücken im Text
  
Von der Editorin vermutete Lücken im überlieferten Textbestand werden mit `<gap reason="missing"/>` ausgezeichnet. Die vermutete Ausdehnung (`@quantity`) der Lücke wird, wo es sinnvoll und möglich erscheint (!), in Buchstaben, Worten, Zeilen oder Seiten (`@unit` mit Wert `character`, `word`, `line` oder `page`) angegeben.
  
Wird die Feststellung einer Lücke von einem früheren Editor übernommen, so wird die Quelle im Attribut `@source` bzw. `@resp` angeführt.
  
```xml
Ταῦτα λέγω εἰς <gap reason="missing" unit="word" quantity="3"/> ση τοὺς καταφεύγοντας κατέλαβεν τότε κατακλυσμός, 
```  
  
Von anderen Editoren vermutete, aber nicht übernommene Lücken werden in einem Apparateintrag als `<rdg>` ausgezeichnet und erhalten das Attribut `@type="lacunam_indicavit"`. Das Element ist ohne Textinhalt („self closing“).
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab"/>
 <rdg wit="#Sav" type="lacunam_indicavit"/>
</app>
```  
  
###### Crux
  
Vom Editor nicht zu emendierender, aber sicher verderbter Text („Crux“) wird mit Hilfe des Elementes `<sic>` ausgezeichnet. Das Element kann dabei sowohl den verderbten Text umschließen oder als selbst-schließendes („leeres“) Element die Stelle der Verderbnis markieren.
  
```xml
καὶ ὅσα ὁ νόμος <sic>διαγορεύει</sic>, 
ὅσα προφῆται <sic/> θεσπίζουσιν 
```  
  
###### Varianten innerhalb von Varianten
  
Varianten können auch ineinander geschachtelt werden, d.h. ein `<lem>`- oder ein `<rdg>`-Element kann seinerseits eine Variante (`<app>`) enthalten. Das `wit`-Attribut des übergeordneten `<app>`-Elementes enthält dabei *alle* Siglen des untergeordeneten `<app>`-Elementes, also sowohl des `<lem>`- als auch des `<rdg>`-Elementes:
  
```xml
<app type="variants">
  <lem wit="#Pb #Pt #Pc #Pa #Be #Pd #Ma #My #Ha #Va">οὐδεμίαν 
   <app type="variants">
    <lem wit="#Pt #Pc #Pa #Be #Pd #Ma #My #Ha #Va">εὑρήσεις</lem>
    <rdg wit="#Pb" cause="orthographic">εὑρήσῃς</rdg>
   </app>
  </lem>
  <rdg wit="#Ab" type="omission"/>
 </app>
```  
  
##### Ökonomische Schreibweise
  
In ihrer Genese zusammengehörige Variantenteile sollten, solange die Variantenträger identisch sind, zur Erhöhung der Lesbarkeit möglichst zusammengefasst werden.
  
```xml
<app type="variants">
 <lem wit="#Pt #Pc #Pa #Be #Pb #Pd #Ma #My #Va #Ab">καὶ νῦν</lem>
 <rdg wit="#Ha" type="omission"/>
</app>
```  
  
und nicht:
  
```xml
<app type="variants">
 <lem wit="#Pt #Pc #Pa #Be #Pb #Pd #Ma #My #Va #Ab">καὶ</lem>
 <rdg wit="#Ha" type="omission"/>
</app>
<app type="variants">
 <lem wit="#Pt #Pc #Pa #Be #Pb #Pd #Ma #My #Va #Ab">νῦν</lem>
 <rdg wit="#Ha" type="omission"/>
</app>
```  
  
##### Überlappungen
  
Ein aus der Struktur der Auszeichnungssprache XML resultierendes Problem bilden Überlappungen von Elementen untereinander; vgl. dazu auch das Kapitel [„Non-hierarchical Structures“ in den TEI-Richtlinien](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/NH.html ). 
  
Nach Möglichkeit sollte entsprechend der ebd. genannten Methode [„Fragmentation and Reconstitution of Virtual Elements“](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/NH.html#NHVE ) vorgegangen werden.
  
Überschneiden sich Elemente unterschiedlicher Kategorie, also z.B. eine textkritische Anmerkung und ein Zitat, so ist dem Element `<app>` der Vorrang einzuräumen und das Element `<quote>` aufzuteilen, wobei die zusammengehörigen Teile des Elementes mit Hilfe der Attribute `@prev` und `@next`, die auf die im Attribut `@xml:id` jeweils zugeteilte ID verweisen, miteinander verbunden werden:
  
```xml
<p>Διὰ τί ἐσαλεύθησαν θεμέλιοι τῆς δημιουργίας; 
<quote xml:id="qu1-1" next="#qu1-2">Τί σοι ἐστί,</quote>
<app type="variants">
  <lem wit="#Pc #Pt #My">
    <quote xml:id="qu1-2" prev="#qu1-1">θάλασσα, ὅτι ἔφυγες;
    <ref decls="#biblical" cRef="LXX:Ps:113:3"/></quote> 
    τί ἔλυσας τὸν ὅρον τοῦ νομοθέτου, τοῦ κελεύσαντός σοι 
    <quote xml:id="qu2-1" next="#qu2-2">Μέχρι τούτου ἐλεύσῃ</quote>
  </lem>
  <rdg wit="#Pd" type="omission"/>
</app>
<quote xml:id="qu2-2" prev="#qu2-1">καὶ οὐχ ὑπερβήσῃ
<ref decls="#biblical" cRef="LXX:Job:38:11"/></quote>;</p>
```  
  
Überschreitet eine Variante eine Gliederungsebene, so muss dieser der
Vorrang eingeräumt und das Element `<app>` analog dem obigen Vorgehen
aufgeteilt und untereinander verlinkt werden.
  
```xml
<div type="textpart" subtype="section" n="1">
    <p>...
    <app type="variants" xml:id="app1-1" next="#app1-2">
        <lem wit="#Pt #Pb #My #Ha #Va #Ab">οὐδὲ γάρ ἐστι καλὸν τὸ ἔξω τοῦ οἴκου τοῦ θεοῦ πολιτεύεσθαι.</lem>
        <rdg wit="#Pc #Pd #Ma">οὐδὲν</rdg>
    </app>
    </p>
</div>
<div type="textpart" subtype="section" n="2">
    <p>
    <app type="variants" xml:id="app1-2" prev="#app1-1">
        <lem wit="#Pt #Pb #My #Ha #Va #Ab">εὑρήσεις</lem>
        <rdg wit="#Pc #Pd #Ma" cause="orthographic">εὑρήσης</rdg>
    </app>
    ...
    </p>
</div>
```  
  
##### Kommentierung textkritischer Entscheidungen
  
Erscheint es nötig oder sinnvoll, textkritische Überlegungen, die über die Typisierung (mit Hilfe des Attributes `@type`) oder die Angabe von Ursachen (mit Hilfe des Attributes `@cause`) hinausgehen, auszuführen, so kann dafür an Ort und Stelle innerhalb des Elementes `<app>` ein Element `<note>` für Bemerkungen, die das gesamte `<app>`-Element betreffen, oder ein Element `<witDetail>` für Bemerkungen, die sich auf eine spezielle Handschrift bezieht, angefügt werden; im Falle von `<witDetail>` wird in einem Attribut `@wit` auf die ID der Handschrift verwiesen. 
  
```xml
<app type="variants">
  <lem wit="#Pt #Pc #Pb #Pd #My #Ma #Ha #Va #Ab">ἀπαστράπτει</lem>
  <rdg wit="#Pa #Be">ἀ</rdg>
  <witDetail wit="#Pa">Blattausfall.</witDetail>
  <note>Sich auf die gesamte Variante beziehende Anmerkung</note>
</app>
```  
  
  
## Dateien-Struktur jeder Edition
  
Für eine möglichst einfache Wiederbenutzbarkeit sind schließlich auch eine einheitliche Benennung der einzelnen Dateien und eine strukturierte Dateiablage sinnvoll. Das „Patristic Text Archive“ folgt hier den [„Capitains Guidelines“](http://capitains.org ) (cf. [Thibault Clérice, Matthew Munson, & Bridget Almas. (2017, May 2). Capitains/Capitains.github.io: 2.0.0 (Version 2.0.0). Zenodo.](http://doi.org/10.5281/zenodo.570516 )) und verwendet [CTS URNs](http://www.homermultitext.org/hmt-docs/cite/cts-urn-overview.html ) (vgl. auch [Christopher W. Blackwell und Neel Smith, „The CITE Architecture: a Conceptual and Practical Overview“, in Monica Berti, Hg., Digital Classical Philology. Ancient Greek and Latin in the Digital Revolution (Age of Access? Grundfragen der Informationsgesellschaft 10; Berlin, 2019), 73–93](https://doi.org/10.1515/9783110599572-006 )). 
  
Innerhalb eines Ordners `data` erhält jeder Autor (oder jede Werkgruppe) einen Ordner, der nach der ID für den Autor oder die Werkgruppe benannt ist. Innerhalb dieses Ordners befinden sich Unterordner, die jeweils nach der IDs für das einzelne Werk benannt sind. In jedem Ordner befindet sich eine Datei `__cts__.xml`, die die Metadaten für die Daten der jeweiligen Ebene enthalten.
  
    data/
      |- pta0013
        |- __cts__.xml
        |- pta003
          |- __cts__.xml
          |- pta0013.pta003.pta-deu1.xml
          |- pta0013.pta003.pta-grc1.xml
          |- pta0013.pta003.pta-MsLa.xml
          |- pta0013.pta003.pta-MsPg.xml
          |- pta0013.pta003.pta-MsPs.xml
          |- pta0013.pta003.pta-MsVi.xml
  
Die Dateinamen folgen den CTS URNs und sind folgendermaßen aufgebaut: Das Kürzel „pta0013“ steht dabei für den Autor Amphilochius und „pta003“ für das Werk „Epistula synodalis“. Der letzte Teil der URN identifiziert die spezifische „Edition“ eines Werkes: Im Beispiel sind das die
kritische Edition des griechischen Textes (pta-grc1), die deutsche Übersetzung (pta-deu1) und die Transkriptionen der vier Handschriften (pta-MsLa, pta-MsPg, pta-MsPs, pta-MsVi).
  
Die Zuteilung neuer IDs für bisher nicht vorhandene Autoren und/oder Werke erfolgt nach [Rücksprache](mailto:annette.von_stockhausen@bbaw.de ).
  
Autor: [Annette von Stockhausen](mailto:annette.von_stockhausen@bbaw.de )
  