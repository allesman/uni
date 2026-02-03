---
tags: Orga
fertig: false
klausur: 2026-02-13T00:00:00.000Z
semester: 1
retake: 2026-04-01T00:00:00.000Z
note: 0
---
#era
#orga 

# Schulz
## Datendarstellungen
- Grundlage: Relais (Stromkreis durch seperaten Strom an/aus öffnen schließen)
- Transistor (selbe Funktionsweise, aber nur 3 Kontakte also 1 Stromkreis)
### -> Binär
- "Word" Basisgröße des Systems (16 bit, 32 bit, etc.)
- Negative Zahlen via Zweierkompliment (Rechnung leichter)
	- Invertierung + 1
	- Wertebereich $[-1^{n-1},2^{n-1}-1]$
- Kommazahlen via
	- Tupel aus 2 Zahlen (vor und nach Komma)
	- Floating Point Numbers
		- **S**: Vorzeichen
		- **F**: Nachkommastellen nach 1 (Fraction, Koeffizient, Mantisse, Significand)
		- **E**: Verschiebung des Kommas (Abzüglich Bias)
		- ($Mantisse\cdot basis^{Exponent}$)
## Abstraktionsebenen
Sprache -> Compiler -> Assembler Code (ISA) -> Binär Code -> Von-Neumann-Schicht -> Mikroarchitektur-Schicht -> Gatter-Schicht -> Bauelemente-Schicht -> Physikalische Schicht
(gibt noch andere Wege zum Compiler, so Bytecode/JVM oder Interpreter)
Vorteile: Verschiedene Versionen jeder Ebene jeweils mit anderen Ebenen kompatibel
Es geht auch immer anders

---
- [ ] Was ist Bias

## C-Kompilierung
`gcc` - C Code -> Kompilierung auf ausführbare Binärdatei
	`-s`: Erzeugt Zwischenergebnis (Assemblersprache)
`hexdump` - Inhalt der Binärdatei in Hex ausgeben
`objdump` 
	``-h``: teilt in sections ein
	`-d`: Disassemblierung (Binär -> Assemblersprache)
	`-S`: Codiertes Programm mit Bezug auf Quellcode

## ISA
> [!NOTE] ISA
> Instruction Set Architectures
> Assemblersprache, Datenkodierungen, Systemeigenschaften, Boot-Up-Prozess
### Komplexität

|          | CISC                                         | RISC                                 |
| -------- | -------------------------------------------- | ------------------------------------ |
| Vorteil  | einfach programmierbar                       | effiziente, schnelle Implementierung |
| Nachteil | langsame Implementierung, ungenutztes        | schwer programmierbar                |
| Format   | variabel (mehrere Formate für selben Befehl) | einheitlich                          |
### Befehlsklassen
#### arithmetische und logische Operationen
##### Addition/Subtraktion
`add`/`sub` `Ziel, Quelle1, Quelle2`
`addi Ziel Quelle1, Konst` <- max 12 bits
`lui` lädt obere 20 bits (zusammen mit `addi` laden von 32 bits)
##### Multiplikation/Division (nur mit `M`-Erweiterung)
`mul` multipliziert untere 32 bit
`mulh` multiply high (multipliziert obere) **signed \* signed**
	...`su` signed * unsigned
	...`u` unsigned * unsigned
`div` Division abgerundet
`rem` Rest
	...`u` unsigned
##### Logische Operationen (bitwise)
`and`,`or`,`xor`
Für jeden Bit der beiden Zahlen
##### Schiebebefehle
Basically wie Multiplikation/Division, manchmal
`sll` shift left logical (um drittes argument, aber nur letzte 5 bits), füllt mit 0 auf
	...`i` intermediate (direkt mit supplied 5 bit Zahl)
`sr` shift right... (zwei Möglichkeit)
	...`l` logical (füllt mit 0 auf)
	...`a` arithmetic (füllt mit 0 auf, aber behält aller ersten bit aka Vorzeichen)
##### Floating Point Arithmetik
Floats mit `F`-Erweiterung
Doubles mit `D`-Erweiterung
Eigene Register
`fadd`,`fsub`
	...`d`
#### Datentransfer
Daten aus dem Hauptspeicher (Arbeitsspeicher) laden
`ld` load double word (64 bit)
`sd` store double word
`ld destination const(Basisadresse)`
Lädt in `destination` Adresse: Wert von`Basisadresse` + `const`
#### Steuerung des Programmlaufs
##### Unbedingter Sprung
`j offset` Springe zu aktuell + `offset`
`jr reg, const` Springe zu Wert von `reg` + `imm`
Beim selbst Schreiben: Sprungmarken
##### Bedingter Sprung
`bxx Operand1, Operand2, offset` Springe um `offset` wenn Bedingung true
`beq`, `bne`, `blt`, `bge`
Andere Richtungen der letzten beiden via Tausch der Operanden
##### Unterprogramm
`jal reg, offset` Jump and link, Springe um `offset`, Speicher Adresse nächsten Befehls in `reg`

+Systembefehle
+Input/Output

> [!warning] Keine 1:1-Beziehung von Opcode und Befehl
> Pseudobefehle, z.B.
> `mv ra, rb` = `add ra, rb, x0`
> `j offset` = `jal x0, offset`

| Caller-saved                | Callee-saved                                                             |
| --------------------------- | ------------------------------------------------------------------------ |
| musst selber Wert speichern | aufgerufene Funktion darf Wert nicht verändern/muss ihn wiederherstellen |

### Register
x0: zero
x1-x31
### Hauptspeicher (Arbeitsspeicher)
Speicherzellen mit Größe entsprechend ISA
Adresse pro Byte (8 bits)
#### Data alignment
Ausrichtung auf n-Byte-Grenze: jede Adresse mod n = 0
##### Verschieden gehandelt von Architekturen
- x86 erlaubt beides, aber alignment = speed
- ARM (teils) fordert alignment, sonst Fehler
- RISC-V hat getrennte Befehle für beides
#### Reihenfolge der Bytes

| Little Endian                            | Big Endian                           |
| ---------------------------------------- | ------------------------------------ |
| kleinere Ziffern auf niedrigerer Adresse | kleinere Ziffern auf höherer Adresse |
| dominiert, da von Intel verwendet        | auch von bestimmten verwendet        |
meist Wechselmöglichkeit zwischen den beiden (z.B. in RISC-V)

Datenstruktur Stack (LIFO)
- wächst (oft) nach unten
Jedes Programm erhält Adressraum (für genutzte Daten und Programm selbst)
![[era03-beispiel.pdf#page=12&rect=663,34,844,436|era03-beispiel, p.12|300]]
Static Data hat z.B. Konstanten wie verwendete Strings

Aufbau Programm/Routine:
- Prologue
- Tatsächlicher Stuff
- Epilogue
Pr/Ep für Sicherung von Variablen und Reservierung von Platz auf dem Stack (via SP)

## Von-Neumann-Architektur
1. Struktur des Rechners unabhängig von bearbeitetem Problem
2. Rechner besteht aus vier Werken:
   Hauptspeicher (RAM)
   Leitwerk (CPU)
   Rechenwerk (CPU)
   Ein-/Ausgabewerk inkl. Sekundärspeicher (Peripherieanschluss, Festplatte)
3. Hauptspeicher hat Zellen gleiche Größe mit Adressen
4. Programm & Daten stehen in selbem Speicher und können durch die Maschine verändert werden
5. Die Maschine nutzt Binär
6. Programm besteht aus Folge von Befehlen
7. Von der Folge kann durch Sprünge abgewichen werden
   Unterprogrammaufrufe:
	   1. Register sichern, Parameter supplien
	   2. Springen (Jump and Link)
	   3. Operation
	   4. Zurückspringen (Jump and Link)
## Exception
![[Pasted image 20251104173149.png]]
## Cache
Idealerweise enthält ein möglichst kleiner Zwischenspeicher, die als nächstes benötigten Daten, damit schneller auf sie zugegriffen werden kann.
Aber was wird als nächstes benötigt?
*zeitliches Lokalitätsprinzip*: vor kurzem verwendete Daten
*räumliches Lokalitätsprinzip*: benachbarte Daten zu zuvor verwendeten

Wie geht dann Schreiben? 2 Möglichkeiten:
- Schreiben in den Cache (bei Löschen aus Cache auch Hauptspeicher updaten)
- Schreiben in den Hauptspeicher (bei Lesen aus Cache neu aus Hauptspeicher holen)

Was wird wo im Cache gespeichert?
Einteilung Speicheradresse in

| Tag                | Index                | Offset              |
| ------------------ | -------------------- | ------------------- |
| ID/Alias von Zeile | ID von Speichermenge | innerhalb von Zeile |
|                    |                      |                     |
## Mehrere Adressräume
Jedes Programm hat eigenen Speicherraum mit virtuellen Adressen, und nur innerhalb dieses Adressraums Zugriff
Virtuelle Adresse wird immer auf physische übersetzt von MMU (früher Hardware) via Seiten-Kachel-Tabelle (auch mehrere Ebenen möglich)
4KiB Kacheln abgebildet auf 4KiB Kacheln (heutzutage auch größere möglich)
Nur Teil des Adressraums jedes Programms ist tatsächlich im Speicher angelegt, bei Bedarf wird erweitert
Was wenn Programm zugeschriebener Speicher nicht erfüllt werden kann weil keine Kacheln verfügbar? Freimachen beliebiger (lange ungenutzter) Kachel durch Auslagern auf Hintergrundspeicher/Festplatte
## Strings
C-String endet mit 0x0
Pascal String beginnt mit Zahl als Länge
# Wille
## ?
### Logic Hazards
### BDT (Binary Decision Tree)
#### Reduktion
easy, S-und I-Reduktion
### ITE (If-Then-Else)
