Die **erweiterte Suche** ermöglicht komplexe Suchanfragen und verwendet dafür die Corpus-Query-Language (CQL).

Folgende **Platzhalter** gibt es: 
- `.` ein einzelnes Zeichen
- `[]` ein einzelner CQL-Ausdruck
- `*` keine oder mehr Wiederholungen des vorangehenden Zeichens
- `+` eine oder mehr Wiederholungen des vorangehenden Zeichens
- `?` keine oder eine Wiederholung des vorangehenden Zeichens/Ausdrucks
- `{n}` genau *n* Wiederholungen des vorangehenden Zeichens/Ausdrucks
- `{n,}` *n* oder mehr Wiederholungen des vorangehenden Zeichens/Ausdrucks
- `{n,k}` zwischen *n* und *k* Wiederholungen des vorangehenden Zeichens/Ausdrucks


Ein CQL-Ausdruck besteht immer aus eckigen Klammern (`[]`), die ein (oder mehrere durch logische Verknüpfung verbundene) Prefix(e) (`word`, `lemma`, `pos`) und zu jedem Prefix einen Wert zwischen Anführungszeichen umfassen, also z.B. `[word="XXX"]`. Außerdem ist es möglich, nach ausgezeichneten Zitaten mit `<quote/>` zu suchen.

Folgende **logische Verknüpfungen** gibt es: 
- innerhalb CQL-Ausdrucks:
    - `&` = `AND` 
    - `|` = `OR`
    - `!` = `NOT`
- zwischen CQL-Ausdrücken:
    - `( cql ) within ( cql )` – Findet einen CQL-Ausdruck innerhalb eines anderen CQL-Ausdrucks 
    - `( cql ) !within ( cql )` – Findet einen CQL-Ausdruck, der nicht innerhalb eines anderen CQL-Ausdrucks steht
    - `( cql ) containing ( cql )` – Findet einen CQL-Ausdruck, der einen anderen CQL-Ausdruck enthält 
    - `( cql ) !containing ( cql )`– Findet einen CQL-Ausdruck, der einen anderen CQL-Ausdruck nicht enthält 
    - `( cql ) followedby ( cql )` – Findet einen CQL-Ausdruck, dem ein anderer CQL-Ausdruck folgt 
    - `( cql ) !followedby ( cql )` – Findet einen CQL-Ausdruck, dem ein anderer CQL-Ausdruck nicht folgt 
    - `( cql ) precededby ( cql )` – Findet einen CQL-Ausdruck, dem ein anderer CQL-Ausdruck vorausgeht 
    - `( cql ) !precededby ( cql )` – Findet einen CQL-Ausdruck, dem ein anderer CQL-Ausdruck nicht vorausgeht 

Ausdrücke können mit Hilfe von Klammern `()` gruppiert werden. 

**Editionen und Übersetzungen (Achtung: keine Transkriptionen) in den folgenden Sprachen sind mit Hilfe von SpaCy-Modellen automatisch analysiert worden: Griechisch, Lateinisch, Englisch, Deutsch. (Das Syrische wird momentan für die Lexikonfunktion des Readers ebenfalls automatisch analysiert; diese Analyse über die Sedra-API steht aber leider nicht für die Suche zur Verfügung; die Einbindung eines SpaCy-Modells für Syrisch ist in Planung, ebenso die Analyse armenischer und altkirchenslavischer Texte. Für diese Sprachen funktioniert daher nur die WORT-Suche, nicht die LEMMA- oder POS-Suche.)**

**Die Suche verwendet die automatisiert analysierten Daten, sobald auf Lemma oder POS (oder zukünftig Morphologie oder Dependency) zurückgegriffen wird. Fehler in den analysierten Daten (v.a. bei der Lemmatisierung) haben daher Auswirkungen auf die Suchergebnisse; u.U. ist es besser, auf die Wortsuche und die Verwendung von Platzhaltern zurückzugreifen. Nicht analysierte Texte haben nur bei Wort-Suchen Treffer.**

Für die Suche nach **Wortarten** (POS, Part of Speech) sind folgende Abkürzungen zu verwenden: ADJ (Adjektiv), ADV (Adverb), INTJ (Interjektion), NOUN (Substantiv), PROPN (Eigenname), VERB (Verb), ADP (Prä-/Postposition), AUX (Hilfsverb), CCONJ (koordinierende Konjunktion), DET (Bestimmungswort), NUM (Zahlwort), PART (Partikel), PRON (Pronomen), SCONJ (unterordnende Konjunktion), PUNCT (Interpunktion).

Die Suche nach **morphologischen** Attributen und nach **syntaktischen** Abhängigkeiten wird demnächst möglich sein.

## Beispiele

- `[word=".*ειν"]` – findet alle Worte, die auf *ειν* enden und davor keinen oder beliebig viele Buchstaben haben, z.B. *ἔχειν*, *μένειν*
- `[word=".*ε[ιῖ]ν"]` – findet alle Worte, die auf *ειν* oder *εῖν* enden und davor keinen oder beliebig viele Buchstaben haben, z.B. *προσαγαγεῖν*, *ἔχειν*
- `[word="ἀπο.+" & pos="ADV"]` – findet Worte, die mit *ἀπο* beginnen und dann mindestens einen weiteren Buchstaben haben *und* ein Adverb sind, also z.B. *ἀποχρώντως*
- `[word="ἀπο.*" & !pos="ADV"]` – findet Worte, die mit *ἀπο* beginnen und dann mindestens einen weiteren Buchstaben haben *und kein* Adverb sind, also z.B. *ἀποστολικῆς*, *ἀποκρίσεις*, *ἀποστολικὴν*, *ἀποκλεισθῆναι*, *ἀποφραγῆναι*
- `[word="ἀπο.*" & (pos="ADV" | pos="ADJ")]` – findet Worte, die mit *ἀπο* beginnen und dann mindestens einen weiteren Buchstaben haben *und* ein Adverb *oder* ein Adjektiv sind, also z.B. *ἀποστολικῆς*, *ἀποστολικὴν*, *ἀποχρώντως*
- `[word="διὰ"][!word="τῶν"]` – findet die Abfolge zweier Worte, wobei das erste Wort *διὰ* ist und das zweite *nicht τῶν*, also z.B. *διὰ τοῦ*, *διὰ σπουδῆς*, *διὰ τοῦτο*, *διὰ ταύτης*, *διὰ τῆς*
- `[pos="NOUN"] [!word="καὶ"] [pos="NOUN"]` – findet die Abfolge dreier Worte, wobei das 1. und 3. Wort ein Substantiv sind und dazwischen kein *καὶ* steht, also z.B. *ἀγάπης ὑμῶν γράμματα*
- `([lemma="ἀγάπη" | lemma="γράμμα"])[]?([lemma="ἀγάπη" | lemma="γράμμα"])` – findet alle Formen von *ἀγάπη oder γράμμα* und *ἀγάπη oder γράμμα* mit *einem oder keinem Wort dazwischen*, also z.B. *ἀγάπης ὑμῶν γράμματα* 
- `([lemma="ἀγάπη"]|[lemma="γράμμα"])[]? followedby ([lemma="ἀγάπη"]|[lemma="γράμμα"])` – findet alle Formen von *ἀγάπη oder γράμμα* mit einem oder keinem nachfolgenden Wort, dem Formen von *ἀγάπη oder γράμμα* folgen, also z.B. *ἀγάπης ὑμῶν*; das nachfolgende *γράμματα* ist nur Kontext
- `[pos="ADJ"] within [pos="DET"] []{1} [pos="NOUN"]` – findet alle *Adjektive*, die direkt zwischen einem Artikel und einem Substantiv stehen, also z.B. *ἁγίαν*, *τὴν* und *σύνοδον* sind Kontext
- `[pos="DET"] []{1} [pos="NOUN"] containing [pos="ADJ"]` – findet alle Ausdrücke aus *Artikel*, einem folgendem *Wort*, das ein *Adjektiv* ist, und einem diesem folgenden *Substantiv*, also z.B. *τὴν ἁγίαν σύνοδον*
- `<quote/> containing [lemma="ἔθνος"]`– findet alle *Zitate*, die eine Form von ἔθνος enthalten
- `<quote/> !containing [lemma="ἔθνος"]`– findet alle *Zitate*, die *keine* Form von ἔθνος enthalten
- `[lemma="σοφός"] within <quote/` – findet alle Formen von σοφός *innerhalb* eines Zitates
- `[lemma="σοφός"] !within <quote/>` – findet alle Formen von σοφός *außerhalb* von Zitaten
- `<quote/> precededby [lemma="ἐντέλλω"] []{1,3}` – findet alle *Zitate*, denen eine Form von ἐντέλλω im Abstand von ein bis drei Worten vorausgeht
- `[lemma="ἐντέλλω"] followedby []{1,3} <quote/>` – findet alle Formen von ἐντέλλω, denen im Abstand von ein bis drei Worten ein *Zitat* folgt