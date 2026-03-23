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