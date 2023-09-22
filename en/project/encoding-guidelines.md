The edition guidelines for the PTA are set out in a [schema](https://doi.org/10.5281/zenodo.3737666 ) that narrows down the comprehensive and often redundant regulations of the TEI in a TEI-compliant way and that is the basis of the following rules and examples.
  
> These edition guidelines are a slightly abridged version (but *updated* to version 3.0 of the schema) [of Annette v. Stockhausen, Die Modellierung kritischer Editionen im digitalen Zeitalter, ZAC 24 (2020), 123-160](https://nbn-resolving.org/urn:nbn:de:kobv:b4-opus4-35237 ). This schema has its origins in the Epidoc Guidelines, but has significantly expanded and modified them.
  
The choice of the TEI-XML mark-up language for the encoding of the digital critical edition marks a fundamental difference from the classical critical edition as we know it from our printed editions, namely the distinction between the encoding of the edition in digital format and its presentation in print, on the internet, as an e-book, etc. The edition in the true sense is the data encoded in TEI-XML, which can be expected to remain available and receivable over a long period of time, while its presentation in print or on the internet is a matter of reduced (or enriched) manifestations of this data in terms of information content, which, especially in the case of online presentation, is subject to the constant change of technology. 
In any case, the advantages of a critical digital edition, as defined and exemplified in the following, should be noted:
  
1.  The creation of full-text transcriptions (instead of recording only readings in a collation table) and the publication of this research data as part of the digital edition increase the comprehensibility of the text-critical decisions made by the editor and make possible a comprehensive review that goes far beyond the variants presented in the *praefatio* of a printed edition, since that is always a matter of concentrating information in as little space as possible.
  
2.  The decisions underlying the *constitutio textus* can be explained in *situ* by text-critical commentaries. This also increases the transparency of the edition.
  
3.  The simultaneous provision of manuscript transcription *and* critical edition keeps the edition open to different edition-philological approaches.
  
4.  Due to the strict separation of data (with a focus on completeness) and presentation of the data (in a selection of presented phenomena made for the respective medium and the respective purpose or question), quite different modes of presentation can be chosen on the basis of a data set, which can additionally be enriched by further data from other sources.
  
##  Building a digital edition according to TEI
  
  
> The following writing conventions are used in these guidelines: `<element>` means XML elements, `@attribute` means XML attributes, and `value` means the values attributed to the attributes; `#` in a value means that it is an identifier defined elsewhere in the TEI file, usually the `<teiHeader>`, which is referenced at this point.
  
TEI files are basically divided into two parts: They contain a [`<teiHeader>`](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-teiHeader.html ) section with all metadata and a [`<text>`](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-text.html ) section with the edition.
  
All files (transcriptions, editions or translations) contain the following metadata in the `<teiHeader>`:
  
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
  
The section `<fileDesc>` contains the bibliographical information on the file, in particular information
  
- on the title (`<titleStmt>`)
- on the publication (`<publicationStmt>`). In this section, the IDs (`<idno>`) (e.g. CPG, CPL, BHG, Pinakes-Oeuvre) should be adjusted, as this enables the interchangeability and linking of the data.
- on the sources (`<sourceDesc>`). In this section, the information in the three types of files (transcription, critical edition, translation) differs significantly.
  
The `<encodingDesc>` section provides all the information concerning the
encoding of the file and in each case contains an element `<refsDecl>`,
which defines the outline structure of the file according to the
[“CapiTainS Guidelines”](http://capitains.org/ ) ([cf. below](#file-structure-of-each-edition )). The section ends with the element `<schemaRef>` which references the version and the used schema.
  
Information on the dating (`<date>`) and location (`placeName`) of the text is provided in the `<creation>` element and on the genre (using the text type classification of <https://www.comphistsem.org/46.html>) in the `<textClass>` element within the `<profileDesc>` section.
  
Since digital editions, unlike printed editions, can be potentially very fluid data, it is of great importance that all significant changes to the file and its authors are recorded in the `<revisionDesc>` section, so that the version history of the individual files can be traced even when detached from the [PTA’s Git repository](https://github.com/PatristicTextArchive/pta_data/ ).
  
##  Transcription of the witnesses
  
  
Manuscripts are witnesses to a specific stage in the transmission of a text. In contrast to the classical “Lachmannian” approach, in which in practice only the variants of the master copy of the text (the archetype) are noted, it is appropriate for digital editions - also taking into account the basic idea of the “New Philology” of valuing each individual transmission medium - and also makes sense in terms of labour economy to transcribe the entire text and then, in a second step, to carry out the collation of the witnesses with the help of the computer.
  
> In the Berlin academy project “Die alexandrinische und antiochenische Bibelexegese in der Spätantike” which uses the PTA as its digital publication platform, the [CollateX](https://web.archive.org/web/20200329141404/https://collatex.net/ ) programme is used for this purpose, whereby the transcription files are converted into the input format required for CollateX with the help of a Python script (<https://github.com/PatristicTextArchive/collator>). Minor errors in the alignment of the collation table can be corrected manually afterwards.
  
The transcriptions are thus also editions and the result of interpretation. However, they differ from the critical edition (see below) in that they follow a diplomatic (documentary) edition paradigm: The phenomena found in the manuscript, such as the spelling of words, accentuation, punctuation and word division, are in principle not normalised in the transcription, i.e. not corrected if necessary. In addition, page, column and line breaks, initials and ektheseis, marginalia, abbreviations, markings, rubrics, erasures, additions - also from a diachronic point of view (sc. in view of scribe changes) - are recorded, but not marked according to their visual appearance, but according to their semantics, i.e. subjected to an interpretation. Even phenomena that cannot be interpreted, such as text that cannot be deciphered, are marked as such and thus uncertainties are not concealed.
  
If necessary, the metadata of the transcriptions can provide more detailed information on the extent to which phenomena are included or not.
  
###  Transcription metadata
  
  
In addition to the metadata mentioned above, the header of the transcription file contains short information about the manuscript in the `<msDesc>` element within the `<sourceDesc>` section, which includes at least the `<msIdentifier>` element. The element receives its own `@xml:id`, which is read e.g. for the identification of the manuscript during collation. If several scribes can be identified in a manuscript, it is also useful to briefly describe these scribes in the `<handNote>` element within a `<handDesc>` subsection in another section `<physDesc>`, which serves to describe the physical nature of the manuscript. The attribute `@xml:id` is referenced in the edition as an identifier and must be set in any case; in addition, other attributes are available, e.g. the attribute `@scribe` can be used if the scribe is known by name.
  
For example, if the handwriting is a marginal catena, the layout can be described in the same section in the `<objectDesc>` within the `<layoutDesc>` element.
  
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
  
###  Edition of the transcription
  
  
The entire transcription is in the `<text>` part of the file in a `<div>` element. The element has the following attributes:
- `@type="edition"`
- `@xml:lang` indicating the language of the edited text using [ISO 639-2](https://www.loc.gov/standards/iso639-2/php/code_list.php ).
- `@n` indicating the URN of the file, see [below](#file-structure-of-each-edition ).
  
####  Mark-up of the structure of the text
  
  
Within this section, at least one subsection `<div>` with the attribute `@type="textpart"` is to be used, whereby the attribute `@subtype` may take the following values: `section` for continuous texts, `fragment` for fragmentary transmission, `commented` and `commentary` for commentaries or comparable texts where a distinction is made between a commented and a commentary text.
  
In the case of a catena, for example, this may look like this:
  
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
  
The text is further subdivided by the element `<seg>` (or in the case of individual words by `<w>`) to which an `@xml-id` is also assigned in each case in order to be able to mark the references between the corresponding parts (text, commentary), while the referencing (commenting) element (`<seg>` or `<p>`) receives an attribute `@corresp`.
  
In addition, the attribute `@ana` can be used for comments (`@subtype='commentary'`) to provide information on the location of the corresponding comment part on the page or its categorization. Possible values are: `marginal`, `interlinear`, `intercolumn`, `scholia`, `hexaplaric`; other values are allowed if necessary. 
  
In the transcription, the `<milestone>` element can be used to refer to structuring of the text (specified using the `@unit` and `@n` attributes) by editions (specified using `@edRef`):
  
```xml
<div type="textpart" subtype="section" n="1">
  <p>
  <milestone unit="section" edRef="#Whittaker" n="1"/>Text
  </p>
</div>
```  
  
For editions that exist in the PTA, the value of the `@edRef `attribute is the URN of the edition (e.g. `urn:cts:pta:pta0001.pta028.pta-grcBibex`), otherwise the `@xml:id` of a bibliographic entry in the `<teiHeader>` should be referenced.
  
The division of the transcripted text is following the division in the manuscript and not the artifical modern divisions introduced by editions.
  
####  Punctuation
  
  
The punctuation is transcribed - without explicit marking - according to the manuscript.
  
####  Title and title-like elements
  
  
Titles are marked with the element `<title>` within the element
`<head>`:
  
```xml
<head>
 <title>Τοῦ αὐτοῦ ὁμιλία</title>
</head>
```  
  
  
####  Line, column, page, gathering beginnings
  
  
Line beginnings are marked with `<lb/>`, column beginnings with `<cb/>`, page beginnings with `<pb/>` and gatherings beginnings with `<gb/>.`
  
If there is a break within a word, the respective element receives the attribute `@break` with the value `no`. There is no space between the parts of the word and the element.
  
At the beginning of the page (and possibly also at the beginning of the gathering), the element receives the attribute `@n` for entering the page numbering and - where available - the attribute `@facs` for entering the link to a digital facsimile.
  
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
  
Where possible, a full-resolution URL of the image provided through [IIIF](https://iiif.io/ ) protocol should be used, as in the example. This is folio 227r of Codex Atheniensis 253, the digital copy of which is made available by the EBE at https://digitalcollections.nlg.gr/nlg-repo/dl/en/browse/3001; f. 227r is image 455, the full-screen URL of which https://digitalcollections.nlg.gr/iiif/3001/EBE0253455.tif/full/full/0/default.jpg can easily be found, for example, with the help of the browser plug-in [Dezoomify](https://dezoomify.ophir.dev/ ), which outputs the IIIF image API address https://digitalcollections.nlg.gr/iiif/3001/EBE0253455.tif/info.json. The image URL is then obtained by replacing `info.json` with [{region}/{size}/{rotation}/{quality}.{format}](https://iiif.io/api/image/3.0/#4-image-requests ), in the given case `full/full/0/default.jpg`. Some libraries such as the BNF, for example, provide the image URL themselves in their [IIIF viewers](https://gallica.bnf.fr/view3if/ ) via the export function.
  
If the owning library makes digitised material available only in its own reader (such as the BML Firenze or the British Library London for example), the corresponding URL of the facsimile of a page should be linked, if available.
  
####  Paragraphs
  
  
Paragraphs - as far as they are marked in the manuscript (e.g. by a gap) – are marked with the element `<p>`. Each transcription consists of at least one paragraph.
  
####  Lists
  
  
Lists (e.g. of names or tables of contents), if they are represented as such in the manuscript, are marked with the element `<list>`, the individual list entries with the element `<item>`. If a list has a highlighted heading, it is marked with the help of the element `<head>`.
  
####  Initials and Ektheseis
  
  
Initials and ektheseis are marked with the element `<hi>`. In the attribute `@rend` it is indicated whether it is an `initial` (spanning several lines) or an `ekthesis` (ekthesis).
  
```xml
<hi rend="ekthesis">θ</hi>ησαυροὶ, ψυχὰς εὐφραίνοντες·
```  
  
  
####  Other highlighting
  
  
*Rubricated* text is also marked up with the element `<hi>`; the attribute `@rend` receives the value `rubricated`.
  
Text highlighted with a *line above* the letter or word is marked up with `<hi rend="overline">`.
  
*Underlined* text is marked up with `<hi rend="underline">`.
  
Text in capitals (for example the lemmata in commentaries) is martked up with `<hi rend="majuscule">`.
  
####  Marginalia
  
  
Marginalia are marked in the transcription as `<note>`, the element being introduced in the text as close as possible to the place where the marginalia is found.
  
The position is specified in the `@place `attribute. Permitted values are `top` (if necessary, specified in more detail: `top_inner`, `top_center`, `top_outer`), `bottom` (`bottom_inner`, `bottom_center`, `bottom_outer`), `margin_inner`, `margin_outer` and `intercolumn`.
  
If a note does not originate from the scribe, this can be indicated by the attribute `@hand`, whereby the correctors should be distinguished (`#m2`, `#m3`, … - generally `#mr` for *manus recentior*; for the indication of hands in the metadata see [above](#transcription-metadata )). If it is not possible to decide by which hand a note has been made, the attribute is assigned the value `unknown`.
  
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
  
  
####  Deleted text
  
  
Text deleted by the writer or a later corrector is marked with `<del>`. The type of deletion is specified in the `@rend` attribute. Permitted values are `erasure`, `strikethrough`, `overwrite` and `expunction`.
  
If a deletion does not originate from the scribe, this can be indicated by the attribute `@hand`, whereby the correctors should be distinguished (`#m2`, `#m3`, … - generally `#mr` for *manus recentior*; for the indication of hands in the metadata see [above](#transcription-metadata )). If it is not possible to decide by which hand a correction has been made, the attribute is assigned the value `unknown`.
  
```xml
γηΐ<del rend="erasure" hand="#m2">ω</del>νων
```  
  
  
####  Corrections
  
  
Corrections (words, but also individual letters) are marked with the `<subst>` element.
  
If a correction does not originate from the scribe, this can be indicated by the attribute `@hand`, whereby the correctors should be distinguished (`#m2`, `#m3`, … - generally `#mr `for *manus recentior*, for the indication of hands in the metadata see [above](#transcription-metadata )). If it is not possible to decide by which hand a correction has been made, the attribute is assigned the value `unknown`.
  
Within this element, the deleted *text* is marked with `<del>`. The type of deletion is specified in the `@rend` attribute. Permitted values are `unmarked` (the text to be replaced is not explicitly marked at all), `marker` (the text to be replaced is marked with a character, e.g. an obelus or similar), `erasure`, `strikethrough`, `overwrite` and `expunction`.
  
The *added text* is marked with `<add>`. The place of the addition is specified with the help of the `@place` attribute. Permitted values are `above`, `below`, `inline` and `margin`.
  
```xml
<subst hand="#m2">
 <del rend="erasure">ἀναλόγως</del>
 <add place="above">παραλόγως</add>
</subst>
```  
  
If the correction is the addition of diacritics to a letter, the letter without is marked with  `<del>` and the attribute `@rend` with the value `repurposed`, the letter with the added diacritic is marked with `<add>` and the attribute `@rend` with the value `inline`.
  
```xml
<subst>
    <del rend="repurposed">α</del>
    <add rend="inline">ά</add>
</subst>
```  
  
If the correction is an overwriting or retracing of the original text without correction (change in text), it is better to use the element `<retrace>`:
  
```xml
ἴσως ἂν ἐνομίσθη <retrace>παρέλκον. ἀνάγραπτον</retrace> τούτων ποιεῖσθαι
```  
  
####  Added text
  
  
Added text that is not accompanied by a correction is marked with the `<add>` element. The location of the addition is specified in the `@place` attribute. Permitted values are `above`, `below`, `inline` and `margin`.
  
If a correction does not originate from the scribe, this can be indicated by the attribute `@hand`, whereby the correctors should be distinguished (`#m2`, `#m3`, … - generally `#mr `for *manus recentior*; for the indication of hands in the metadata see [above](#transcription-metadata )). If it is not possible to decide by which hand a correction has been made, the attribute is assigned the value `unknown`.
  
```xml
<add place="above" hand="#m2">hinzugefügter Text</add>
```  
  
  
####  Unreadable text
  
  
Unreadable text is specified with the self-closing element `<gap>` (for other uses of this element, see [the next entry](#gap-in-the-text )). The attribute `@reason` is assigned the value `illegible`. The (estimated) size (`@quantity`) is given in letters (`@unit="character"`), if necessary lines (`@unit="line"`).  
  
```xml
<gap reason="illegible" quantity="10" unit="character"/>
```  
  
  
####  Gap in the text
  
  
A gap in the text is also indicated with the `<gap>` element. The attribute `@reason` is in this case assigned the value `damage` (physical damage) or `fenestra` (left blank by the writer). The (estimated) amount (`@quantity`) is indicated in letters, lines or pages (`@unit` with value `character`, `word`, `line` or `page`). 
  
```xml
<gap reason="fenestra" quantity="10" unit="character"/>
```  
  
  
If, however, a gap has been created by the destruction of text by the scribe (sc. erasure: `@rend="erasure"`), it is marked with the element `<del>`; if necessary, in the case of destruction by another hand, the attribute `@hand` is to be indicated, whereby the correctors should be distinguished (`#m2`, `#m3`, … - generally `#mr `for *manus recentior*; for the indication of hands in the metadata see [above](#transcription-metadata )). If it is not possible to decide by which hand a correction has been made, the attribute is assigned the value `unknown`.
  
```xml
<del rend="erasure" hand="#m2">
 <gap reason="illegible" quantity="10" unit="character"/>
</del>
```  
  
  
####  Unclear reading
  
  
If a text cannot be deciphered with certainty, it is marked with the `<unclear>` element. The attribute `@reason` indicates the reason for the uncertain reading by the values `damage` (physical damage), `illegible` (not readable) or `retraced` (text traced). How secure the reading is is indicated by means of the attribute `@cert`, which can take the values `low` and `high`.
  
```xml
<unclear reason="illegible" cert="high">ἄνθρωπον</unclear>
```  
  
  
####  Change of scribe
  
  
If the writer changes in the text, the `<handShift/>` element is inserted at the position of the change. The scribe can be identified by the attributes `@medium` (characteristic of the ink or the writing material used), `@scribeRef` or `@scriptRef`, whereby for the latter attributes reference should be made to the corresponding `@xml:id` in the `<teiHeader>` (`<handDesc>`, see [above](#transcription-metadata )).
  
```xml
<pb n="228r"/>
<handShift scribeRef="#m2"/>ὃς φησὶ πρὸς αὐτόν· κορ<lb break="no"/>νήλιε·
```  
  
  
####  Nomina sacra
  
  
Nomina sacra *can be* marked-up. For this purpose, within a `<choice>` element, the abbreviation is included in the element `<abbr>` with the attribute `@type` of the value `nomSac` and the expanded form is noted in the `<expan>` element.
  
```xml
<choice>
    <expan>πνεύματι</expan>
    <abbr type="nomSac">
       <hi rend="overline">πνι</hi>
    </abbr>
</choice>
```  
  
  
####  Other abbreviations
  
  
Other abbreviations are encoded similar to the nomina sacra. For this purpose, within a `<choice>` element, the abbreviation is included in the element `<abbr>` with the attribute `@type` of the value `suspension` and the expanded form is noted in the `<expan>` element.
  
> The BBAW deliberately refrains from noting other abbreviations for the most part for reasons of practicability and the time required otherwise.
  
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
  
  
####  Numbers
  
  
Numbers are marked with the element `<num>`.
  
```xml
<num>ΛΓ</num>
```  
  
  
####  Diple and Paragraphos
  
  
Quotations in manuscripts are often marked with a diple (single or double) in the margin. They are noted in the transcription with the help of `<g type="diple"/>` or `<g type="doubled_diple"/>.` (The `<quote>` element is *not* used in the transcription!)
  
```xml
<lb/><g type="diple"/>προσέχετε φησὶ λαός μου τῶι νόμωι μου· κλίνατε τὸ οὖς ὑμῶν εἰς τὰ ῥήματα
<lb/><g type="diple"/>τοῦ στόματός μου· ἀνοίξω ἐν παραβολαῖς τὸ στόμα μου φθέγξομαι προβλήματα
<lb/><g type="diple"/>ἀπ αρχῆς· εἶτα διδάσκων πόθεν ταῦτα μεμάθηκεν· ὅσα ἠκούσαμεν φησὶ καὶ
```  
  
  
Lines marked in the manuscript with a paragraphos in the margin are noted using `<g type="paragraphos"/>`.
  
##  Critical Edition
  
  
###  Metadata of the critical edition
  
  
####  Handwritten witnesses and earlier editions
  
  
In addition to the [metadata mentioned above](#building-a-digital-edition-according-to-tei ), the header of the file for the edition contains a list of the manuscripts used within the section `<sourceDesc>` in a subsection `<listWit>`. The information on the individual manuscripts is provided with the help of the element `<witness>`. The transcription of the manuscript should be linked in the attribute `@corresp` (in the form of its URN, see [below](#file-structure-of-each-edition )).
  
All entries receive a machine-readable ID in the `@xml-id` attribute, to which a human-readable siglum, which may also contain further formatting, corresponds in the `<witness> `subordinate element `<abbr type="siglum">`.
  
If the manuscript is a copy of another manuscript, the `xml:id` of this manuscript is linked in the `@source` attribute. This makes it possible to eliminate a manuscript marked in this way (and all text variants attested by it), e.g. for presentation, but also for analysis by a transformation script.
  
The usual Latin name of the manuscript is given in the `<name>` element, the date of the manuscript in the `<origDate>` element (if necessary, additionally machine-readable using the attributes `@notBefore` and `@notAfter` or `@when`), and the folia or pages on which the edited text is located are indicated in the element `<locus>` (if necessary, machine-readable using the attributes `@from` and `@to`).
  
If a more detailed description of the manuscript is necessary or desired, e.g. because an edition of an author’s work is being compiled and manuscripts are relevant to several texts for this reason, it makes sense to outsource this to a separate file, using as fully as possible the elements described in the [TEI Guidelines in the chapter “Manuscript Description”](https://tei-c.org/release/doc/tei-p5-doc/en/html/MS.html ), and then to refer to them in the `@key` attribute of the `<name>` element.
  
> For the editions produced at the BBAW, such manuscript descriptions (focussed on the content) are created as standard, which are listed under unique manuscript IDs on [https://pta.bbaw.de/manuscripts/](https://pta.bbaw.de/manuscripts/ ); those IDs are used as value for `@key`.
  
Manuscript families and hyparchetypes can be combined within the section `@listWit` in a separate subsection `<listWit>` with its own element `<head>`, which gets its own machine-readable ID for the family in the attribute `@xml:id` (and analogously a human-readable siglum in the element `<abbr type="siglum">`). These could be also used in the attribute  `@wit` of a reading; it is advised, though, to refrain from that, but rather to use the sigla of the respective individual manuscripts to avoid errors. Group sigla could be produced in the course of generating print or web presentations.  
  
Indirect tradition or ancient as well as modern translations should also be noted in this way if they are to be referred to in the apparatus entries of the edition.
  
```xml
<listWit>
 <listWit xml:id="a">
  <head>Hyparchetyp <abbr type="siglum">α</abbr>
  </head>
  <witness xml:id="La" corresp="pta0013.pta003.pta-MsLa.xml">
    <abbr type="siglum">La</abbr>
    <name corresp="388.1418.0412.xml">Laurentianus Plut. IV 12</name>
    <origDate notBefore="1401" notAfter="1500">s. XV</origDate>
    <locus>f. 131v–133v</locus>
  </witness>
  <witness xml:id="Vi" source="#La" corresp="pta0013.pta003.pta-MsVi.xml">
    <abbr type="siglum">Vi</abbr>
    <name corresp="1297.1341.0190.xml">Vindobonensis theol. gr. 190</name>
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
  
  
Corresponding to the listing of manuscripts in a subsection `<listWit>` within the section `<sourceDesc>`, earlier editions are each listed in a subsection `<listBibl>` in the element `<bibl>` (or `<biblStruct>`):
  
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
  
  
Authors of conjectures that cannot be bibliographed in the above sense because, for example, the conjectures were transmitted orally or they are cited in another edition, are included as follows:
  
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
  
  
####  Encoding of biblical references
  
  
In the `<encodingDesc>` section, a further element `<refsDecl>` with the attribute `@xml:id` of the value `biblical` specifies in machine- and human-readable form the system according to which biblical passages are referenced and how these references can be resolved. 
  
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
  
  
The abbreviations used in the PTA for the books of the Old Testament (LXX) are:
  
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
  
The abbreviations used in the PTA for the books of the New Testament are:
  
```txt
Mt, Mk, Lk, Jn, Act, Rom, 1Cor, 2Cor,
Gal, Eph, Phil, Col, 1Th, 2Th, 1Tim,
2Tim, Tt, Phm, Heb, Jak, 1P, 2P, 1Jn,
2Jn, 3Jn, Jud, Rev.
```  
  
The passages are formed as follows: Biblical corpus (LXX, Hexapla, Vg [= Vulgata] or NA [= Nestle-Aland]):Book:Chapter:Verse (e.g.: 1,1-2,1.4), e.g. `LXX:Gn:1:1-3`.
  
####  Indication of the encoded phenomena
  
  
Also in the `<encodingDesc>` section, the `<editorialDecl>` section within the `<interpretation>` subsection elaborates on which phenomena have been marked up in the text and to what extent. This allows users of the edition to quickly see what to expect from the edition. Adjustments to `@ana` and to the text are to be made accordingly.
  
```xml
<editorialDecl>
  <interpretation>
    <p>This file is encoded according to the guidelines of the Patristic Text Archive (PTA). See https://pta.bbaw.de/project/encoding-guidelines and https://doi.org/10.5281/zenodo.3737666.</p>
    <p xml:id="biblical-quotations"
       ana="fully/partially/not-annotated fully/partially/not-identified">Biblical quotations are fully/partially annotated and/but not fully/partially referenced. References follow the scheme declared <ref target="#biblical">above</ref>. 
             </p>
    <p xml:id="places"
       ana="fully/partially/not-annotated fully/partially/not-identified">Places are fully/partially annotated and/but not fully/partially referenced with <ref target="https://pleiades.stoa.org/">Pleiades Gazetteer</ref> IDs.</p>
    <p xml:id="persons"
       ana="fully/partially/not-annotated fully/partially/not-identified">Persons are fully/partially annotated and/but not fully/partially referenced with IDs according to the <ref target="https://github.com/PatristicTextArchive/tipnr_data">TIPNR - Tyndale Individualised Proper Names with all References</ref> list for biblical persons and IDs of <ref target="https://github.com/PatristicTextArchive/pta_metadata/blob/main/pta_persons.json">PTA persons index</ref> for all other persons.</p>
    <p xml:id="groups"
       ana="fully/partially/not-annotated fully/partially/not-identified">Groups of persons and organisations are fully/partially annotated and/but not fully/partially referenced with IDs according to the IDs of <ref target="https://github.com/PatristicTextArchive/pta_metadata/blob/main/pta_groups.json">PTA groups index</ref> for all other groups.</p>
 </interpretation>
  ...
</editorialDecl>
```  
  
The annotation status is defined as follows:
  
- `fully-annotated`: All instances of a phenomenon (e.g. biblical quotations, persons, places) are encoded with the respective element.
- `partially-annotated`: Some instances of a phenomenon (e.g. biblical quotations, persons, places) are encoded with the respective element.
- `not-annotated`: No instance of a phenomenon (e.g. biblical quotations, persons, places) is encoded with the respective element.
  
The extension to which the annotations are identified with norm data is defined as follows:
  
- `fully-identified`: All encoded instances of a phenomenon (e.g. biblical quotations, persons, places) are identified with the respective norm data.
- `partially-identified`: Some encoded instances of a phenomenon (e.g. biblical quotations, persons, places) are identified with the respective norm data.
- `not-identified`: No encoded instances of a phenomenon (e.g. biblical quotations, persons, places) are identified with the respective norm data.
  
  
####  Normalisation
  
  
Within the `<editorialDecl>` section, the `<normalisation>` and `<punctuation>` subsections describe the extent to which the handwritten text has been normalised in the critical edition. Adjustments are to be made.
  
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
  
####  Type of encoding of the variants
  
  
The last element in the `<encodingDesc>` section is the type of marking up of the text-critical variants. The entry *must* read:
  
```xml
<variantEncoding method="parallel-segmentation" location="internal"/>
```  
  
  
####  Type of edition
  
  
Within the `<profileDesc>` section, the type of edition is provided in the  `<textClass>` subsection in `<keywords scheme="#editionstatus">`. The element `<term>` has one of the following phrases:
  
-   `critical-edition` for a critical edition in which the text-critical variants have been coded. This should be the normal case for new editions that follow the model presented here.
  
-   `critical-edition-no-app` for a critical edition in which the text-critical variants have not been encoded, e.g. because it is a retro-digitisation of a printed critical edition and for copyright reasons the apparatus cannot be included in the retro-digitisation.
  
-   `critical-edition-outdated` for an edition that notes text-critical variants but does not, for example, comprehensively include the manuscripts.
  
-   `pre-critical-edition` for pre-modern editions (e.g. in the Patrologia Graeca or Latina).
  
A special case is `metacritical-edition-with-app`, which is used for the [SBLGNT edition](https://www.sblgnt.com/ ) of the New Testament.
####  Status of edition
  
  
Finally, the element `<revisionDesc>` receives an attribute `@status`, in which the status of the edition is specified. The following values are possible:
- `draft`: Draft version, work in progress
- `unfinished`: Work not yet finished, for example annotations need to be done
- `approved`: Approved (final) version
  
###  Edition
  
  
The entire critical edition is in the `<text>` part of the file. It consists of at least one element `<div>`, which contains the edited text. The element has the following attributes:
- `type="edition"`
- `@xml:lang` indicating the language of the edited text using [ISO 639-2](https://www.loc.gov/standards/iso639-2/php/code_list.php )
- `@n` indicating the URN of the file, see [below](#file-structure-of-each-edition ).
  
```xml
<div type="edition" xml:lang="grc" n="urn:cts:pta:pta0007.pta010.pta-grcBibex">
<!-- Text der Edition -->
</div>
```  
  
  
In new editions, the edition should be preceded by a section `<div type="praefatio">` with the praefatio.
  
####  Praefatio
  
  
The Praefatio offers in a continuous text everything that is necessary for understanding the following text and its tradition. Above all, the critical value of the manuscripts and their mutual relationship to each other should be explained, ancient translations and other indirect transmission as well as earlier editions and translations into modern languages should be mentioned and appreciated in their critical value.
  
In principle, it makes sense to link the information given in the `<teiHeader>` by using the element `<ref>` and the attribut `@target`.
  
Subsections can be set up using `<div type="section" n="1">`, which can also contain their own headings in a `<head>` element.
  
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
  
For footnotes the element `<note>` is used. Bibliographic data that is not already defined in the `<teiHeader>` can be given at point by using the element `<bibl>`;  the attribut `@xml:id` may be used to reference entries like those. It is also possible to reference the text (or variants), if a `@xml:id` is provided with the respective element (for example `<seg>`, `<app>` or `<rdg>`). Lists may also be used.
  
####  Text
  
  
#####  Encoding of the structure of the text
  
  
Within the element `<div type="edition">` the text structure reconstructed by the editor (according to the specifications in the `<refsDecl n="CTS">` in the `<teiHeader>`) is distinguished with the help of (also nested) subsections `<div>` of `@type="textpart"`, whereby the following values are possible for the attribute `@subtype`:
  
-   Part: `<div type="textpart" subtype="part" n="1">`
  
-   Book: `<div type="textpart" subtype="book" n="1">`
  
-   Homily: `<div type="textpart" subtype="homily" n="1">`
  
-   Chapter: `<div type="textpart" subtype="chapter" n="1">`
  
-   Subdocument:
    `<div type="textpart" subtype="subdok" n="1">`
  
-   Praefatio (non-numbered preface in the text):
    `<div type="textpart" subtype="praefatio" n="praefatio">`
  
-   Section: `<div type="textpart" subtype="section" n="1">`
  
-   Fragment:
    `<div type="textpart" subtype="fragment" n="1">`
  
-   Testimonium:
    `<div type="textpart" subtype="testimonium" n="1">`
  
-   Commented text:
    `<div type="textpart" subtype="commented" n="Gen_1_1">`
  
-   Commentary:
    `<div type="textpart" subtype="commentary" n="Gen_1_1">` (cf. [above](#mark-up-of-the-structure-of-the-text ))
  
The `@n` attribute receives the reference indicator (which is used for citing the respective passage), usually a number, but text like “pr”, “hypopsalmos”, “hypothesis”, “perioche” etc. are also possible. Please note that the attribute may not contain whitespace, but only letters, numbers, symbols and punctuation signs.
  
Paragraphs within these subsections are marked with the help of the `<p>` element. Each `<div>` element contains at least one `<p>` element. Lists are also allowed: They are marked (instead of `<p>`) with the element `<list>`,  the individual list entries with the element `<item>`. If a list has a heading,  it is marked with the help of the element `<head>`.
  
#####  Marking up further structural elements
  
  
The page breaks in the manuscripts and earlier editions are indicated as required by means of the `<pb>` element; the page reference is in the `@n` attribute and the manuscript or edition is referred to in the `@edRef` attribute:
  
```xml
<pb n="126r" edRef="#La"/>
```  
  
  
#####  Encoding of biblical and other quotations (and allusions)
  
  
Quotations are marked with the help of the `<quote>` element and can be given a `@type` attribute so that a distinction can be made between `marked` and `unmarked` quotations; for paraphrased quotations - insofar as they are marked as quotations at all - the value `paraphrase` can be used. In editions of biblical commentaries, lemma quotations are given the value `lemma` to differentiate them from other quotations.
  
Explicit quotations citing the author of the quotation are marked with the element `<cit>` and the phrase in it leading the quotation is marked with the element `<ref>`. Insertions in the quotation (such as “said”) are marked with the help of `<seg type="insertion">` within the quotation.
  
Allusions (e.g. to biblical stories and events) are marked with the help of `<seg type="allusion">`.
  
Pseudo-quotations can be marked with the help of `<seg type="psq">`.
  
For bible quotations, the respective bible passage is given within the `<ref>` element with reference to the specifications in the `<teiHeader>` (`@decls="#biblical"`) in the `@cRef` attribute.
  
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
  
If non-biblical texts are cited, the passage reference is also indicated by means of the `<ref>` element: If the referenced text is available in the Patristic Text Archive, the PTA-URN is given with reference to the specifications in the `<teiHeader>` (`@decls="#pta"`) in the attribute `@cRef`. If the referenced text is present in the [Perseus Digital Library](https://scaife.perseus.org/ ), the CTS-URN with reference to the specifications in the `<teiHeader>` (`@decls="#perseus"`) is given in the attribute `@cRef`. If the referenced text is not available in either repository, the reference for the referenced text is given in the attribute `@source` in the form “Authorabbrev_Workabbrev_Location”; ancient Greek authors should be referenced according to the lists of [H. G. Liddell/R. Scott/H. S. Jones, A Greek - English Lexicon, Oxford ^9^1968](https://lsj.gr/wiki/Index:AuthorsWorks/All ) and G. W. H. Lampe, A Patristic Greek Lexicon, Oxford ^3^1987, for Latin ones the abbreviations of the Thesaurus Linguae Latinae (cf. [Index librorum scriptorum inscriptionum ex quibus exempla afferuntur](https://thesaurus.badw.de/en/tll-digital/index/ )) should be used, with dots in the abbreviations deleted without replacement.
  
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
  
#####  Encoding of similia and sources
  
  
Similia are marked up with the help of `<seg type="similar">`, sources (as far as it is not a citation) with the help of `<seg type="source>`. The source is indicated within the `<seg>` element in a `<ref>` element.
  
```xml
<seg type="similar">
ἵνα εἰς βάθος διαδῷ τὴν οἰκείαν ἐνέργειαν ἡ βαφή
<ref decls="#pta" cRef="urn:cts:pta:pta0022.pta003.pta-grc1:12.1"/>
</seg>
```  
  
  
#####  Encoding of direct speech
  
  
Direct speech is marked up with the help of the `<said>` element.
  
```xml
<p>
καὶ μή μοι λέγε· 
<said>οὐκ ἔσχε καιρὸν πολιτεύσασθαι καλῶς.</said>
</p>
```  
  
#####  Encoding of dialogue
  
  
Dialogue is marked up with the help of `<sp>` (instead of `<p>`). For the person speaking `<speaker>` is used, the spoken text is marked up with `<p>`.
  
@import “examples/ed_speech.xml” {class=“lines-numbers”}
  
#####  Encoding of people, organisations and places
  
  
**Persons** are marked up with the help of the element `<persName>`. In the case of biblical persons, the attribute `@type` with the value `biblical` is used, all other persons do not receive an attribute `@type`. In the attribute `@key`, the `person_id` in the [PTA person list](https://github.com/PatristicTextArchive/pta_metadata/blob/main/pta_persons.json ) is specified, which in turn draws on the list [“Translators Individualised Proper Names with all References”](https://github.com/tyndale/STEPBible-Data ) as well as its own register of non-biblical persons. Non-biblical persons who are missing from the PTA register can be added after [consultation](mailto:annette.von_stockhausen@bbaw.de ).
  
**Institutions (such as synods or theological groupings), peoples and other groups** are marked up using the `<orgName>` element. In the attribute `@key`, the `org_id` of the [PTA organisations list](https://github.com/PatristicTextArchive/pta_metadata/blob/main/pta_orgs.json ) is specified. Organisations that are missing from the PTA register can be added after [consultation.](mailto:annette.von_stockhausen@bbaw.de )
  
**Places** are marked with the help of the element `<placeName>`, in the attribute `@ref` the ID of the [Pleiades Gazetteer](https://pleiades.stoa.org/ ) (using the URL) is referred to. 
  
```xml
<p>
ἐπίσκοπον <persName key="PTA_P00012">Βασίλειον</persName> 
καὶ <orgName key="PTA_O00001">τὴν ἁγίαν σύνοδον τῶν πατέρων τῶν 
ἐν <placeName ref="https://pleiades.stoa.org/places/511268">Νικαίᾳ</placeName> 
σύνοδον</orgName>. 
τοίνυν ὁ <persName type="biblical" key="Adam_Gen.2.19">Ἀδὰμ</persName>
</p>
```  
  
  
#####  Text witnesses
  
  
The manuscripts witnessing the text are documented in the element `<app>` with the attribute `@type="witnesses"`. The element receives a unique identifier in the attribute `@xml:id`, in the attribute `@prev` or `@next` reference is made to the corresponding entry (`<witStart/>`/`<lacunaStart/>` -> `<witEnd/>`/`<lacunaEnd/>` and vice versa). If necessary, a reference to a corresponding text-critical variant or reading can be made in the attribute `@corresp`.
The element contains only the element `<rdg>` with the attribute `@wit`, in which one of the self-closing elements `<witStart/>` (= beginning of a witness), `<witEnd/>` (= end of a witness), `<lacunaStart/>` (= beginning of a gap) or `<lacunaEnd/>` (= end of a gap) is inserted. The element does not contain any text, but is inserted (comparable to a milestone element like `<pb>`) at the appropriate place in the text: In the case of `<witStart>` and `<lacunaEnd>` it comes before the first word present in the witness or after the gap ends, in the case of `<witEnd>` and `<lacunaStart>` it comes after the last word present in the witness or before which the gap begins. 
  
```xml
<app type="textcritical">
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
  
(This somewhat awkward way of notation is necessary because according to the [TEI Guidelines](https://tei-c.org/Vault/P5/2.0.0/doc/tei-p5-doc/en/html/ref-model.rdgPart.html ) the elements `<witStart/>`, `<lacunaStart/>`, `<witEnd/>`, `<lacunaEnd/>` are only allowed to be inside a `<rdg>` or `<lem>` in an `<app>` and the sensible [amendment request to allow these elements also outside in the text was rejected by the TEI Technical Council](https://github.com/TEIC/TEI/issues/301 ).)
  
  
#####  Encoding the variants
  
  
The encoding of the variants reflects the editorial decisions made in the editing process, especially the assessment of the variants and the stemmatic contexts, and is *not a* neutral description of the surviving material, but an interpretation of it.
  
At each point in the text that has survived in different versions, the variants are indicated within the `<app>` element, which has an `@type` attribute with the value `variants`. Within this element `<app>`, the reconstructed text is marked with the element `<lem>`, the variants judged to be secondary with the element `<rdg>`, whereby this element may occur more than once within an `<app>` entry, in contrast to `<lem>`. All types of variant transmission described below presuppose an assessment of the individual variants as primary (`<lem>`) or secondary (`<rdg>`).
  
*All* variant witnesses are indicated in the `<lem>` and in the `<rdg>` elements in the attribute `@wit`, if the variant is in a manuscript, or in the attribute `@source` or `@resp`, if the variant goes back to a conjecture in an edition or by a person.
  
In the case of a printed edition, one would thus speak of a positive apparatus, with the particularity that in the case of the digital critical edition, the readings of codices descripti are also indicated. The step of elimination or the reduction of the positive apparatus to a negative apparatus can, but does not have to, be carried out when preparing the data for presentation (in print or online). The categorical difference between the traditional critical edition in print and the critical digital edition lies in this distinction between the complete recording of data, which makes the traceability and verifiability of editorial decisions possible to a much greater extent than before, and, if necessary, selective presentation.
  
The values of the elements `@wit`, `@source` and `@resp` refer to the values of the attribute `@xml:id` of the element `<witness>`, `<bibl>` or `<person>` specified in the element `<sourceDesc>` (in the `<teiHeader>`, [see above](#handwritten-witnesses-and-earlier-editions )).
  
To increase readability for human recipients of the edition, all variant carriers within the `@wit` attribute should be presented in a consistent order (and taking stemmatic relationships into account).
  
In the case of several variants within an `<app>` element, the various `<rdg>` entries should be ranked in such a way that the closer they are stemmatically (according to the editor’s assessment) to the `<lem>` variant, the earlier they are listed.
  
Variants (`<lem>` and `<rdg>` or several `<rdg>` entries) that are considered to belong together in their genesis or otherwise can be placed in one element `<rdgGrp>` for clarification.
  
The text of the variation shall always be given in its full text and shall not be abbreviated under any circumstances.
  
#####  Analysis of the causes for the variation
  
  
Variants can have an attribute `@cause`, with the help of which the editor provides the recipient of the edition with an analysis of the probable cause for the variant and which can thus also be easily filtered for presentation. The following values of this attribute are possible:
  
-   `orthographic`, when a variant is interpreted by the editor as affecting only the spelling, i.e., in the case of Greek manuscripts, for example, as most likely being due to itacism.
-   `homoioteleuton` or `homoiarkton` or `saut_du_meme` if, in the opinion of the editor, a variant is due to homoioteleuton or homoiarkton or a saut du même au même.
-   `dittography`, when a variant is interpreted as a dittography.
  
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
  
  
#####  Typification of variants
  
  
The results of the analysis of the type of a variant is given in the `@type` attribute.
  
######  Additions
  
  
Additions, including dittographies and other repetitions, are marked in the `<rdg>` element as `<@type="addition">`. The `<lem>` element remains without text content (“self-closing”).
  
```xml
<app type="variants">
 <lem wit="#Pt #Pc #Pd #Ma #My"/>
 <rdg wit="#Ha #Pa #Be" type="addition">καὶ περὶ τοῦ ἁγίου πνεύματος</rdg>
 <rdg wit="#Pb #Va" type="addition">λόγος πάνυ ὠφέλιμος</rdg>
</app>
```  
  
  
######  Omissions
  
  
Omissions are marked as `<@type="omission">`. The `<rdg>` element remains without text content (“self-closing”).
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha">ἀπεικάζεται καὶ</lem>
 <rdg wit="#Pt #Pc #Pd #Ma #My #Ab" type="omission"/>
</app>
```  
  
  
######  Deletions
  
  
Deletions are marked as `<@type="deletion">`, whereby (in contrast to the transcription) it is no longer differentiated how the text was deleted, since this information can be taken from the transcription file at any time.
  
Deletions are analytically distinguished from omissions by the fact that they are due to a deliberate intervention by the writer of the respective manuscript. The `<rdg>` element is again without textual content (“self-closing”).
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">καὶ</lem>
 <rdg wit="#Pb" type="deletion"/>
</app>
```  
  
  
######  Not readable text
  
  
Unreadable text is marked as `<@type="illegible">`. The element `<rdg>` is without text content (“self-closing”).
  
```xml
<app type="variants">
 <lem wit="#Pt #Pc #Pa #Be #Pb #Pd #Ma #My #Va #Ab">καὶ</lem>
 <rdg wit="#Ha" type="illegible"/>
</app>
```  
  
######  Gap in text of a manuscript
  
  
A gap im text of a manuscripts is (following the rules for transcription) marked as `<@type="damage">` (damage) als `<@type="fenestra">` (intentional gap) oder als `<@type="deletion">` (deleted). The element `<rdg>` is without text content (“self-closing”).
  
######  Transpositions
  
  
Transpositions are marked as `<@type="transposition">`. In the `<rdg>` element, the transposed text is reproduced in its full wording (sc. not abbreviated).
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha">τὰ τοῦ θεοῦ</lem>
 <rdg wit="#Pt #Pc #Pd #Ma #My #Ab" type="transposition">τοῦ
   θεοῦ τὰ</rdg>
</app>
```  
  
  
Rearrangements that affect longer passages of text - especially if they span structural units - are marked as omissions and additions, with both `<app>` elements each receiving an `@xml:id` attribute and referencing the other using the `@prev` and `@next` attributes.
  
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
  
  
######  Corrections by scribe
  
  
Corrections of the text by the scribe or a later corrector are distinguished in such a way that the order of the different stages of transmission is indicated in the `<rdg>` element with the help of the `@varSeq` attribute.
  
If a variant created by correction is identical to another variant, this other variant can be given a unique identifier in the `@xml:id` attribute and the correcting variant can refer to this identifier in the `@copyOf` attribute; the `<rdg>` element is empty (“self-closing”) in this case.
  
The element `<rdg>` can additionally contain the attribute `@hand`, whereby the scribe (`#m1`) and the correctors (`#m2`, `#m3`, … - generally `#mr `for *manus recentior*) should be distinguished. If it is not possible to decide by which hand a correction has been made, the attribute is given the value `unknown`. 
  
The location of the correction is specified by using the respective elements for deletion, addition, etc. together with their attributes, [see above](#edition-of-the-transcription ). 
  
```xml
<app type="variants">
 <rdgGrp><lem wit="#Pa #Pb #Ha #Va">ὁ γενναῖος ἐκεῖνος</lem>
 <rdg wit="#Be" varSeq="2" hand="m2"><add place="above">ὁ γενναῖος ἐκεῖνος</add></rdg></rdgGrp>
 <rdg wit="#Be" varSeq="1" type="transposition">ἐκεῖνος ὁ γενναῖος</rdg>
</app>
```  
  
  
Microscopic text substitutions (such as the substitution of individual letters within a word) are also marked up according to the procedure for manuscript transcription within a `<subst>` element with the element `<del>` (substituted text) and the element `<add>` (supplemented text). The `<subst>` element in this case receives the `@hand` attribute. If only text is added or deleted during a correction, only the `<add>` or `<del>` element is used and the `@hand` attribute is attached to this element.
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">ἔχωμεν</lem>
 <rdg wit="#Ha">ἔχ<subst hand="#m2">
   <del>ο</del>
   <add place="above">ω</add>
  </subst>μεν</rdg>
</app>
```  
  
  
######  Conjectures by editors
  
  
Conjectures are marked with `<@type="conjecture">`: If this is done in the element `<lem>`, it is an emendation of the editor (or an older one that the editor joins), if this is done in the element `<rdg>`, it is a conjecture of a different origin not adopted by the editor.
  
Corrections of minor errors (or orthographic normalisations) that do not reach the level of a conjecture are marked with `<@type="correction">`.
  
```xml
<app type="variants">
 <lem resp="#AvS" type="correction">οὐκ</lem>
 <rdg wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">οὐχ</rdg>
</app>
```  
  
  
Proposals of conjectures (*proposuit* or *dubitanter*) are marked in the `<rdg>` element as `<@type="proposition">`. If necessary, the degree of probability of the conjecture being true can be recorded in the `@cert` attribute; possible values are: `low`, `medium`, `high`.
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">ψευδόμενος</lem>
 <rdg resp="#AvS" type="proposition" cert="low">ἀδικῶν</rdg>
</app>
```  
  
  
Text deleted by the editor is marked with `<@type="deletion">` in the `<lem>` element. If the deleted text is to be quoted, it is marked with the help of the `<surplus>` element; otherwise the element remains without text content (“self-closing”). Deletions by other editors are also marked as `<@type="deletion">`.
  
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
  
  
Text added by emendation is marked with `<@type="addition">`. The handwritten variant is marked in the `<rdg>` element with `@type="omission"`; the `<rdg>` element remains without text content (“self-closing”). 
  
To indicate the extent of the addition, the added text is marked up by using the `<supplied>` element, if transmitted text is supplied. In this case `<@type="conjecture">` is to be used instead of `<@type="addition">`.
  
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
  
  
The author of a conjecture, emendatio or correction is referred to in the attribute `@resp` or, in the case of a conjecture taken from an edition, in the attribute `@source` (in contrast to the attribute `@wit` for manuscripts).
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">ψευδόμενος</lem>
 <rdg source="#Savile1612" type="conjecture">ἀδικῶν</rdg>
 <rdg resp="#Ac" type="conjecture">ψευσάμενος</rdg>
</app>
```  
  
  
######  Gaps in the text
  
  
Gaps in the surviving text (as suspected by the editor) are marked with `<gap reason="missing">`. The presumed extent (`@quantity`) of the gap is indicated in letters, words, lines or pages (`@unit` with value `character`, `word`, `line` or `page`) where it seems reasonable and possible (!).
  
If the detection of a gap is taken from a previous editor, the source is indicated in the `@source `or `@resp` attribute.
  
```xml
Ταῦτα λέγω εἰς <gap reason="missing" unit="word" quantity="3"/> ση τοὺς καταφεύγοντας κατέλαβεν τότε κατακλυσμός, 
```  
  
  
Gaps suspected by other editors but not taken over are marked in an apparatus entry as `<rdg>` and receive the attribute `@type="lacunam_indicavit"`. The element is without text content (“self-closing”).
  
```xml
<app type="variants">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab"/>
 <rdg wit="#Sav" type="lacunam_indicavit"/>
</app>
```  
  
  
######  Crux
  
  
Text that cannot be emended by the editor but is certainly corrupted (“crux”) is marked up with the help of the `<sic>` element. The element can either enclose the corrupted text or mark the place of the corruption as a self-closing (“empty”) element.
  
```xml
καὶ ὅσα ὁ νόμος <sic>διαγορεύει</sic>, 
ὅσα προφῆται <sic/> θεσπίζουσιν 
```  
  
  
######  Variants within variants
  
  
Variants can also be nested within each other, i.e. a `<lem>` or a `<rdg>`  element can enclose a variant (`<app>`). The wit attribute of the outer `<app>`  element includes all sigla of the inner `<app>` element (both of `<lem>` and of `<rdg>`): 
  
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
  
  
#####  Economic notation
  
  
Variants that belong together in their genesis should, as long as the variant carriers are identical, be combined as far as possible to increase readability.
  
```xml
<app type="variants">
 <lem wit="#Pt #Pc #Pa #Be #Pb #Pd #Ma #My #Va #Ab">καὶ νῦν</lem>
 <rdg wit="#Ha" type="omission"/>
</app>
```  
  
  
and not:
  
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
  
  
#####  Overlaps
  
  
One problem resulting from the structure of the XML markup language is the overlapping of elements; cf. also the chapter [“Non-hierarchical Structures” in the TEI Guidelines.](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/NH.html )
  
If possible, the method [“Fragmentation and Reconstitution of Virtual Elements”](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/NH.html#NHVE ) should be used.
  
If elements of different categories overlap, e.g. a text-critical note and a quotation, the element `<app>` is to be given priority and the element `<quote>` is to be split up, whereby the parts of the element that belong together are linked with the help of the attributes `@prev` and `@next`, which refer to the ID assigned in the attribute `@xml:id` in each case:
  
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
  
  
If a variant exceeds a division level, it must be given priority and the `<app>` element must be split and linked to each other in the same way as above.
  
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
  
  
#####  Commenting on text-critical decisions
  
  
If it seems necessary or feasible to expand on text-critical considerations that go beyond the indication of causes (with the help of the `@cause` attribute) or  typification (with the help of the `@type` attribute), an element `<note>` for remarks that concern the entire `<app>` element or an element `<witDetail>` for remarks that refer to a specific manuscript can be added within the `<app>` element. In this case, the `<app>`, `<lem>` or `<rdg>` element receives an attribute `@xml:id`, which is referred to in the `<note>` or `<witDetail>` element in an attribute `@target`.
  
```xml
<app type="variants" xml:id="var1">
  <lem wit="#Pt #Pc #Pb #Pd #My #Ma #Ha #Va #Ab">ἀπαστράπτει</lem>
  <rdg wit="#Pa #Be" xml:id="lac-Pa">ἀ</rdg>
  <witDetail wit="#Pa" target="#lac-Pa">Blattausfall.</witDetail>
  <note target="#var1">Sich auf die gesamte Variante beziehende Anmerkung</note>
</app>
```  
  
  
##  File structure of each edition
  
  
Finally, in order to make reuse as easy as possible, it also makes sense to have uniform naming of the individual files and a structured file repository. The Patristic Text Archive follows the [CapiTainS Guidelines](http://capitains.org ) (cf. [Thibault Clérice, Matthew Munson, & Bridget Almas. (2017, May 2). Capitains/Capitains.github.io: 2.0.0 (Version 2.0.0). Zenodo.](http://doi.org/10.5281/zenodo.570516 )) and uses [CTS URNs](http://www.homermultitext.org/hmt-docs/cite/cts-urn-overview.html ) (cf. [Christopher W. Blackwell und Neel Smith, “The CITE Architecture: a Conceptual and Practical Overview”, in Monica Berti, ed., Digital Classical Philology. Ancient Greek and Latin in the Digital Revolution (Age of Access? Grundfragen der Informationsgesellschaft 10; Berlin, 2019), 73–93](https://doi.org/10.1515/9783110599572-006 )).
  
Within a folder `data`, each author (or textgroup) is in a folder named according to the ID for the author or textgroup. Within this folder are subfolders, each named according to the ID for the individual work. Within each folder is a file `__cts__.xml` which contains the metadata for the data in that folder.
  
    data/
      |- pta0013
        |- __cts__.xml
        |- pta003
          |- __cts__.xml
          |- pta0013.pta003.pta-enu1.xml
          |- pta0013.pta003.pta-grc1.xml
          |- pta0013.pta003.pta-MsLa.xml
          |- pta0013.pta003.pta-MsPg.xml
          |- pta0013.pta003.pta-MsPs.xml
          |- pta0013.pta003.pta-MsVi.xml
  
The file names follow the CTS URNs and are structured as follows: The abbreviation “pta0013” stands for the author Amphilochius and “pta003” for the work “Epistula synodalis”. The last part of the URN identifies the specific “edition” of a work: in the example, these are the critical edition of the Greek text (pta-grc1), the German translation (pta-deu1) and the transcriptions of the four manuscripts (pta-MsLa, pta-MsPg, pta-MsPs, pta-MsVi).
  
If you need new PTA-IDs for yet not existant authors/textgroups and/or works, please get into [contact](mailto:annette.von_stockhausen@bbaw.de ) with us.
  