---
tags: ds
---
(siehe [[Relationen]])
Graph besteht aus Knoten $V$ und Kanten $E \subseteq V\times V$

> [!info] Bipartit
> Ein Graph ist bipartit, wenn man seine Knoten in zwei Mengen einteilen kann, die untereinander keine Kanten haben

Verkettung / Multiplikation von Relationen ist **NICHT** kommutativ
Endorelation: Relation einer Menge mit sich selbst, $A^{k}$
$R^{\le k}$: Alle Knoten, die in min. $k$ Schritten erreichbar sind.

**Eigenschaften Graphen**

|                 |                                                               |                                                                        |
| --------------- | ------------------------------------------------------------- | ---------------------------------------------------------------------- |
| reflexiv        | Alle Knoten haben Schleifen                                   | $\forall a\in A:(a,a)\in R$                                            |
| irreflexiv      | Kein Knoten hat eine Schleife                                 | $\forall a\in A:(a,a)\notin R$                                         |
| symmetrisch     | Alle Kanten haben auch die Gegenrichtung                      | $(a,b)\in R\to(b,a)\in R$                                              |
| transitiv       | Existiert ein Pfad zwischen zwei Knoten, dann auch eine Kante | $\text{wenn }(a,b)\in R \text{ und }(b,c)\in R\text{ dann }(a,c)\in R$ |
| antisymmetrisch | Keine Kanten haben die Gegenrichtung, außer Schleifen         |                                                                        |
| asymmetrisch    | Keine Kanten haben die Gegenrichtung, auch keine Schleifen    |                                                                        |
$R^+$: Transitive Hülle (kleinstmögliche Erweiterung von $R$, sodass transitiv)
$R^*$: Reflexiv-Transitive Hülle (-,,-, sodass transitiv und reflexiv)



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
