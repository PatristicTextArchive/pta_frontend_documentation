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


A CQL expression always consists of square brackets (`[]`) that contain one (or more) prefix(es) (`word`, `lemma`, `pos`) linked by logical operations and a value between inverted commas for each prefix, e.g. `[word="XXX"]`.

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

The following abbreviations should be used when searching for **Part of Speech** (POS): ADJ (adjective), ADV (adverb), INTJ (interjection), NOUN (noun), PROPN (proper noun), VERB (verb), ADP (prep/postposition), AUX (auxiliary verb), CCONJ (coordinating conjunction), DET (determiner), NUM (numeral), PART (particle), PRON (pronoun), SCONJ (subordinating conjunction), PUNCT (punctuation).

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
