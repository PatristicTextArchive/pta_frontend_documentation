The **simple search** allows you to 
- Search for a word, lemma or part of speech, 
- Search for a consecutive, uninterrupted series of words, lemmas or parts of speech.

Press the corresponding button for the element to be searched for (word, lemma, part of speech); ‘Word’ is the default setting. 

**Placeholders** are permitted both within and between words: 
- `.` a single character
- `*` no or more repetitions of the preceding character
- `+` one or more repetitions of the preceding character
- `?` none or one repetition of the preceding character
- `{n}` exactly *n* repetitions of the preceding character
- `{n,}` *n* or more repetitions of the preceding character
- `{n,k}` between *n* and *k* repetitions of the preceding character

The following abbreviations should be used when searching for **Part of Speech** (POS): ADJ (adjective), ADV (adverb), INTJ (interjection), NOUN (noun), PROPN (proper noun), VERB (verb), ADP (prep/postposition), AUX (auxiliary verb), CCONJ (coordinating conjunction), DET (determiner), NUM (numeral), PART (particle), PRON (pronoun), SCONJ (subordinating conjunction), PUNCT (punctuation).

## Examples

### Search for a word, lemma or part of speech

- Word: `ἀληθινοῖς` - finds the word *ἀληθινοῖς*
- Lemma: `ἀληθινός` - finds all forms of the lemma ἀληθινός
- Part of speech: `ADJ` - finds all adjectives

### Search for a consecutive, uninterrupted series of words, lemmas or parts of speech

- Series of words: `τὴν ἁγίαν σύνοδον` - finds the words τὴν ἁγίαν σύνοδον in exactly this order
- Series of lemmas: `ὁ ἅγιος σύνοδος` - finds all forms of the three lemmas ὁ, ἅγιος and σύνοδος in exactly this order
- Series of word types: `DET ADJ NOUN` - finds all words of the word type DET, ADJ, NOUN in exactly this order

### Search with wildcards

- `συν.+` - finds all words that begin with *συν* and have at least one other letter
- `.{1,5}ειν` - finds all words that end with *ειν* and have between one and five letters before it
- `.γ.{0,2}α.+` - finds all words that begin with any letter, then have a *γ*, then between no and any two letters, then an *α* and finally one or more letters of your choice. For example, *ἀγαθῶν* is found, but also *ἁγίαν*.
- `τὴν .* σύνοδον` or `ὁ .* σύνοδος` or `DET .* NOUN` - finds the first and last word or lemma or POS and no word or a word of any length in between.

*Attention:* For word types, the placeholder refers to the words found, not to the word type (`.{4,}` does not mean a word type with 4 or more letters, but refers to a word with 4 or more letters found with the search).