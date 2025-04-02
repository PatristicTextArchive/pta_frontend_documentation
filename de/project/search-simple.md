Die **einfache Suche** ermöglicht die 
- Suche nach einem Wort, Lemma oder einer Wortart, 
- Suche nach einer konsekutiven, nicht unterbochenen Reihe von Worten, Lemmata oder Wortarten.

Für das zu suchende Element (Wort, Lemma, Wortart) ist der entsprechende Schalter zu betätigen; "Wort" ist voreingestellt. 

**Platzhalter** sind sowohl innerhalb als auch zwischen Worten erlaubt: 
- `.` ein einzelnes Zeichen
- `*` keine oder mehr Wiederholungen des vorangehenden Zeichens
- `+` eine oder mehr Wiederholungen des vorangehenden Zeichens
- `?` keine oder eine Wiederholung des vorangehenden Zeichens
- `{n}` genau *n* Wiederholungen des vorangehenden Zeichens
- `{n,}` *n* oder mehr Wiederholungen des vorangehenden Zeichens
- `{n,k}` zwischen *n* und *k* Wiederholungen des vorangehenden Zeichens

Für die Suche nach **Wortarten** (POS, Part of Speech) sind folgende Abkürzungen zu verwenden: ADJ (Adjektiv), ADV (Adverb), INTJ (Interjektion), NOUN (Substantiv), PROPN (Eigenname), VERB (Verb), ADP (Prä-/Postposition), AUX (Hilfsverb), CCONJ (koordinierende Konjunktion), DET (Bestimmungswort), NUM (Zahlwort), PART (Partikel), PRON (Pronomen), SCONJ (unterordnende Konjunktion), PUNCT (Interpunktion).

## Beispiele

### Suche nach einem Wort, Lemma oder einer Wortart

- Wort: `ἀληθινοῖς` – findet das Wort *ἀληθινοῖς*
- Lemma: `ἀληθινός` – findet alle Formen des Lemmas ἀληθινός
- Wortart: `ADJ` – findet alle Adjektive

### Suche nach einer konsekutiven, nicht unterbochenen Reihe von Worten, Lemmata oder Wortarten

- Reihe von Worten: `τὴν ἁγίαν σύνοδον` – findet die Worte τὴν ἁγίαν σύνοδον in genau dieser Reihenfolge
- Reihe von Lemmata: `ὁ ἅγιος σύνοδος` – findet alle Formen der drei Lemmata ὁ, ἅγιος und σύνοδος in genau dieser Reihenfolge
- Reihe von Wortarten: `DET ADJ NOUN` – findet alle Worte der Wortart DET, ADJ, NOUN in genau dieser Reihenfolge

### Suche mit Platzhaltern

- `συν.+` – findet alle Worte, die mit *συν* beginnen und mindestens einen weiteren Buchstaben haben
- `.{1,5}ειν` – findet alle Worte, die auf *ειν* enden und davor zwischen einem und fünf Buchstaben haben
- `.γ.{0,2}α.+` – findet alle Worte, die mit irgendeinem Buchstaben beginnen, dann ein *γ* haben, danach zwischen keinem und zwei beliebige Buchstaben, danach ein *α* und schließlich einen oder mehrere beliebige Buchstaben. Gefunden wird z.B. *ἀγαθῶν*, aber auch *ἁγίαν*.
- `τὴν .* σύνοδον` oder `ὁ .* σύνοδος` oder `DET .* NOUN` – findet das erste und das letzte Wort oder Lemma oder POS und dazwischen kein oder ein Wort von beliebiger Länge.

*Achtung:* Bei Wortarten bezieht sich der Platzhalter auf die gefundenen Worte, nicht auf die Wortart (`.{4,}` bedeutet nicht eine Wortart mit 4 oder mehr Buchstaben, sondern bezieht sich auf ein mit der Suche gefundenes Wort mit 4 oder mehr Buchstaben).