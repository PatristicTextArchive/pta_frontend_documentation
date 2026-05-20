The **advanced search** enables complex search queries and uses the Corpus Query Language (CQL) for this.

The following **placeholders** are available: 
- `.` a single character
- `[]` a single CQL expression
- `*` no or more repetitions of the preceding character
- `+` one or more repetitions of the preceding character
- `?` none or one repetition of the preceding character/expression
- `{n}` exactly *n* repetitions of the preceding character/expression
- `{n,}` *n* or more repetitions of the preceding character/expression
- `{n,k}` between *n* and *k* repetitions of the preceding character/expression


A CQL expression always consists of square brackets (`[]`) that contain one (or more) prefix(es) (`word`, `lemma`, `pos`) linked by logical operations and a value between inverted commas for each prefix, e.g. `[word="XXX"]`. It is also possible to search for annotated quotations with `<quote/>`.

The following **logical links** exist: 
- within CQL expressions:
    - `&` = `AND` 
    - `|` = `OR`
    - `!` = `NOT`
- between CQL expressions:
    - `( cql ) within ( cql )` - Finds a CQL expression within another CQL expression 
    - `( cql ) !within ( cql )` - Finds a CQL expression that is not within another CQL expression
    - `( cql ) containing ( cql )` - Finds a CQL expression that contains another CQL expression 
    - `( cql ) !containing ( cql )`- Finds a CQL expression that does not contain another CQL expression 
    - `( cql ) followedby ( cql )` - Finds a CQL expression that is followed by another CQL expression 
    - `( cql ) !followedby ( cql )` - Finds a CQL expression that is not followed by another CQL expression 
    - `( cql ) precededby ( cql )` - Finds a CQL expression that is preceded by another CQL expression 
    - `( cql ) !precededby ( cql )` - Finds a CQL expression that is not preceded by another CQL expression 

Expressions can be grouped using parentheses `()`. 

**Editions and translations (note: no transcriptions) in the following languages have been automatically analyzed with the help of SpaCy models: Greek, Latin, Armenian, English, German. (Syriac is currently also automatically analyzed for the lexicon function of the reader; unfortunately, this analysis via the Sedra API is not available for the search; the integration of a SpaCy model for Syriac is being planned. It is also planned to add Armenian and Church Slavonic. Currently, you can only do searches for WORD, not for LEMMA or POS in these languages.)**

**The search uses the automatically analyzed data as soon as lemma or POS (or in future morphology or dependency) is used. Errors in the analyzed data (especially in lemmatization) therefore have an impact on the search results; it may be better to resort to word searches and the use of wildcards.  Unanalyzed texts only have hits in word searches.**

The following abbreviations should be used when searching for **Part of Speech** (POS): ADJ (adjective), ADV (adverb), INTJ (interjection), NOUN (noun), PROPN (proper noun), VERB (verb), ADP (prep/postposition), AUX (auxiliary verb), CCONJ (coordinating conjunction), DET (determiner), NUM (numeral), PART (particle), PRON (pronoun), SCONJ (subordinating conjunction), PUNCT (punctuation).

It will soon be possible to search for **morphological** attributes and **syntactic** dependencies.

## Examples

- `[word=".*ειν"]` - finds all words that end with *ειν* and have no letters or any number of letters before them, e.g. *ἔχειν*, *μένειν*
- `[word=".*ε[ιῖ]ν"]` - finds all words that end in *ειν* or *εῖν* and have no or any number of letters before them, e.g. *προσαγαγεῖν*, *ἔχειν*.
- `[word="ἀπο.+" & pos="ADV"]` - finds words that begin with *ἀπο* and then have at least one further letter *and* are an adverb, e.g. *ἀποχρώντως*
- `[word="ἀπο.*" & !pos="ADV"]` - finds words that start with *ἀπο* and then have at least one other letter *and are not* an adverb, e.g.  *ἀποστολικῆς*, *ἀποκρίσεις*, *ἀποστολικὴν*, *ἀποκλεισθῆναι*, *ἀποφραγῆναι*
- `[word="ἀπο.*" & (pos="ADV" | pos="ADJ")]` - finds words that begin with *ἀπο* and then have at least one other letter *and* are an adverb *or* an adjective, e.g. *ἀποστολικῆς*, *ἀποστολικὴν*, *ἀποχρώντως*
- `[word="διὰ"][!word="τῶν"]` - finds the sequence of two words where the first word is *διὰ* and the second is *not τῶν*, e.g. *διὰ τοῦ*, *διὰ σπουδῆς*, *διὰ τοῦτο*, *διὰ ταύτης*, *διὰ τῆς*
- `[pos="NOUN"] [!word="καὶ"] [pos="NOUN"]` - finds the sequence of three words, where the 1st and 3rd word are a noun and there is no *καὶ* in between, e.g. *ἀγάπης ὑμῶν γράμμματα*
- `([lemma="ἀγάπη" | lemma="γράμμμα"])[]? ([lemma="ἀγάπη" | lemma="γράμμμα"])` - finds all forms of *ἀγάπη or γράμμμα* and *ἀγάπη or γράμμμα* with *one or no word in between*, e.g. *ἀγάπης ὑμῶν γράμμματα*
- `([lemma="ἀγάπη"]|[lemma="γράμμα"])[]? followedby ([lemma="ἀγάπη"]|[lemma="γράμμμα"])` - finds all forms of *ἀγάπη or γράμμα* with one or no subsequent word followed by forms of *ἀγάπη or γράμμα*, e.g. *ἀγάπη or γράμμα*. e.g. *ἀγάπης ὑμῶν*; the following *γράμματα* is only context
- `[pos="DET"] []{1} [pos="NOUN"] containing [pos="ADJ"]` - finds all expressions consisting of *article*, a following *word*, which is an *adjective*, and a following *noun*, e.g. *τὴν ἁγίαν σύνοδον*
- `[pos="ADJ"] within [pos="DET"] []{1} [pos="NOUN"]` - finds all *adjectives* that are directly between an article and a noun, e.g. *ἁγίαν*, *τὴν* and *σύνοδον* are context
- `<quote/> containing [lemma=“ἔθνος”]`- finds all *quotes* that contain a form of ἔθνος
- `<quote/> !containing [lemma=“ἔθνος”]`- finds all *quotes* that *do not* contain any form of ἔθνος
- `[lemma=“σοφός”] within <quote/` - finds all forms of σοφός *within* a quote
- `[lemma=“σοφός”] !within <quote/>` - finds all forms of σοφός *outside* of quotations
- `<quote/> precededby [lemma=“ἐντέλλω”] []{1,3}` - finds all *quotes* that are preceded by a form of ἐντέλλω one to three words apart
- `[lemma=“ἐντέλλω”] followedby []{1,3} <quote/>` - finds all forms of ἐντέλλω that are followed by a *quote* between one and three words apart