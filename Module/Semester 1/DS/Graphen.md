*Pfad*: Folge von Knoten, die mit Kanten verbunden sind
	*einfach*: keine doppelten Kanten
*Distanz*: Länge des kürzesten Pfads zwischen zwei Knoten
*Zusammenhangskomponente*: Teilgraphen, die zusammenhängen
ungerichtet + keine Schleifen -> einfacher Graph

| Abkürzung | Name                |
| --------- | ------------------- |
| $K_{n}$   | vollständiger Graph |
| $C_n$     | Kreisgraph          |
| $P_n$     | Pfadgraph           |
| $K_{m,n}$ | Kreisgraph          |
| $M_{m,n}$ | Gittergraph         |
| $Q_{n}$   | Hyperwürfel         |
| $B_{n}$   | perfekter Binärbaum |
*Spannbaum* hat Kanten eines Graphen und Teilmenge der Knoten, sodass ein Baum (keine Zyklen) entsteht
*Gradfolge* (Liste der Grade der Knoten)
Realisierbar wenn
1. gerade Summe
2. letztes Element $d_n$ entfernen, letzte $d_n$ Komponenten um 1 verkleinern, aufsteigend sortieren
   -> gdw. Ergebnis realisierbar ist auch Ursprünglicher Graph realisierbar
3. 