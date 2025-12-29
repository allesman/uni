---
tags: ds
---
diskret heißt basically abzählbar (<-> kontinuierlich)

Mehrdeutigkeit vermeiden im...
Syntax -> Klammern etc.
Semantik -> Alles genau definieren

> [!info] Aussage
> wahr oder falsch
> erfüllbar (kann wahr sein)
> nicht erfüllbar (kann nicht wahr sein)
> gültig (immer wahr/muss wahr sein)

# Zusammengesetze Aussagen
## **Junktoren**
*und*($\land$), *oder*($\lor$), *nicht* ($\neg$), *falls-dann* ($\to$), *gdw* ($\leftrightarrow$), *xor* ($\oplus$) 

| A   | B   | A und B | A oder B | A xor B | falls A dann B |
| --- | --- | ------- | -------- | ------- | -------------- |
| 0   | 0   | 0       | 0        | 0       | 1              |
| 0   | 1   | 0       | 1        | 1       | 1              |
| 1   | 0   | 0       | 1        | 1       | 0              |
| 1   | 1   | 1       | 1        | 0       | 1              |
# Hinreichend vs Notwendig
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
