# Automaten

### Funktionsweise

Ein Automat befindet sicher immer in genau einem Zustand. Er liest Symbole ein und kann, abhängig vom eingelesenen Symbol seinen Zustand ändern.  
Im einfachsten Fall werden alle Zeichen nacheinander eingelesen und er Endzustand (Zustand nachdem das letzte Symbol gelesen wird) entscheidet ob das Wort akzeptiert wurde (in der vom Automaten akzeptierten Sprache liegt) oder nicht.

### Typen

#### Nichtdeterministisch vs deterministisch

Ein Automat **kann** deterministisch sein, dh. nach jedem eingelesenem Symbol gibt es nur genau einen möglichen Folgezustand. Per Definition ist dies jedoch nicht zwangsweise notwendig. Wird ein nichtdeterministischer Automat verwendet um zu entscheiden, ob ein Wort in einer Sprache liegt oder nicht, so muss es nur eine richtige Zustandsfolge geben, welche das Wort akzeptiert, damit das Wort akzeptiert wird.

#### Transitionssysteme, Akzeptoren und Transduktoren

Automaten welche lediglich ihre Zustände ändern, jedoch keine Ausgaben haben oder eine Sprache akzeptieren werden **Transistionssysteme** genannt.  
Wenn ein Automat eine Sprache "erkennt", dh. akzeptierende Zustände hat und entscheiden kann, ob ein Wort zu einer Sprache gehört oder nicht, spricht man von einem **Akzeptor**.  
Ein Automat darf auch eine Ausgabe erzeugen, in diesem Fall spricht man von **Transduktoren**.  
Eine Turingmaschine kann beispielsweise sowohl ein Akzeptor, also auch ein Transduktor sein.

#### Deterministischer Endlicher Automat (DEA)

Ein DEA ist ein Akzeptor und hat folgende formale Bestandteile:

- Endliche, nichtleere Menge an Zuständen Q
- Eingabealphabet; z. B. Σ = { *a*, *b* }
- Übergangsfunktion
- Startzustand; q<sub>0</sub> ∈ Q
- Nichtleere Menge an akzeptierenden Endzuständen; q<sub>accept</sub> ⊆ Q

Die Übergangsfunktion bestimmt für jede Kombination aus Zustand und eingelesenem Zeichen aus dem Alphabet den Folgezustand.  
Eine Turingmaschine kann (wenn sie akzeptierende Endzustände hat) auch als spezielle Form eines DEA angesehen werden.

## Chomsky-Hierarchie

Die Chomsky-Hierarchie, manchmal auch Chomsky-Schützenberger-Hierarchie, benannt nach dem amerikanischen Linguisiten Noam Chomsky und dem französischem Mathematiker Marcel Schützenberger, wurde erstmals 1956 von Noam Chomsky beschrieben. Sie dient der Klassifizierung von Grammatiken bzw. formalen Sprachen.  
Die Chomsky-Hierarchie ordnet Grammatiken, bzw. Sprachen in eine der vier Typen Typ 0, Typ 1, Typ 2 oder Typ 3 ein. Die "niedrigeren" Typen sind allgemeiner, dh. eine Typ 1 Sprache ist implizit auch eine Typ 0 Sprache, jedoch ist es spezifischer. Es gilt Typ 3 ⊂ Typ 2 ⊂ Typ 1 ⊂ Typ 0. Durch die Einteilung können Grammatiken, Automaten bzw. auch Algorithmen eingeordnet werden und auch gezeigt werden, dass bestimmte Arten dieser genau gleich viel oder eben unterschiedlich viel "können" (Im Sinne von bestimmte Typen von Sprachen erkennen).

### Typ 0 - Unbeschränkte Grammatiken

Unbeschränkte Grammatiken beinhalten alle Grammatiken. Dies ist nicht gleichbedeutend mit beliebigen Sprachen, sondern alle Sprachen, welche semi-entscheidbar sind. Eine Sprache ist semi-entscheidbar, wenn es eine Turingmaschine gibt, welche wenn ein Wort in der Sprache ist, immer in einem akzeptierenden Zustand hält und wenn es nicht in der Sprache ist entweder in einem nicht-akzeptierenden Zustand hält, oder auch nie hält (wenn sie immer hält ist es entscheidbar). Man kann auch sagen, dass eine Sprache semi-entscheidbar ist, wenn es irgendeinen Algorithmus gibt, der Wörter der Sprache erkennt. Man spricht auch von rekursiv aufzählbaren Sprachen oder einer erkennbaren Sprache.  
Ein klassisches Beispiel ist das Halteproblem, dh. die Sprache aller Programme, welche immer irgendwann stoppen und nicht endlos weiterlaufen ist semi-entscheidbar. Die Umkehrung widerum, also alle Programme, welche unendlich lange laufen, ist ein Beispiel für eine nicht rekursiv aufzählbare Sprache.

### Typ 1 - Kontextsensitive Grammatiken

Die kontextsensitiven, auch monotone Grammatiken genannt, erzeugen genau die Sprachen, welche von einem nichtdeterministischen linear beschränkten Automaten erkannt werden. Ein linear beschränkter Automat ist eine Turingmaschine, deren Band nicht unbeschränkt groß ist, sondern nur die Länge des Eingabewortes hat (manchmal auch eine Größe Linear zur Länge der Eingabe). Ob deterministische linear beschränkte Automaten auch genau kontextsensitive Sprachen erzeugen, oder weniger ist bisher unklar und noch nicht bewiesen.  
Beispiele:

- { a<sup>n</sup>b<sup>n</sup>c<sup>n</sup> | n >= 0 } - Wörter welche mit einer Reihe von a's beginnen, gefolgt von einer Reihe von b's und endend mit einer Reihe von c's und die anzahl ist jeweils dieselbe (also { abc, aabbcc, aaabbbccc... })
- Primzahlen in der Binärdarstellung
- Die Programmiersprache Perl wurde absichtlich kontextsensitiv erstellt

### Typ 2 - Kontexfreie Grammatiken

Die kontextfreien Grammatiken entsprechen den nichtdeterministischen Kellerautomaten, dh. sie erzeugen/erkennen dieselben Sprachen. In diesem Fall ist bewiesen, das deterministische Kellerautomaten nicht ausreichen.
Beispiele:

- { a<sup>n</sup>b<sup>n</sup> | n >= 0 } - Wörter bestehend aus einer Reihe von a's gefolgt von derselben Anzahl an b's
- Sprache der Palindrome

#### Kellerautomaten

Ein Kellerautomat sieht einer Turingmaschine in der Darstelung ähnlich, hat aber eigentlich im Vergleich zu endlichen Automaten nur zwei Erweiterungen:

- Ein Kellerautomat hat einen Zwischenspeicher, Stack oder Keller genannt, in welchen der Automat ein Zeichen schreiben kann, und beim nächsten Symbol des Wortes dieses wieder ausliest
- Ein Kellerautomat darf auchmehrere Zustandsübergänge hitnereinander durchführen bzw. Symbole in den Kellerschreiben, bevor das nächste Symbol des Wortes gelesen wird

### Typ 3 - Reguläre Grammatiken

Reguläre Grammatiken entsprechen genau endlichen Automaten, unabhängig davon ob diese deterministisch sind oder nicht. Das bedeutet, dass man aus einem nichtdeterministischen endlichen Automaten immer einen deterministischen endlichen Automaten bauen kann, welcher dieselbe Sprache akzeptiert. Man stellt fest, dass endliche Automaten nur ein "endliches Gedächtnis" haben, dh. Sprachen, die von einer beliebigen Anzahl Zeichen abhängen sind nicht mehr regulär. Eine weitere Art reguläre Sprachen darzustellen sind reguläre Ausdrücke, welcher selbst einfach nur eine Zeichenkette ist, welche gewissen Regeln befolgt und aus der eine reguläre Sprache erzeugt werden kann. Der aus der Progrmamierung bekannte Regex baut auf reguläre Ausdrücke auf, hat jedoch ein paar Erweiterungen (lookaheads und backreferences zu Gruppen) welche nicht mehr in die Definition regulärer Ausdrücke passt. Regex kann dadurch manche Typ2 und Typ 1 Sprachen erkennen, jedoch auch nicht alle Typ 2 und Typ 1 Sprachen.  
Beispiele:

- Alle endlich großen/aufzählbaren Sprachen
- { (ab)<sup>n</sup> | n >= 0 } - Alle Wörter, die einfach nur ab beliebig oft wiederholen
- { wa | w ∈ Σ* } - Alle Wörter, welche auf a enden