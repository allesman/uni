Spannbaum hat Knoten eines Graphs und Teilmenge der Kanten, sodass es einen Baum ergibt.

Gradfolge = Liste der Knotengrade des Graphen
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
*notwendig*: jeder Knoten hat mindestens Grad $\frac{|V|}{2}$
**planarer Graph**: Kann in 2D ohne Überschneidung von Kanten gezeichnet werden
*hinreichend und notwendig*: **Eulersche Polyederformel**: $f-|E|+|V|=2$ 
*notwendig:* $\deg(v)\le |V|$
*notwendig*: $3|V|-6\geq|E|$
*idk*: $|E|\le 2|V|-4$
