---
tags: ds
---
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
# Induktionsbeweis
**IB** (P gilt für $n_0$)
**IS** ($P(n)\to P(n+1$) beweisen)
	**IA** (P gilt für beliebiges $n\in \mathbb{N}_0$)
	$a_{n+1} =^{Def} ... =^{IA}$
	dann auflösen, sodass P auch für $n+1$ gilt
$n_0$ muss nicht zwingend 0 sein, man kann auch woanders anfangen
**Starke Induktion**: Manchmal kann man nicht von $P(n)$ auf $P(n+1)$ schließen
-> Dann muss man $P$ für alle $x$ mit $n_0\le x \le n$ annehmen, um auf $P(n+1)$ zu schließen