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
**Realisierbarkeit**:
- Wenn ungerade Summe kann daraus, kein Graph erstellt werden
- Havel Hakimi (erzeugen eines leichter auf Realisierbarkeit testbaren Graphen, der realisierbar ist gdw es der urpsprüngliche ist): 
	- aufsteigend sortieren
	- letztes Element $d_n$ entfernen
	- letzte $d_n$ Komponenten um 1 verkleinern
	- 🔁
**Euler-Kreis:** Haus des Nikolaus (Jede Kante besucht)
*hinreichend und notwendig*: jeder Knotengrad gerade
**Hamilton-Kreis:** Jeder Knoten besucht, jede Kante $\leq1$
*hinreichend*: jeder Knoten hat mindestens Grad $\frac{|V|}{2}$
**planarer Graph**: Kann in 2D ohne Überschneidung von Kanten gezeichnet werden
*hinreichend und notwendig*: **Eulersche Polyederformel**: $f-|E|+|V|=2$ 
*notwendig:* $\deg(v)\le |V|$
*notwendig*: $3|V|-6\geq|E|$
*idk*: $|E|\le 2|V|-4$
