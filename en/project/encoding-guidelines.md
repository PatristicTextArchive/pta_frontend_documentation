The edition guidelines for the PTA are set out in a *schema* that narrows
down the comprehensive and often redundant regulations of the TEI
in a TEI-compliant way and that is the basis of the following rules and
examples.
  
> These edition guidelines are a slightly abridged version (but *updated*
> to version 2.0 of the schema) [of Annette v. Stockhausen, Die
> Modellierung kritischer Editionen im digitalen Zeitalter, ZAC 24
> (2020),
> 123-160](https://nbn-resolving.org/urn:nbn:de:kobv:b4-opus4-35237).
> This schema has its origins in the Epidoc Guidelines, but has
> significantly expanded and modified them.
  
The choice of the TEI-XML mark-up language for the encoding of the
digital critical edition marks a fundamental difference from the
classical critical edition as we know it from our printed editions,
namely the distinction between the encoding of the edition in digital
format and its presentation in print, on the internet, as an e-book,
etc. The edition in the true sense is the data encoded in TEI-XML,
which can be expected to remain available and receivable over a long
period of time, while its presentation in print or on the internet is a
matter of reduced (or enriched) manifestations of this data in terms of
information content, which, especially in the case of online
presentation, is subject to the constant change of technology.
  
In any case, the advantages of a critical digital edition, as defined
and exemplified in the following, should be noted:
  
1.  The creation of full-text transcriptions (instead of recording only
    readings in a collation table) and the publication of this research
    data as part of the digital edition increase the comprehensibility
    of the text-critical decisions made by the editor and make possible
    a comprehensive review that goes far beyond the variants presented
    in the *praefatio* of a printed edition, since that is always a matter
    of concentrating information in as little space as possible.
  
2.  The decisions underlying the *constitutio textus* can be explained
    in *situ* by text-critical commentaries. This also increases the
    transparency of the edition.
  
3.  The simultaneous provision of manuscript transcription *and*
    critical edition keeps the edition open to different
    edition-philological approaches.
  
4.  Due to the strict separation of data (with a focus on completeness)
    and presentation of the data (in a selection of presented phenomena
    made for the respective medium and the respective purpose or
    question), quite different modes of presentation can be chosen on
    the basis of a data set, which can additionally be enriched by
    further data from other sources.
  
##  Building a digital edition according to TEI
  
  
> The following writing conventions are used in these guidelines:
> `<element>` means XML elements, `@attribute` means XML attributes, and
> `value` means the values attributed to the attributes; `#` in a value
> means that it is an identifier defined elsewhere in the TEI file,
> usually the `<teiHeader>`, which is referenced at this point.
  
TEI files are basically divided into two parts: They contain a
[`<teiHeader>`](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-teiHeader.html )
section with all metadata and a
[`<text>`](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-text.html )
section with the edition.
  
All files (transcriptions, editions or translations) contain the
following metadata in the `<teiHeader>`:
  
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
    </encodingDesc>
    <profileDesc>
      <creation>
          <date>Date of creation</date>
          <placeName>Place or region of creation</placeName>
      </creation>
      <textClass>
        Genre of text according to https://www.comphistsem.org/46.html
      </textClass>
    </profileDesc>
    <revisionDesc>
      <change who="#AvS" when="2019-02-05">Transkription des Textes anhand des Mikrofilms im Besitz des CNRS</change>
    </revisionDesc>
  </teiHeader>
```  
  
The section `<fileDesc>` contains the bibliographical information on the
file, in particular information
  
- on the title (`<titleStmt>`)
- on the publication (`<publicationStmt>`). In this section, the IDs (`<idno>`) (e.g. CPG, CPL, BHG, Pinakes-Oeuvre) should be adjusted, as this enables the interchangeability and linking of the data.
- on the sources (`<sourceDesc>`). In this section, the information in the three types of files (transcription, critical edition, translation) differs
significantly.
  
The `<encodingDesc>` section provides all the information concerning the
encoding of the file and in each case contains an element `<refsDecl>`,
which defines the outline structure of the file according to the
[“CapiTainS Guidelines”](http://capitains.org/ ).
  
Information on the dating (`<date>`) and location (`placeName`) of the
text is provided in the `<creation>` element and on the genre (using the
text type classification of <https://www.comphistsem.org/46.html>) in the
`<textClass>` element within the `<profileDesc>` section.
  
Since digital editions, unlike printed editions, can be potentially very
fluid data, it is of great importance that all significant changes to
the file and its authors are recorded in the `<revisionDesc>` section,
so that the version history of the individual files can be traced even
when detached from the [PTA's Git repository](https://github.com/PatristicTextArchive/pta_data/ ).
  
##  Transcription of the witnesses
  
  
Manuscripts are witnesses to a specific stage in the transmission of a
text. In contrast to the classical “Lachmannian” approach, in which in
practice only the variants of the master copy of the text (the archetype) are noted, it is appropriate for digital editions - also taking into account the basic
idea of the “New Philology” of valuing each individual transmission
medium - and also makes sense in terms of labour economy to transcribe
the entire text and then, in a second step, to carry out the collation
of the witnesses with the help of the computer.
  
> In the Berlin academy project, the
> [CollateX](https://web.archive.org/web/20200329141404/https://collatex.net/ )
> programme is used for this purpose, whereby the transcription files
> are converted into the input format required for CollateX with the
> help of a Python script (<https://github.com/PatristicTextArchive/collator>).
> Minor errors in the alignment of the collation table can be corrected
> manually afterwards.
  
The transcriptions are thus also editions and the result of
interpretation. However, they differ from the critical edition (see
below) in that they follow a diplomatic (documentary) edition paradigm:
The phenomena found in the manuscript, such as the spelling of words,
accentuation, punctuation and word division, are in principle not
normalised in the transcription, i.e. not corrected if necessary. In
addition, page, column and line breaks, initials and ektheseis,
marginalia, abbreviations, markings, rubrics, erasures, additions - also
from a diachronic point of view (sc. in view of scribe changes) - are
recorded, but not marked according to their visual appearance, but
according to their semantics, i.e. subjected to an interpretation. Even
phenomena that cannot be interpreted, such as text that cannot be
deciphered, are marked as such and thus uncertainties are not concealed.
  
If necessary, the metadata of the transcriptions can provide more
detailed information on the extent to which phenomena are included or
not.
  
###  Transcription metadata
  
  
In addition to the metadata mentioned above, the header of the
transcription file contains short information about the manuscript in
the `<msDesc>` element within the `<sourceDesc>` section, which includes
at least the `<msIdentifier>` element. The element receives its own
`@xml:id`, which is read e.g. for the identification of the manuscript
during collation. If several scribes can be identified in a manuscript,
it is also useful to briefly describe these scribes in the
`<handNote>` element within a `<handDesc>` subsection in another section
`<physDesc>`, which serves to describe the physical nature of the
manuscript. The attribute `@xml:id` is referenced in the edition as an
identifier and must be set in any case; in addition, other attributes
are available, e.g. the attribute `@scribe` can be used if the scribe is
known by name.
  
For example, if the handwriting is a marginal catena, the layout can be
described in the same section in the `<objectDesc>` within the
`<layoutDesc>` element.
  
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
  
###  Edition
  
  
The entire transcription is in the `<text>` part of the file in a
`<div>` element. The element has the following attributes:
- `type="edition"`
- `@xml:lang` indicating the language of the edited
text using [ISO 639-2](https://www.loc.gov/standards/iso639-2/php/code_list.php ).
- `@n` indicating the URN of the file, see [below](#dateistruktur ).
  
####  Mark-up of the structure of the text
  
  
Within this section, at least one subsection `<div>` with the attribute
`@type="textpart"` is to be used, whereby the attribute `@subtype` may
take the following values: `section` for continuous texts,
`fragment` for fragmentary transmission, `commented` and `commentary` for
commentaries or comparable texts where a distinction is made between a
commented and a commentary text.
  
In the case of a catena, for example, this may look like this:
  
```xml
<div type="edition" xml:lang="grc" n="urn:cts:pta:pta0013.pta003.pta-MsPs">
  <pb n="112v"/>
  <div type="textpart" subtype="commented" n="Gen:1:1–2">
   <seg xml:id="alpha">
    <g type="obelos"/> Εν ἀρχῇ ἐποίησεν ὁ θεὸς τὸν
       οὐρανὸν καὶ τὴν γῆν.</seg>
   <seg xml:id="beta">ἡ δὲ γῆ ἦν ἀόρατος καὶ ἀκατασκεύαστος, καὶ 
       σκότος ἐπάνω τῆς <seg xml:id="a">ἀβύσσου</seg>, καὶ 
       πνεῦμα θεοῦ ἐπεφέρετο ἐπάνω τοῦ ὕδατος.</seg>
   <div type="textpart" subtype="commentary" n="A">
      <head>
       <title type="lemma">Εὐσεβίου·</title>
      </head>
      <seg corresp="#alpha">
       <g type="obelos"/>Kommentar</seg>
      <seg corresp="#beta">Kommentar</seg>
   </div>
   <div type="textpart" subtype="commentary" n="B">
      <seg corresp="#a">Worterklärung</seg>
   </div>
  </div>
</div>
```  
  
The text is further subdivided by the element `<seg>` to which an `@xml-id` is
also assigned in each case in order to be able to mark the references
between the corresponding parts (text, commentary).
  
In the transcription, the `<milestone>` element can be used to refer to
structuring of the text (specified using the `@unit` and `@n` attributes)
by editions (specified using `@edRef`):
  
```xml
<div type="textpart" subtype="section" n="1">
  <p>
  <milestone unit="section" edRef="#Whittaker" n="1"/>Text
  </p>
</div>
```  
  
For editions that exist in the PTA, the value of the `@edRef `attribute
is the URN of the edition (e.g. `urn:cts:pta:pta0001.pta028.pta-grcBibex`).
  
####  Punctuation
  
  
The punctuation is transcribed - without explicit marking - according to
the manuscript.
  
####  Title and title-like elements
  
  
Titles are marked with the element `<title>` within the element
`<head>`:
  
```xml
<head>
 <title>Τοῦ αὐτοῦ ὁμιλία</title>
</head>
```  
  
  
####  Line, column, page, gathering beginnings
  
  
Line beginnings are marked with `<lb/>`, column beginnings with
`<cb/>`, page beginnings with `<pb/>` and gatherings beginnings with `<gb/>.`
  
If there is a break within a word, the respective element receives the
attribute `@break` with the value `no`. There is no space between the parts of the word and the element.
  
At the beginning of the page (and possibly also at the beginning of the
gathering), the element receives the attribute `@n` for entering the page
numbering and - where available - the attribute `@facs` for entering the
link to a digital facsimile.
  
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
  
  
####  Paragraphs
  
  
Paragraphs - as far as they are marked in the manuscript (e.g. by a gap)
– are marked with the element `<p>`. Each transcription consists of at
least one paragraph.
  
####  Initials and Ektheseis
  
  
Initials and ektheseis are marked with the element `<hi>`. In the
attribute `@rend` it is indicated whether it is an `initial` (spanning
several lines) or an `ekthesis` (ekthesis).
  
```xml
<hi rend="ekthesis">θ</hi>ησαυροὶ, ψυχὰς εὐφραίνοντες·
```  
  
  
####  Other highlighting
  
  
Rubricated text is also marked with the element `<hi>`; the attribute
`@rend` receives the value `rubricated`.
  
Text highlighted with a line above the letter or word is marked with
`<hi rend="overline">`.
  
Underlined text is marked with `<hi rend="underline">`.
  
####  Marginalia
  
  
Marginalia are marked in the transcription as `<note>`, the element
being introduced in the text as close as possible to the place where the
marginalia is found.
  
The position is specified in the `@place `attribute.
Permitted values are `top` (if necessary, specified in more detail:
`top_inner`, `top_center`, `top_outer`), `bottom` (`bottom_inner`,
`bottom_center`, `bottom_outer`), `margin_inner` and `margin_outer`.
  
```xml
<note place="top_center"><num>ΛΓ</num></note>
```  
  
  
####  Deleted text
  
  
Text deleted by the writer or a later corrector is marked with
`<del>`. The type of deletion is specified in the `@rend` attribute.
Permitted values are `erasure`, `strikethrough`, `overwrite` and
`expunction`.
  
If a deletion does not originate from the scribe, this can be indicated by the attribute `@hand`, whereby the correctors should be distinguished (`#m2`, `#m3`, ... - generally `#mr` for *manus recentior*; for the indication of hands in the metadata see [above](#meta_transkription )). If it is not possible to decide by which hand a correction has been made, the attribute is assigned the value `unknown`.
  
```xml
γηΐ<del rend="erasure" hand="#m2">ω</del>νων
```  
  
  
####  Corrections
  
  
Corrections (words, but also individual letters) are marked with the
`<subst>` element.
  
If a correction does not originate from the scribe, this can be
indicated by the attribute `@hand`, whereby the correctors should be
distinguished (`#m2`,
`#m3`, ... - generally `#mr `for *manus recentior*, for the indication
of hands in the metadata see [above](#meta_transkription )). If it is not possible to decide by which hand a
correction has been made, the attribute is assigned the value `unknown`.
  
Within this element, the deleted *text* is marked with `<del>`. The type
of deletion is specified in the `@rend` attribute. Permitted values are
`unmarked` (the text to be replaced is not explicitly marked at all),
`marker` (the text to be replaced is marked with a character, e.g. an
obelus or similar), `erasure`, `strikethrough`, `overwrite` and
`expunction`.
  
The *added text* is marked with `<add>`. The place of the addition is
specified with the help of the `@place` attribute. Permitted values are
`above`, `inline` and `margin`.
  
```xml
<subst hand="#m2">
 <del rend="erasure">ἀναλόγως</del>
 <add place="above">παραλόγως</add>
</subst>
```  
  
  
####  Added text
  
  
Added text that is not accompanied by a correction is marked with the
`<add>` element. The location of the addition is specified in the
`@place` attribute. Permitted values are `above`, `inline` and `margin`.
  
If a correction does not originate from the scribe, this can be
indicated by the attribute `@hand`, whereby the correctors should be
distinguished (`#m2`,
`#m3`, ... - generally `#mr `for *manus recentior*; for the indication
of hands in the metadata see [above](#meta_transkription )). If it is not possible to decide by which hand a
correction has been made, the attribute is assigned the value `unknown`.
  
```xml
<add place="above" hand="#m2">hinzugefügter Text</add>
```  
  
  
####  Unreadable text
  
  
Unreadable text is specified with the self-closing element `<gap>` (for
other uses of this element, see [the next entry](#transcr_gap )). The
attribute `@reason` is assigned the value `illegible`. The (estimated)
size (`@quantity`) is given in letters (`@unit="character"`), if
necessary lines (`@unit="line"`).
  
```xml
<gap reason="illegible" quantity="10" unit="character"/>
```  
  
  
####  Gap in the text
  
  
A gap in the text is also indicated with the `<gap>` element. The
attribute `@reason` is in this case assigned the value
`damage` (physical damage) or `fenestra` (left blank by the writer). The
(estimated) amount (`@quantity`) is indicated in letters, lines or pages
(`@unit` with value `character`, `line` or `page`).
  
```xml
<gap reason="fenestra" quantity="10" unit="character"/>
```  
  
  
If, however, a gap has been created by the destruction of text by the
scribe (sc. erasure: `@rend="erasure"`), it is marked with the element
`<del>`; if necessary, in the case of destruction by another hand, the
attribute `@hand` is to be indicated, whereby the correctors should be
distinguished (`#m2`,
`#m3`, ... - generally `#mr `for *manus recentior*; for the indication
of hands in the metadata see [above](#meta_transkription )). If it is not possible to decide by which hand a
correction has been made, the attribute is assigned the value `unknown`.
  
```xml
<del rend="erasure" hand="#m2">
 <gap reason="illegible" quantity="10" unit="character"/>
</del>
```  
  
  
####  Unclear reading
  
  
If a text cannot be deciphered with certainty, it is marked with the
`<unclear>` element.
  
```xml
<unclear>ἄνθρωπον</unclear>
```  
  
  
####  Change of scribe
  
  
If the writer changes in the text, the `<handShift/>` element is
inserted at the position of the change. The scribe can be identified by
the attributes `@medium` (characteristic of the ink or the writing
material used), `@scribeRef` or `@scriptRef`, whereby for the latter
attributes reference should be made to the corresponding `@xml:id` in
the `<teiHeader>` (`<handDesc>`, see [above](#meta_transkription )).
  
```xml
<pb n="228r"/>
<handShift scribeRef="#m2"/>ὃς φησὶ πρὸς αὐτόν· κορ<lb break="no"/>νήλιε·
```  
  
  
####  Nomina sacra
  
  
Nomina sacra *can be* marked-up. For this purpose, within a
`<choice>` element, the abbreviation is included in the element `<abbr>` with the
attribute `@type` of the value `nomSac` and the expanded form is noted
in the `<expan>` element.
  
```xml
<choice>
    <expan>πνεύματι</expan>
    <abbr type="nomSac">
       <hi rend="overline">πνι</hi>
    </abbr>
</choice>
```  
  
  
####  Abbreviations
  
  
If the circumstance of the abbreviation is to be noted, but not the
abbreviated form itself, the element `<expan>` can be used.
  
> The BBAW deliberately refrains from noting the abbreviated form for
> reasons of practicability and the time required otherwise; if
> abbreviations are to be included comprehensively, proceed analogously
> to the nomina sacra.
  
```xml
<choice>
    <expan>κύριε</expan>
    <abbr type="nomSac">
        <hi rend="overline">κε</hi>
    </abbr>
</choice> <expan>εὐλόγησον</expan>
```  
  
  
####  Numbers
  
  
Numbers are marked with the element `<num>`.
  
```xml
<num>ΛΓ</num>
```  
  
  
####  Diple and Paragraphos
  
  
Quotations in manuscripts are often marked with a diple (single or
double) in the margin. They are noted in the transcription with the help
of `<g type="diple"/>` or `<g type="doubled_diple"/>.` (The
`<quote>` element is *not* used in the transcription!)
  
```xml
<lb/><g type="diple"/>προσέχετε φησὶ λαός μου τῶι νόμωι μου· κλίνατε τὸ οὖς ὑμῶν εἰς τὰ ῥήματα
<lb/><g type="diple"/>τοῦ στόματός μου· ἀνοίξω ἐν παραβολαῖς τὸ στόμα μου φθέγξομαι προβλήματα
<lb/><g type="diple"/>ἀπ αρχῆς· εἶτα διδάσκων πόθεν ταῦτα μεμάθηκεν· ὅσα ἠκούσαμεν φησὶ καὶ
```  
  
  
Lines marked in the manuscript with a paragraphos in the margin are
noted using `<g type="paragraphos"/>`.
  
##  Critical Edition
  
  
###  Metadata of the critical edition
  
  
####  Handwritten witnesses and earlier editions
  
  
In addition to the [metadata mentioned above](#aufbau ), the header of
the file for the edition contains a list of the manuscripts used within the
section `<sourceDesc>` in a subsection `<listWit>`. The information on
the individual manuscripts is provided with the help of the element
`<witness>`. The transcription of the manuscript should be linked in the attribute
`@corresp` (in the form of its URN, see [below](#dateistruktur )).
  
All entries receive a machine-readable ID in the `@xml-id` attribute, to
which a human-readable siglum, which may also contain further formatting,
corresponds in the `<witness> `subordinate element
`<abbr type="siglum">`.
  
If the manuscript is a copy of another manuscript, the `xml:id` of this
manuscript is linked in the `@source` attribute. This makes it possible
to eliminate a manuscript marked in this way (and all text variants
attested by it), e.g. for presentation, but also for analysis by a
transformation script.
  
The usual Latin name of the manuscript is given in the `<name>` element,
the date of the manuscript in the `<origDate>` element (if necessary,
additionally machine-readable using the attributes
`@notBefore` and `@notAfter` or `@when`), and the folia or
pages on which the edited text is located are indicated in the element
`<locus>` (if necessary, machine-readable using the
attributes `@from` and `@to`).
  
If a more detailed description of the manuscript is necessary or
desired, e.g. because an edition of an author's work is being compiled
and manuscripts are relevant to several texts for this reason, it makes
sense to outsource this to a separate file, using as fully as possible
the elements described in the [TEI Guidelines in the chapter “Manuscript
Description”](https://tei-c.org/release/doc/tei-p5-doc/en/html/MS.html), and then to refer to them in the `@corresp` attribute of
the `<name>` element.
  
> For the editions produced at the BBAW, such manuscript descriptions
> (focussed on the content) are created as standard, which are listed
> under unique manuscript IDs on
> [https://pta.bbaw.de/manuscripts/](https://pta.bbaw.de/manuscripts/ ).
  
Manuscript families and hyparchetypes can be combined within the
section `@listWit` in a separate subsection `<listWit>` with its own
element `<head>`, which gets its own machine-readable ID for the family
in the attribute `@xml:id` (and analogously a human-readable siglum in
the element `<abbr type="siglum">`).
  
Indirect tradition or ancient as well as modern translations should also
be noted in this way if they are to be referred to in the apparatus
entries of the edition.
  
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
  
  
Corresponding to the listing of manuscripts in a subsection
`<listWit>` within the section `<sourceDesc>`, earlier editions are each
listed in a subsection `<listBibl>` in the element `<bibl>` (or
`<biblStruct>`):
  
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
  
  
Authors of conjectures that cannot be bibliographed in the above sense because, for
example, the conjectures were transmitted orally or they are cited in
another edition, are included as follows:
  
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
  
  
In the `<encodingDesc>` section, a further element `<refsDecl>` with the
attribute `@xml:id` of the value `biblical` specifies in machine- and
human-readable form the system according to which biblical passages are
referenced and how these references can be resolved.
  
```xml
<refsDecl xml:id="biblical">
 <cRefPattern matchPattern="(.+):(.+):([0-9]+):([0-9]+)[\-\.]*[0-9]*" replacementPattern="https://www.bibelwissenschaft.de/bibelstelle/$2$3,$4/$1">
   <p>Referenzen beziehen sich auf biblisches Buch, Kapitel, Vers, sc. LXX:Gn:1:1; ebenso möglich ist: LXX:Gn:1:1-3 für eine Reihe von Versen oder LXX:Gn:1:1.3 für zwei Verse, die nicht aufeinander folgen.</p>
   <p>Es werden die folgenden Abkürzungen verwendet: Gn, Ex, Lv, Num, Dt, Jos, Judg, Rt, 1Sa, 2Sa, 1Ko, 2Ko, 1Chr, 2Chr, 3Esr, Esr, Est, Jdt, Tob, 1Mak, 2Mak, 3Mak, 4Mak, Ps, Oden, Prov, Eccl, Song, Job, Wis, Sir, PsSal, Hos, Am, Mi, Joel, Ob, Jon, Nah, Hab, Zeph, Hag, Sach, Mal, Is, Jr, Bar, Lam, EpistJer, Hes, Sus, Dn, Bel; Mt, Mk, Lk, Jn, Act, Rom, 1Cor, 2Cor, Gal, Eph, Phil, Col, 1Th, 2Th, 1Tim, 2Tim, Tt, Phm, Heb, Jak, 1P, 2P, 1Jn, 2Jn, 3Jn, Jud, Rev.</p>
 </cRefPattern>
 <cRefPattern matchPattern="(.+):(.+):([0-9]+)[\-\.]*[0-9]*" replacementPattern="https://www.bibelwissenschaft.de/bibelstelle/$2$3/$1">
   <p>Referenzen beziehen sich auf biblisches Buch, Kapitel, sc. LXX:Gn:1; ebenso möglich ist: LXX:Gn:1-3 für eine Reihe von Kapiteln oder LXX:Gn:1.3 für zwei Kapitel, die nicht aufeinander folgen.</p>
 </cRefPattern>
 <cRefPattern matchPattern="(.+):(.+)" replacementPattern="https://www.bibelwissenschaft.de/bibelstelle/$2/$1">
   <p>Referenzen beziehen sich auf biblisches Buch, sc. LXX:Gn.</p>
 </cRefPattern>
</refsDecl>
```  
  
  
The abbreviations used in the PTA for the books of the Old Testament
(LXX) are:
  
```txt
Gn, Ex, Lv, Num, Dt, Jos, Judg, Rt, 1Sa,
2Sa, 1Ko, 2Ko, 1Chr, 2Chr, 3Esr, Esr,
Est, Jdt, Tob, 1Mak, 2Mak, 3Mak, 4Mak,
Ps, Oden, Prov, Eccl, Song, Job, Wis,
Sir, PsSal, Hos, Am, Mi, Joel, Ob, Jon,
Nah, Hab, Zeph, Hag, Sach, Mal, Is, Jr,
Bar, Lam, EpistJer, Hes, Sus (Sus-LXX), Dn (Dn-LXX), Bel (Bel-LXX).
  
```  
  
The abbreviations used in the PTA for the books of the New Testament
are:
  
```txt
Mt, Mk, Lk, Jn, Act, Rom, 1Cor, 2Cor,
Gal, Eph, Phil, Col, 1Th, 2Th, 1Tim,
2Tim, Tt, Phm, Heb, Jak, 1P, 2P, 1Jn,
2Jn, 3Jn, Jud, Rev.
```  
  
The passages are formed as follows: Biblical corpus (LXX, Hexapla, Vg or
NT):Book:Chapter:Verse (e.g.: 1,1-2,1.4), e.g. `LXX:Gn:1:1-3`.
  
####  Indication of the encoded phenomena
  
  
Also in the `<encodingDesc>` section, the
`<editorialDecl>` section within the `<interpretation>` subsection
elaborates on which phenomena have been marked up in the text. This
allows users of the edition to quickly see what to expect from the
edition. Adjustments are to be made if necessary.
  
```xml
<editorialDecl>
  <interpretation>
    <p xml:id="biblical-quotations">
    Bibelzitate sind ausgezeichnet und nach den oben angeführten Grundsätzen nachgewiesen.
    </p>
    <p xml:id="places">
    Orte sind ausgezeichnet und mit den IDs des <ref target="https://pleiades.stoa.org/">Pleiades Gazetteers</ref>
referenziert.
    </p>
    <p xml:id="persons">
    Personen sind ausgezeichnet. Biblische Personen sind mit den IDs der <ref target="https://github.com/tyndale/STEPBible-Data">TIPNR - Tyndale Individualised Proper Names with all References</ref>-Liste, alle übrigen Personen und Gruppen mit den IDs der
<ref target="https://lobid.org/gnd">GND</ref> referenziert.
    </p>
  </interpretation>
  ...
</editorialDecl>
```  
  
  
####  Normalisation
  
  
Within the `<editorialDecl>` section, the `<normalisation>` and
`<punctuation>` subsections describe the extent to which the handwritten
text has been normalised in the critical edition. Adjustments are to be
made if necessary.
  
```xml
<editorialDecl>
  ...
  <normalization>
   <p>
    Angaben zur Handhabung von Großschreibung,
    ν-ephelkystikon, σ: οὕτως, Iota subscriptum/adscriptum,
    Trema, Enklitika, Apostroph/Elisionen, Zahlzeichen, Worttrennung,
    nomina sacra.
   </p>
  </normalization>
  <punctuation>
   <p>
    Angaben zur Normalisierung der Interpunktion: Setzung von Punkt,
    Komma, Semikolon, Fragezeichen, Gedankenstrichen und Klammern
   </p>
  </punctuation>
</editorialDecl>
```  
  
####  Type of encoding of the variants
  
  
The last element in the `<encodingDesc>` section is the type of marking
up of the text-critical variants. The entry *must* read:
  
```xml
<variantEncoding method="parallel-segmentation" location="internal"/>
```  
  
  
####  Edition status
  
  
Finally, the element `<revisionDesc>` receives an attribute `@status`,
in which the status of the edition is specified. The following values
are possible:
  
-   `critical-edition` for a critical edition in which the text-critical
    variants have been coded. This should be the normal case for new
    editions that follow the model presented here.
  
-   `critical-edition-no-app` for a critical edition in which the
    text-critical variants have not been encoded, e.g. because it is a
    retro-digitisation of a printed critical edition and for copyright
    reasons the apparatus cannot be included in the retro-digitisation.
  
-   `critical-edition-outdated` for an edition that notes text-critical
    variants but does not, for example, comprehensively include the
    manuscripts.
  
-   `pre-critical-edition` for pre-modern editions (e.g. in the
    Patrologia Graeca or Latina).
  
-   `preliminary-edition` for the provisional publication of critical
    editions in progress. Substantial changes are to be expected at any
    time for editions marked in that way!
  
###  Edition
  
  
The entire critical edition is in the `<text>` part of the file. It
consists of at least one element `<div>`, which contains the edited
text. The element has the following attributes:
- `type="edition"`
- `@xml:lang` indicating the language of the edited text using [ISO 639-2](https://www.loc.gov/standards/iso639-2/php/code_list.php )
- `@n` indicating the URN of the file, see [below](#dateistruktur ).
  
```xml
<div type="edition" xml:lang="grc" n="urn:cts:pta:pta0007.pta010.pta-grcBibex">
<!-- Text der Edition -->
</div>
```  
  
  
In new editions, the edition should be preceded by a section
`<div type="praefatio">` with the praefatio.
  
####  Praefatio
  
  
The Praefatio offers in a continuous text everything that is necessary
for understanding the following text and its tradition. Above all, the
critical value of the manuscripts and their mutual relationship to each
other should be explained, ancient translations and other indirect
transmission as well as earlier editions and translations into modern
languages should be mentioned and appreciated in their critical value.
  
In principle, it makes sense to link the information given in the
`<teiHeader>`.
  
Subsections can be set up using `<div type="section" n="1">` (and 
`<div type="subsection" n="1">` for subdivisions), which can
also contain their own headings in a `<head>` element.
  
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
  
  
####  Text
  
  
#####  Encoding of the structure of the text
  
  
Within the element `<div type="edition">` the text structure
reconstructed by the editor (according to the specifications in the
`<refsDecl n="CTS">` in the `<teiHeader>`) is distinguished with the
help of (also nested) subsections `<div>` of `@type="textpart"`, whereby
the following values are possible for the attribute `@subtype`:
  
-   Book (numbered): `<div type="textpart" subtype="book" n="1">`
  
-   Homily (numbered): `<div type="textpart" subtype="homily" n="1">`
  
-   Chapter (numbered): `<div type="textpart" subtype="chapter" n="1">`
  
-   Subdocument (numbered):
    `<div type="textpart" subtype="subdok" n="1">`
  
-   Praefatio (non-numbered preface in the text):
    `<div type="textpart" subtype="praefatio" n="praefatio">`
  
-   Section (numbered): `<div type="textpart" subtype="section" n="1">`
  
-   Fragment (numbered):
    `<div type="textpart" subtype="fragment" n="1">`
  
-   Commented text (commented passage):
    `<div type="textpart" subtype="commented" n="Gen_1_1">`
  
-   Commentary (annotated passage):
    `<div type="textpart" subtype="commentary" n="Gen_1_1">`
  
-   Hypopsalmos (unnumbered):
    `<div type="textpart" subtype="hypopsalmos" n="hypopsalmos">`
  
-   Hypothesis (not numbered):
    `<div type="textpart" subtype="hypothesis" n="hypothesis">`
  
-   Perioche (not numbered):
    `<div type="textpart" subtype="perioche" n="perioche">`
  
Paragraphs within these subsections are marked with the help of the
`<p>` element. Each `<div>` element contains at least one `<p>` element.
  
#####  Marking up further structural elements
  
  
The page breaks in the manuscripts and earlier editions are indicated as
required by means of the `<pb>` element; the page reference is in the
`@n` attribute and the manuscript or edition is referred to in the
`@edRef` attribute:
  
```xml
<pb n="126r" edRef="#La"/>
```  
  
  
#####  Encoding of biblical and other quotations (and allusions)
  
  
Quotations are marked with the help of the `<quote>` element and can be
given a `@type` attribute so that a distinction can be made between
`marked` and `unmarked` quotations; for paraphrased quotations - insofar
as they are marked as quotations at all - the value `paraphrase` can be
used. In editions of biblical commentaries, lemma quotations are given
the value `lemma` to differentiate them from other quotations.
  
Explicit quotations citing the author of the quotation are marked with
the element `<cit>` and the phrase in it leading the quotation is marked
with the element `<ref>`. Insertions in the quotation (such as
“said”) are marked with the help of `<seg type="insertion">` within
the quotation.
  
Allusions (e.g. to biblical stories and events) are marked with the help
of `<seg type="allusion">`.
  
Pseudo-quotations can be marked with the help of `<seg type="psq">`.
  
For bible quotations, the respective bible passage is given within the
`<ref>` element with reference to the specifications in the
`<teiHeader>` (`@decls="#biblical"`) in the `@cRef` attribute.
  
```xml
<p>Καὶ ὥσπερ ἐκεῖ εἴρηται· 
<quote type="marked">Καὶ προσκολληθήσεται πρὸς τὴν γυναῖκα αὐτοῦ, καὶ ἔσονται οἱ δύο εἰς σάρκα μίαν<ref decls="#biblical" cRef="LXX:Gn:2:24"/></quote>, οὕτως ἡ ψυχὴ ἑνουμένη τῷ θεῷ λόγῳ βοᾷ· 
<quote type="marked">Ἐκολλήθη ἡ ψυχή μου ὀπίσω σου· ἐμοῦ δὲ ἀντελάβετο ἡ δεξιά σου.<ref decls="#biblical" cRef="LXX:Ps:62:9"/></quote> 
Εἶχεν οὖν ἡ παλαιὰ συναγωγὴ ἄνδρα τὸν νόμον, ὡς μαρτυρεῖ Ἡσαΐας σήμερον διὰ τοῦ ἀποστόλου φθεγξάμενος· 
<cit><ref decls="#biblical" cRef="NA:Gal:4:27">Τῇ γὰρ προφητικῇ κατεχρήσατο φωνῇ Παῦλος λέγων· </ref><quote type="marked">Καθὼς γέγραπται ὅτι πολλὰ τὰ τέκνα τῆς ἐρήμου μᾶλλον ἢ τῆς ἔχούσης τὸν ἄνδρα.</quote></cit>
</p>
```  
  
  
#####  Encoding of similia and sources
  
  
Similia are marked up with the help of `<seg type="similar">`, sources (as
far as it is not a citation) with the help of
`<seg type="source>`. The source is indicated within the `<seg>` element
in a `<ref>` element.
  
```xml
<seg type="similar">
ἵνα εἰς βάθος διαδῷ τὴν οἰκείαν ἐνέργειαν ἡ βαφή
<ref>Athanasius, decr. 12,1</ref>
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
  
  
#####  Encoding of people, organisations and places
  
  
**Persons** are marked up with the help of the element `<persName>`. In the
case of biblical persons, the attribute `@type` with the value
`biblical` is used, all other persons do not receive an attribute
`@type`. In the attribute `@key`, the `person_id` in the [PTA person list](https://github.com/PatristicTextArchive/pta_metadata/blob/main/pta_persons.json )
is specified, which in turn draws on the list [“Translators Individualised Proper Names with all References”](https://github.com/tyndale/STEPBible-Data ) as well as its own register of non-biblical persons. Non-biblical persons who are
missing from the PTA register can be added after
[consultation](mailto:annette.von_stockhausen@bbaw.de ).
  
**Institutions (such as synods or theological groupings), peoples and other groups** are marked up using the `<orgName>` element. In the
attribute `@key`, the `org_id` of the [PTA organisations list](https://github.com/PatristicTextArchive/pta_metadata/blob/main/pta_orgs.json )
is specified. Organisations that are missing from the PTA register can
be added after [consultation.](mailto:annette.von_stockhausen@bbaw.de )
  
**Places** are marked with the help of the element `<placeName>`, in
the attribute `@ref` the ID of the [Pleiades Gazetteer](https://pleiades.stoa.org/ ) (using the URL) is referred to.
  
```xml
<p>
ἐπίσκοπον <persName key="PTA_P00012">Βασίλειον</persName> καὶ
<orgName key="PTA_O00001">τὴν ἁγίαν σύνοδον τῶν πατέρων τῶν ἐν <placeName ref="https://pleiades.stoa.org/places/511268">Νικαίᾳ</placeName> σύνοδον</orgName>.
τοίνυν ὁ <persName type="biblical" key="Adam_Gen.2.19">Ἀδὰμ</persName>
</p>
```  
  
  
#####  Text witnesses
  
  
The manuscripts witnessing the text is documented in the element
`<app>` with the attribute `@type="witnesses"`. The element contains
only one element `<rdg>` with the attribute `@wit`, in which one of the
self-closing elements `<witStart/>` (= beginning of a witness),
`<witEnd/>` (= end of a witness), `<lacunaStart/>` (= beginning of a gap)
or `<lacunaEnd/>` (= end of a gap) is inserted.
  
```xml
<app type="witnesses">
    <rdg wit="#Ecl114"><witStart/>μεμαρτύρητο</rdg>
</app>
...
<app type="witnesses">
 <rdg wit="#Pa #Be">εἰ<lacunaEnd/></rdg>
</app>
```  
  
  
#####  Encoding the variants
  
  
The encoding of the variants reflects the editorial decisions made in the
editing process, especially the assessment of the variants and the
stemmatic contexts, and is *not a* neutral description of the surviving
material, but an interpretation of it.
  
At each point in the text that has survived in different versions, the
variants are indicated within the `<app>` element, which has an
`@type` attribute with the value `textcritical`. Within this element
`<app>`, the reconstructed text is marked with the element `<lem>`, the
variants judged to be secondary with the element `<rdg>`, whereby this
element may occur more than once within an `<app>` entry, in contrast to
`<lem>`. All types of variant transmission described below presuppose an
assessment of the individual variants as primary (`<lem>`) or secondary
(`<rdg>`).
  
*All* variant witnesses are indicated in the `<lem>` and in the
`<rdg>` elements in the attribute `@wit`, if the variant is in a
manuscript, or in the attribute `@source` or `@resp`, if the variant goes
back to a conjecture in an edition or by a person.
  
In the case of a printed edition, one would thus speak of a positive
apparatus, with the particularity that in the case of the digital
critical edition, the readings of codices descripti are also indicated.
The step of elimination or the reduction of the positive apparatus to a
negative apparatus can, but does not have to, be carried out when
preparing the data for presentation (in print or online). The
categorical difference between the traditional critical edition in print
and the critical digital edition lies in this distinction between the
complete recording of data, which makes the traceability and
verifiability of editorial decisions possible to a much greater extent
than before, and, if necessary, selective presentation.
  
The values of the elements `@wit`, `@source` and `@resp` refer to the
values of the attribute `@xml:id` of the element `<witness>`,
`<bibl>` or `<person>` specified in the element `<sourceDesc>` (in the
`<teiHeader>`, [see above](#sourceDesc )).
  
To increase readability for human recipients of the edition, all variant
carriers within the `@wit` attribute should be presented in a consistent
order (and taking stemmatic relationships into account).
  
In the case of several variants within an `<app>` element, the various
`<rdg>` entries should be ranked in such a way that the closer they are
stemmatically (according to the editor's assessment) to the
`<lem>` variant, the earlier they are listed.
  
Variants (`<lem>` and `<rdg>` or several `<rdg>` entries) that are
considered to belong together in their genesis or otherwise can be
placed in one element `<rdgGrp>` for clarification.
  
The text of the variation shall always be given in its full text and
shall not be abbreviated under any circumstances.
  
#####  Typification of variants
  
  
Variants can have an attribute `@type`, with the help of which the
editor provides the recipient of the edition with an analysis of the
variant and which can thus also be easily filtered for presentation. The
following values of this attribute are possible:
  
-   `orthographic`, when a variant is interpreted by the editor as
    affecting only the spelling, i.e., in the case of Greek manuscripts,
    for example, as most likely being due to itacism.
-   `homoioteleuton` or `homoiarkton` if, in the opinion of the editor,
    a variant is due to homoioteleuton or homoiarkton.
-   `dittography`, when a variant is interpreted as a dittography.
  
```xml
<app type="textcritical">
  <lem source="#Sav" cause="conjecture">νομογράφῳ</lem>
  <rdgGrp>
    <rdg wit="#Be #Ab">τῷ νόμῳ γράφει</rdg>
    <rdg wit="#Pt #Pa #Pb #Pd #Ma #Ha #Va" type="orthographic">τῷ νομῳ γράφει</rdg>
  </rdgGrp>
  <rdgGrp>
    <rdg wit="#Pc">τὸν νόμον γράφει</rdg>
    <rdg wit="#My" type="orthographic">τὸν νόμων γράφει</rdg>
  </rdgGrp>
</app>
```  
  
  
#####  Analysis of the causes for the variation
  
  
The results of the analysis of reasons for variants are given in the
`@cause` attribute.
  
######  Additions
  
  
Additions, including dittographies and other repetitions, are marked in
the `<rdg>` element as `<@cause="addition">`. The `<lem>` element
remains without text content (“self-closing”).
  
```xml
<app type="textcritical">
 <lem wit="#Pt #Pc #Pd #Ma #My"/>
 <rdg wit="#Ha #Pa #Be" cause="addition">καὶ περὶ τοῦ ἁγίου πνεύματος</rdg>
 <rdg wit="#Pb #Va" cause="addition">λόγος πάνυ ὠφέλιμος</rdg>
</app>
```  
  
  
######  Omissions
  
  
Omissions are marked as `<@cause="omission">`. The `<rdg>` element
remains without text content (“self-closing”).
  
```xml
<app type="textcritical">
 <lem wit="#Pa #Be #Pb #Va #Ha">ἀπεικάζεται καὶ</lem>
 <rdg wit="#Pt #Pc #Pd #Ma #My #Ab" cause="omission"/>
</app>
```  
  
  
######  Deletions
  
  
Deletions are marked as `<@cause="deletion">`, whereby (in contrast to
the transcription) it is no longer differentiated how the text was
deleted, since this information can be taken from the transcription file
at any time.
  
Deletions are analytically distinguished from omissions by the fact that
they are due to a deliberate intervention by the writer of the
respective manuscript. The `<rdg>` element is again without textual
content (“self-closing”).
  
```xml
<app type="textcritical">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">καὶ</lem>
 <rdg wit="#Pb" cause="deletion"/>
</app>
```  
  
  
######  Not readable text
  
  
Unreadable text is marked as `<@cause="illegible">`. The element
`<rdg>` is without text content (“self-closing”).
  
######  Transpositions
  
  
Transpositions are marked as `<@cause="transposition">`. In the
`<rdg>` element, the transposed text is reproduced in its full wording
(sc. not abbreviated).
  
```xml
<app type="textcritical">
 <lem wit="#Pa #Be #Pb #Va #Ha">τὰ τοῦ θεοῦ</lem>
 <rdg wit="#Pt #Pc #Pd #Ma #My #Ab" cause="transposition">τοῦ
   θεοῦ τὰ</rdg>
</app>
```  
  
  
Rearrangements that affect longer passages of text - especially if they
span structural units - are marked as omissions and additions, with both
`<app>` elements each receiving an `@xml:id` attribute and referencing
the other using the `@prev` and `@next` attributes.
  
```xml
<div type="textpart" subtype="section" n="1">
    <p>οὐδὲ γἁρ 
    <app type="textcritical" xml:id="app1-1" next="#app1-2">
        <lem wit="#Pt #Pb #My #Ha #Va #Ab">καλόν ἐστι</lem>
        <rdg wit="#Pc #Pd Ma" cause="omission"/>
    </app>
    </p>
</div>
<div type="textpart" subtype="section" n="2">
    <p>τὸ ἔξω τοῦ οἴκου τοῦ θεοῦ πολιτεύεσθαι
    <app type="textcritical" xml:id="app1-2" prev="#app1-1">
        <lem wit="#Pt #Pb #My #Ha #Va #Ab"/>
        <rdg wit="#Pc #Pd #Ma" cause="addition">καλόν ἐστι</rdg>
    </app>
      </p>
</div>
```  
  
  
######  Corrections by scribe
  
  
Corrections of the text by the scribe or a later corrector are
distinguished in such a way that the order of the different stages of
transmission is indicated in the `<rdg>` element with the help of the
`@varSeq` attribute.
  
If a variant created by correction is identical to another variant, this
other variant can be given a unique identifier in the
`@xml:id` attribute and the correcting variant can refer to this
identifier in the `@copyOf` attribute; the `<rdg>` element is empty
(“self-closing”) in this case.
  
The element `<rdg>` can additionally contain the attribute `@hand`,
whereby the scribe (`#m1`) and the correctors (`#m2`, `#m3`, ... -
generally `#mr `for *manus recentior*) should be distinguished. If it is
not possible to decide by which hand a correction has been made, the
attribute is given the value `unknown`.
  
The location of the correction is specified using the
`@style` attribute; possible values are `supralinear`, `marginal` and
`inline`.
  
```xml
<app type="textcritical">
 <lem wit="#Pa #Pb #Ha #Va" xml:id="lem178">ὁ γενναῖος ἐκεῖνος</lem>
 <rdg wit="#Be" varSeq="1" cause="transposition">ἐκεῖνος ὁ γενναῖος</rdg>
 <rdg wit="#Be" varSeq="2" hand="m2" style="supralinear" copyOf="#lem178"/>
</app>
```  
  
  
Microscopic text substitutions (such as the substitution of individual
letters within a word) are better marked up according to the procedure for
manuscript transcription within a `<subst>` element with the element
`<del>` (substituted text) and the element `<add>` (supplemented text).
The `<subst>` element in this case receives the `@hand` attribute. If
only text is added or deleted during a correction, only the `<add>` or
`<del>` element is used and the `@hand` attribute is attached to this
element.
  
```xml
<app type="textcritical">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">ἔχωμεν</lem>
 <rdg wit="#Ha">ἔχ<subst hand="#m2">
   <del>ο</del>
   <add place="above">ω</add>
  </subst>μεν</rdg>
</app>
```  
  
  
######  Conjectures by editors
  
  
Conjectures are marked with `<@cause="conjecture">`: If this is done in
the element `<lem>`, it is an emendation of the editor (or an older one
that the editor joins), if this is done in the element
`<rdg>`, it is a conjecture of a different origin not adopted by the
editor.
  
Corrections of minor errors (or orthographic normalisations) that do not
reach the level of a conjecture are marked with `<@cause="correction">`.
  
```xml
<app type="textcritical">
 <lem resp="#AvS" cause="correction">οὐκ</lem>
 <rdg wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">οὐχ</rdg>
</app>
```  
  
  
Proposals of conjectures (*proposuit* or *dubitanter*) are marked in the
`<rdg>` element as `<@cause="proposition">`. If necessary, the degree of
probability of the conjecture being true can be recorded in the
`@cert` attribute; possible values are: `low`, `medium`, `high`.
  
```xml
<app type="textcritical">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">ψευδόμενος</lem>
 <rdg resp="#AvS" cause="proposition" cert="low">ἀδικῶν</rdg>
</app>
```  
  
  
Text deleted by the editor is marked with `<@cause="deletion">` in the
`<lem>` element. If the deleted text is to be quoted, it is marked with
the help of the `<surplus>` element; otherwise the element remains
without text content (“self-closing”). Deletions by other editors are
also marked as `<@cause="deletion">`.
  
```xml
<app type="textcritical">
 <lem resp="#AvS" cause="deletion"/>
 <rdg wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">οὐκ</rdg>
</app>
<app type="textcritical">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">οὐκ</lem>
 <rdg source="#Sav" cause="deletion"><surplus>οὐκ</surplus></rdg>
</app>
```  
  
  
Text added by emendation is marked with `<@cause="addition">`. The added
text is marked up using the `<supplied>` element. The handwritten
variant is marked in the `<rdg>` element with `@cause="omission"`; the
`<rdg>` element remains without text content (“self-closing”).
  
```xml
<app type="textcritical">
 <lem resp="#AvS" cause="addition"><supplied>οὐκ</supplied></lem>
 <rdg wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab"
  cause="omission"/>
</app>
```  
  
  
The author of a conjecture, emendatio or correction is referred to in
the attribute `@resp` or, in the case of a conjecture taken from an
edition, in the attribute `@source` (in contrast to the attribute
`@wit` for manuscripts).
  
```xml
<app type="textcritical">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab">ψευδόμενος</lem>
 <rdg source="#Savile1612" cause="conjecture">ἀδικῶν</rdg>
 <rdg resp="#AC" cause="conjecture">ψευσάμενος</rdg>
</app>
```  
  
  
######  Gaps in the text
  
  
Gaps in the surviving text (as suspected by the editor) are marked
with `<gap reason="missing">`. The presumed extent (`@quantity`) of the
gap is indicated in letters, words, lines or pages (`@unit` with value
`character`, `word`, `line` or `page`) where it seems reasonable and
possible (!).
  
If the detection of a gap is taken from a previous editor, the source is
indicated in the `@source `or `@resp` attribute.
  
```xml
Ταῦτα λέγω εἰς <gap reason="missing" unit="word" quantity="3"/> ση τοὺς καταφεύγοντας κατέλαβεν τότε κατακλυσμός, 
```  
  
  
Gaps suspected by other editors but not taken over are marked in an
apparatus entry as `<rdg>` and receive the attribute
`@cause="lacunam_indicavit"`. The element is without text content
(“self-closing”).
  
```xml
<app type="textcritical">
 <lem wit="#Pa #Be #Pb #Va #Ha #Pt #Pc #Pd #Ma #My #Ab"/>
 <rdg wit="#Sav" cause="lacunam_indicavit"/>
</app>
```  
  
  
######  Crux
  
  
Text that cannot be emended by the editor but is certainly corrupted
(“crux”) is marked up with the help of the `<sic>` element. The element
can either enclose the corrupted text or mark the place of the
corruption as a self-closing (“empty”) element.
  
```xml
καὶ ὅσα ὁ νόμος <sic>διαγορεύει</sic>, 
ὅσα προφῆται <sic/> θεσπίζουσιν 
```  
  
  
######  Variants within variants
  
  
Variants can also be nested within each other. In this case, the lemma
of the overlapping apparatus entry does not receive an `@wit` attribute,
since the attestation can be calculated from the
`@wit` attributes of the elements `<lem>` and `<rdg>` in the inner apparatus entry.
  
The inner `<app>` element must necessarily be in the `<lem>` element, i.e.
in the reconstructed text, of the outer apparatus entry, never in the
`<rdg>` element.
  
```xml
<app type="textcritical">
 <lem>οὐδεμίαν 
  <app type="textcritical">
   <lem wit="#Pt #Pc #Pa #Be #Pd #Ma #My #Ha #Va">εὑρήσεις</lem>
   <rdg wit="#Pb" type="orthographic">εὑρήσῃς</rdg>
  </app>
 </lem>
 <rdg wit="#Ab" cause="omission"/>
</app>
```  
  
  
#####  Economic notation
  
  
Variants that belong together in their genesis should, as long as
the variant carriers are identical, be combined as far as possible to
increase readability.
  
```xml
<app type="textcritical">
 <lem wit="#Pt #Pc #Pa #Be #Pb #Pd #Ma #My #Va #Ab">καὶ νῦν</lem>
 <rdg wit="#Ha" cause="omission"/>
</app>
```  
  
  
and not:
  
```xml
<app type="textcritical">
 <lem wit="#Pt #Pc #Pa #Be #Pb #Pd #Ma #My #Va #Ab">καὶ</lem>
 <rdg wit="#Ha" cause="omission"/>
</app>
<app type="textcritical">
 <lem wit="#Pt #Pc #Pa #Be #Pb #Pd #Ma #My #Va #Ab">νῦν</lem>
 <rdg wit="#Ha" cause="omission"/>
</app>
```  
  
  
#####  Overlaps
  
  
One problem resulting from the structure of the XML markup language is
the overlapping of elements; cf. also the chapter [“Non-hierarchical Structures” in the TEI Guidelines.](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/NH.html )
  
If possible, the method [“Fragmentation and Reconstitution of Virtual Elements”](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/NH.html#NHVE )
should be used.
  
If elements of different categories overlap, e.g. a text-critical note
and a quotation, the element `<app>` is to be given priority and the
element `<quote>` is to be split up, whereby the parts of the element that
belong together are linked with the help of the attributes `@prev` and
`@next`, which refer to the ID assigned in the attribute
`@xml:id` in each case:
  
```xml
<p>Διὰ τί ἐσαλεύθησαν θεμέλιοι τῆς δημιουργίας; 
<quote xml:id="qu1-1" next="#qu1-2">Τί σοι ἐστί,</quote>
<app type="textcritical">
  <lem wit="#Pc #Pt #My">
    <quote xml:id="qu1-2" prev="#qu1-1">θάλασσα, ὅτι ἔφυγες;<ref decls="#biblical" cRef="LXX:Ps:113:3"/></quote> τί ἔλυσας τὸν ὅρον τοῦ νομοθέτου, τοῦ κελεύσαντός σοι <quote xml:id="qu2-1" next="#qu2-2">Μέχρι τούτου ἐλεύσῃ</quote>
  </lem>
  <rdg wit="#Pd" cause="omission"/>
</app>
<quote xml:id="qu2-2" prev="#qu2-1">καὶ οὐχ ὑπερβήσῃ<ref decls="#biblical" cRef="LXX:Job:38:11"/></quote>;</p>
```  
  
  
If a variant exceeds a division level, it must be given priority and the
`<app>` element must be split and linked to each other in the same way
as above.
  
```xml
<div type="textpart" subtype="section" n="1">
    <p>...
    <app type="textcritical" xml:id="app1-1" next="#app1-2">
        <lem wit="#Pt #Pb #My #Ha #Va #Ab">οὐδὲ γάρ ἐστι καλὸν τὸ ἔξω τοῦ οἴκου τοῦ θεοῦ πολιτεύεσθαι.</lem>
        <rdg wit="#Pc #Pd #Ma">οὐδὲν</rdg>
    </app>
    </p>
</div>
<div type="textpart" subtype="section" n="2">
    <p>
    <app type="textcritical" xml:id="app1-2" prev="#app1-1">
        <lem wit="#Pt #Pb #My #Ha #Va #Ab">εὑρήσεις</lem>
        <rdg wit="#Pc #Pd #Ma" type="orthographic">εὑρήσης</rdg>
    </app>
    ...
    </p>
</div>
```  
  
  
#####  Commenting on text-critical decisions
  
  
If it seems necessary or feasible to expand on text-critical considerations that go
beyond typification (with the help of the `@type` attribute) or the
indication of causes (with the help of the `@cause` attribute), an
element `<note>` for remarks that concern the entire `<app>` element or
an element `<witDetail>` for remarks that refer to a specific manuscript
can be added within the `<app>` element. In this case, the
`<app>`, `<lem>` or `<rdg>` element receives an attribute
`@xml:id`, which is referred to in the `<note>` or
`<witDetail>` element in an attribute `@target`.
  
```xml
<app type="textcritical">
  <lem wit="#Pt #Pc #Pb #Pd #My #Ma #Ha #Va #Ab">ἀπαστράπτει</lem>
  <rdg wit="#Pa #Be" xml:id="lac-Pa">ἀ</rdg>
  <witDetail wit="#Pa" target="#lac-Pa">Blattausfall.</witDetail>
</app>
```  
  
  
##  File structure of each edition
  
  
Finally, in order to make reuse as easy as possible, it also makes sense
to have uniform naming of the individual files and a structured file
repository. The Patristic Text Archive follows the [CapiTainS Guidelines](http://capitains.org ) and uses [CTS URNs](http://www.homermultitext.org/hmt-docs/cite/cts-urn-overview.html ) (cf. [Christopher W. Blackwell und Neel Smith, “The CITE Architecture: a Conceptual and Practical Overview”, in Monica Berti, ed., Digital Classical Philology. Ancient Greek and Latin in the Digital Revolution (Age of Access? Grundfragen der Informationsgesellschaft 10; Berlin, 2019), 73–93](https://doi.org/10.1515/9783110599572-006 ).
  
Within a folder `data`, each author (or textgroup) is in a
folder named according to the ID for the author or textgroup. Within this
folder are subfolders, each named according to the ID for the individual work.
Within each folder is a file `__cts__.xml` which contains the metadata
for the data in that folder.
  
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
  
The file names follow the CTS URNs and are structured as follows: The
abbreviation “pta0013” stands for the author Amphilochius and
“pta003” for the work “Epistula synodalis”. The last part of the URN
identifies the specific “edition” of a work: in the example, these are
the critical edition of the Greek text (pta-grc1), the German
translation (pta-deu1) and the transcriptions of the four manuscripts
(pta-MsLa, pta-MsPg, pta-MsPs, pta-MsVi).
  
If you need new PTA-IDs for yet not existant authors/textgroups and/or works, please get into [contact](mailto:annette.von_stockhausen@bbaw.de ) with us.
  