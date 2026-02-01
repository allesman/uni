---
tags: ds, orga
fertig: false
klausur: 2026-02-16T00:00:00.000Z
moodle: "[[https://ds.tum.sexy]]"
semester: 1
---

# Grundlagen
diskret heißt basically abzählbar (<-> kontinuierlich)

Mehrdeutigkeit vermeiden im...
Syntax -> Klammern etc.
Semantik -> Alles genau definieren

> [!info] Aussage
> wahr oder falsch
> erfüllbar (kann wahr sein)
> nicht erfüllbar (kann nicht wahr sein)
> gültig (immer wahr/muss wahr sein)

## Zusammengesetze Aussagen
### **Junktoren**
*und*($\land$), *oder*($\lor$), *nicht* ($\neg$), *falls-dann* ($\to$), *gdw* ($\leftrightarrow$), *xor* ($\oplus$) 

| A   | B   | A und B | A oder B | A xor B | falls A dann B |
| --- | --- | ------- | -------- | ------- | -------------- |
| 0   | 0   | 0       | 0        | 0       | 1              |
| 0   | 1   | 0       | 1        | 1       | 1              |
| 1   | 0   | 0       | 1        | 1       | 0              |
| 1   | 1   | 1       | 1        | 0       | 1              |
## Hinreichend vs Notwendig
falls A, dann B 
wenn gültig:
-> B ist **hinreichend** für A
-> A ist **notwendig** für B
> [!info] Prädikate
> parametrisierte Aussagen, die eine Eigenschaft zusprechen
## Quantoren
*für alle* ($\forall$), *existiert* ($\exists$), *kein*

> [!hint] Negation
> $\lnot (\forall x P(x))\equiv\exists x (\lnot P(x))$ "Nicht für alle x gilt P" = "Es gibt ein x für das nicht P gilt"
> $\lnot (\exists x P(x))\equiv\forall x (\lnot P(x))$ "Nicht ein (kein) x für das P gilt" = "Für alle x gilt nicht P"
# Beweis
- aufgebaut aus Beweisschritten
	- aufgebaut aus *Prämissen -> Konsequenz*

z.B. Syllogismen (Bandersnatch), modus ponens ($(P\to Q)\land P)\to Q$)
# Beweisstrategien

| Name            | Funktionsweise am Beispiel $A\to B$       | Beispiel                               |
| --------------- | ----------------------------------------- | -------------------------------------- |
| direkter Beweis | Nimm A an, beweis damit B                 | ![[IMG_20251016_150731310 copy.png]]   |
| Kontraposition  | Nimm $\lnot B$ an, beweis damit $\lnot A$ | ![[IMG_20251016_150731310 copy 2.png]] |
| Widerspruch     | Nimm $\lnot A$ an, finde Widerspruch      | ![[IMG_20251016_150731310.jpg]]        |
![[DS-Slides.pdf#page=43&rect=24,38,353,164|DS-Slides, p.43]]
# Mengen
- Mehrfachnennung und Ordnung spielt keine Rolle
- explizite und implizite Definition
- Menge darf in Definition nur bereits Definierte Mengen verwenden (Russel)
Symmetrische Differenz $\{1,2\} \triangle \{2,3\}=\{1,3\}$
*Disjunkt* = Keine Überschneidung
$A\uplus B$: Vereinigung disjunkter Mengen
mit $M=\{\{1,2\}, \{2,3\}\}$,  $\cap M=\{1,2\} \cap \{2,3\}$ 
Potenzmenge $2^M$ ist Menge aller möglichen Teilmengen
$|2^M|=2^{|M|}$
*Partition* = Teilmenge der Potenzmenge, alle Mengen sind disjunkt, Vereinigung ergibt Menge (ohne $\emptyset$)
KV-Diagramm
![[Pasted image 20251021210048.png]]
Distributivgesetz gilt in verschiedenen Weisen

Tupel = endliche Sequenz

Sequenz $(a_i)_{i\in \mathbb{N}}=(a_0,a_1,a_2,...,a_i)$

Geometrische Folge $a_i:=cq^i$
Geometrische Reihe: $a_{i+1}:=a_i+cq^i$

Kartesisches Produkt = Menge aller 2-Tupel mit Elementen aus den respektiven Mengen
geht auch für >2 Mengen
$A\times A=A^2$
$A^0=\{()\}$

## Sprachen
$\Sigma$ Alphabet
Sprache $S \subseteq \Sigma^*$
Wort als Tupel der Buchstaben, vereinfachte Darstellung durch Anreihung der Elemente

# Natürliche Zahlen
Induktionsbeweis
**IB** (P gilt für $n_0$)
**IS** ($P(n)\to P(n+1$) beweisen)
	**IA** (P gilt für beliebiges $n\in \mathbb{N}_0$)
	$a_{n+1} =^{Def} ... =^{IA}$
	dann auflösen, sodass P auch für $n+1$ gilt
$n_0$ muss nicht zwingend 0 sein, man kann auch woanders anfangen
**Starke Induktion**: Manchmal kann man nicht von $P(n)$ auf $P(n+1)$ schließen
-> Dann muss man $P$ für alle $x$ mit $n_0\le x \le n$ annehmen, um auf $P(n+1)$ zu schließen

# Relationen / Graphen

Relation $R\subseteq A_1,A_2,...A_k$
Inverse Relation $R^{-1}=R^T=\{(b,a)|(a,b)\in \mathbb{R}\}$ 

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

**Wörter**
$\preceq_{p}$ Präfix
$\preceq_{s}$ Suffix
$\cong_{c}$ Konjugiert
$\preceq_i$ Infix

## Ordnungsrelationen
reflexiv, transitiv, antisymmetrisch
- Totale Ordnung: alle Paare aus $a$ und $b$ stehen in Relation
- Partielle Ordnung: nicht -,,-
Visualisierung mit Hasse Diagrammen (weglassen der Kanten, die nur durch Reflexivität und Transitivität auftauchen)
**Besondere Elemente**
- maximales Element: steht nie an Stelle eins einer Relation
- größtes Element: für alle Elemente existiert Relation wo an Stelle zwei 
- minimales Element: steht nie an Stelle zwei einer Relation
- kleinstes Element: für alle Elemente existiert Relation wo an Stelle eins
- größte untere Schranke (in Bezug auf Teilmenge): größtes Element, das $\le$ alle der Teilmenge
- kleinste obere Schranke (-,,-): kleinstes Element, das $\ge$ alle der Teilmenge
## Äquivalenzrelationen
reflexiv, transitiv, symmetrisch
Partitionieren die Elemente in Äquivalenzklassen
Äquivalenzklasse von Element $a$ bezüglich Relation $R$: $[a]_{R}$
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

# Funktionen
Untergruppe von Relationen $R\subseteq A\times B$, wo jedes Element von $A$ maximal einmal vertreten ist
partielle Funktion: Nicht jedes Element von $A$ vertreten
$B^A=:\{f:A\to B\}$ aka die Menge aller Funktionen zwischen $A$ und $B$
**Multimenge**: mehrmals dasselbe Element erlaubt
# Operationen
- Untergruppe von Funktionen
- $f:A^k\to A$ ist $k$-stellige Operation, aber $2$-stellige Relation
- mögliche Eigenschaften
	- assotiativ
	- kommutativ
	- idempotent: $a\diamond a=a$
	- linksneutrales Element $e_l$: $e_{l}\diamond a=a$
	- rechtsneutrales Element $e_r$: $a\diamond e_{r}=a$

$f^{2}(x)=(f\circ f)(x)$
$f^0(x)=Id_{x}$

Wenn $f=A^A$, dann injektiv <-> bijektiv <-> surjektiv
Wenn $g\circ f$ bijektiv, dann $f$ injektiv $g$ surjektiv
**Orbit**=eindeutig bestimmter unendlicher Pfad

# Kardinalität
$|A|\le|B|\leftrightarrow \text{Es gibt eine injektive Funktion} f:A\to B$
$|A|=|B|\leftrightarrow \text{Es gibt eine bijektive Funktion} f:A\to B$
${0,1}^{\mathbb{N}}=\text{Funktionen mit } \mathbb{N}\to\{0,1\}$
zeig $|A|=|B|$
- Option 1: Bijektion $A\to B$
- Option 2: Injektion $A\to B$ und $B\to A$
$|A|<|B|$ Bilde Ungleichungskette $|A|\le|C_{1}|\le \dots \leq |C_{N}|\le B$
Für $|C_{i}\leq|C_{i+1}|$: Injektion
Für $|C_{i}=|C_{i+1}|$: Satz von Cantor

# Logik
![[DS-Slides.pdf#page=516&rect=1,20,340,272|DS-Slides, p.449]]
![[DS-Slides.pdf#page=517&rect=6,47,313,274|DS-Slides, p.450]]
![[DS-Slides.pdf#page=518&rect=3,52,341,267|DS-Slides, p.451]]