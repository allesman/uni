---
tags: orga
fertig: false
klausur: 2026-02-09T00:00:00.000Z
moodle: "[[https://eidi.tum.sexy]]"
semester: 1
---
![[Altkausuren]]
# Einführung, Teil 1-2
ts is free vro
- Geheimnisprinzip -> Abstraktionsebene -> erleichtert Wartung
- Bei Methodenaufruf werden gegebene Parameter für Ausführung der Methode kopiert
- [[Abstract Keyword]]
- [[Array]]
## Call-by-Value (Referenzen)#
Java übergibt **Kopien der Referenz**. `arr[0]=1` ändert das **Original-Objekt im Heap**. `arr = new int[1]` ändert nur die **lokale Kopie** der Referenz und hat außen keine Auswirkung.
# Teil 3: Testen
## Testklassen
assert
nicht Objekte mit \=\= vergleichen
base case, edge cases
# Teil 4: Kontrollstrukturen  
broooo free
# Teil 5: Felder (arrays)
auch free außer
## Matrixmultiplikation
```
for i in zeilen:
	for j in spalten:
		skalarprodukt(i,j)
		
skalarprodukt(a,b):
	for i,j in a,b:
		output+= i*j
```
# Teil 6: Einige Abstrakte Datentypen
- [[Bubble Sort]]
- Radix Sort
## Allgemein
### Implementierung
#### Komposition statt Vererbung!
Wird eine Datenstruktur A durch Nutzung einer anderen Struktur B implementiert, ist **Vererbung (`A extends B`) suboptimal**, da B nicht **gekapselt** bleibt (Bsp: `Stack extends ArrayList` erbt `add(0,x)`, was **LIFO bricht**). Durch **Komposition** (B als Attribut) bleibt man **flexibel**, falls B später gegen eine andere Struktur ausgetauscht werden soll.
#### Generische Datentypen
Die generische Form **`A<B>`** macht primär dann Sinn, wenn B den **Typ der in A gespeicherten Elemente** definiert (z.B. eine Liste von B-Objekten).
## Liste
### Queue (FIFO)
#### RingBuffer (FIFO)
### Stack (LIFO)
# Teil 7: Objektorientierung 
## Vererbung
## Polymorphie!
### Statischer vs. Dynamischer Typ
Der **statische Typ** bestimmt die sichtbaren **[[#Methodensignatur|Methodensignaturen]]** für den Compiler; der **dynamische Typ** bestimmt die ausgeführte **Implementierung** der JVM.
### Methodensignatur
Name (nicht Return-Type), Parametertypen und Reihenfolge (nicht Namen)
aka ==public static int== **method**(**String **==hallo,== **int** ==hallo==)
### Generics & Bounds
Bei `A<U extends C>` ist die Konstruktion **`new A<C>()`** erlaubt, da für die Typprüfung und Generics **jede Klasse als Subtyp ihrer selbst** betrachtet wird.
### Ambiguity Error
Ein **Compile-Fehler**, wenn der Compiler bei überladenen Methoden **keine eindeutige Signatur** als "besten Match" bestimmen kann.
### Casting
```java
oldStaticType object = new dynamicType();
newStaticType object = (newStaticType) object;
```

Erstellt ein neues Objekt mit dem alten **dynamischen** und dem in Klammern angegebenen neuen **statischen** Typ.
Ein **Upcast** (von extender auf extendee) schränkt die **Sichtbarkeit** auf Methoden ein, die im **statischen Zieltyp** deklariert sind.

## Abstraktion/Interfaces
![[Pasted image 20260131162811.png|500]]
## Enums
# [[#Teil 8: Rekursion]]
rekursion schmekursion sag ich immer
- [[Binary Tree]]
- [[Binary Search]]
## Endrekursion (Tail-Call)
# Teil 9: Fortgeschrittene Programmierkonstrukte  
## Iteration
- `Iterable`implementieren
  -> `iterator()` bereitstellen
- `iterator()` returnt ein Objekt einer Klasse, die `Iterator` implementiert
  -> muss Methoden `hasNext()` & `next()` bereitstellen
## Lambda Expressions

| aus:                                           | kann man machen:                                     | Erklärung                                 |
| ---------------------------------------------- | ---------------------------------------------------- | ----------------------------------------- |
| `dtyp methode(dtyp param, ...)`<br>`{ stuff }` | `(dtyp`[^1]`param, ...) -> {stuff [..] return wert}` | kein methodenname nötig, aber dafür pfeil |
| `(...)` <br>`{ return wert }`                  | `(...) -> wert`                                      | nur 1 anweisung: direkt return            |
| `dtyp methode(dtyp param)`<br>`{...}`          | `param -> {...}`                                     | nur 1 parameter                           |
`::` Methode einer Klasse/static Objekt auswählen

[^1]: datentypen können weggelassen werden, (aber nur wenn man es mit allen macht), dann wird inferred
## Berühmte Interfaces (aus `java.util.function`)
| **Interface**        | **Funktion**            | **Erklärung / Logik**                                                                                    |
| -------------------- | ----------------------- | -------------------------------------------------------------------------------------------------------- |
| **`Supplier<T>`**    | `T get()`               | Liefert einen Wert vom Typ `T`.                                                                          |
| **`Consumer<T>`**    | `void accept(T a)`      | Nimmt einen Wert `T` an und macht "shit" damit, ohne etwas zurückzugeben.                                |
| **`Function<T, R>`** | `R apply(T a)`          | Nimmt `T` an und gibt ein Resultat `R` zurück.                                                           |
| **`Predicate<T>`**   | `boolean test(T a)`     | Prüft eine Bedingung und gibt `true` oder `false` zurück.                                                |
| **`Comparator<T>`**  | `int compare(T a, T b)` | Vergleicht zwei Objekte:<br>`a > b` -> `return > 0`<br>`a == b` -> `return 0`<br>`a < b` -> `return < 0` |
## Streams
### Erstellen
- `Stream.of(n,m,...)` aus festen Werten
- `Stream.generate(insertSupplierName)` aus Supplier (infinite amount of elements!)
- `StreamSupport.stream(insertIterableName.spliterator(), false)` aus Iterables
- `Arrays.stream(insertArrayName)` aus Array
- `insertCollectionName.stream()` aus Collections (Listen, Sets, ...) 
### Stream-Methoden

> [!danger] Genau eine terminale Operation pro Stream!
> Stream kann nur eine [[#*Terminal*|terminale Operation]] bekommen, aber erst durch diese werden die [[#*Intermediate*|intermediate Operationen]] überhaupt erst ausgeführt!

#### Intermediate
| **Methode**       | **Erklärung**                                                                                                                                                                                                                                                                                        |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`map()`**       | macht shit auf jedem Element des streams und gibt neuen zurück (**Function**). Datentyp ändern mit [[#Casting]] oder auch z.B. `mapToInt()` bei supported Typen (dann kriegt man auf Datentyp ausgerichteten Stream mit extra Methoden wie `avg()`). **Braucht terminale Option zum funktionieren.** |
| **`flatMap()`**   | hat als 2. argument nicht wieder ein `T` Objekt sondern, einen `Stream<T>`, so können pro Wert >1 neue Werte entstehen.                                                                                                                                                                              |
| **`filter()`**    | filtered nach **Predicate**.                                                                                                                                                                                                                                                                         |
| **`takeWhile()`** | nimmt Werte weiter solange **Predicate** zutrifft, dann stopp.                                                                                                                                                                                                                                       |
| **`limit(n)`**    | nimmt die ersten `n` Elemente.                                                                                                                                                                                                                                                                       |
| **`distinct()`**  | self explanatory.                                                                                                                                                                                                                                                                                    |
| **`peek()`**      | wie `foreach()` aber consumed nicht -> **braucht terminale Option zum funktionieren**.                                                                                                                                                                                                               |
| **`sorted()`**    | braucht [[#Berühmte Interfaces (aus `java.util.function`)\|Comparator]], es gibt standard aber man kann auch seinen eigenen machen.                                                                                                                                                                  |
| **`parallel()`**  | parallele Bearbeitung, nicht deteministisch!                                                                                                                                                                                                                                                         |
#### Terminal
| **Methode**                 | **Erklärung**                                                                                                     |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **`foreach()`**             | macht generell shit ohne return, aka nimmt einen [[#Berühmte Interfaces (aus `java.util.function`)\|Consumer]]    |
| **`collect()`**             | in Collection speichern (z.B. `Collectors.toList()`).                                                             |
| **`toArray()`**             | braucht Referenz für Konstruktor der Klasse.                                                                      |
| **`count()`**               | self explanatory.                                                                                                 |
| **`findAny()`**             | beliebiges Element finden (als Optional).                                                                         |
| **`max`/`min(comparator)`** | findet das Maximum oder Minimum basierend auf dem Comparator.                                                     |
| **`reduce(startWert,acc)`** | reduziert auf einen Wert (using accumulator, erst Startwert mit Element 1, dann das Ergebnis mit Element 2, ...). |

> [!success] Consumer anwenden ohne Termination
> Um `foreach()`-Style Operationen vorzunehmen (z.B. Attribute der enthaltenen Objekte modifizieren) **ohne den Stream zu terminieren** (weil man danach noch z.B. sortieren will), kann man stattdessen Operationen wie **`map()` oder `peek()`** nutzen. Diese werden aber logischerweise nur ausgeführt, wenn der Stream später noch terminiert wird.
### Speichereffizienz
Streams sind **lazy** und verarbeiten Daten **"on-the-fly"**, was sie **speichereffizienter** macht als persistente Collections im RAM.
## I/O
- `Path` ist ein Interface, du kannst Objekt von Klasse, die dieses implementiert erstellen mit `Path.of("x/y/z")`
	- entweder Path zu File,
		- dann kann man mit `Files.readString()` und `Files.writeString()` self explanatory shit machen
		- oder mit `Files.write()` Iterables und so reinschreiben
		- oder mit `Files.readAllLines()` Lines als Stream lesen
	- oder Path von Directory, dann gibts `Files.walk()`, was n gefüllten Stream ausgibt

# Teil 10: Nebenläufigkeit  
## Threads
- `Thread` vs `Runnable`
	- `Runnable`
		- etwas, das wir machen
		- aka Liste von Anweisungen
		- plainstes Interface, das keine Paramter nimmt und nichts zurückgibt
	- `Thread`
		- kann `Runnable` übergeben bekommen, um zu festlegen was er tun soll
- IMMER `start()` benutzen, nie `run()`
- `wait()` braucht
	- Handling für `InterruptedException` (`try/catch` oder mit `throws` nach oben geben)
	- (bei auf Objekt) *Ownership* des Objekts via `synchronized(obj)`
- `join()` aufrufen -> warten bis thread fertig ist.
- `synchronized` als
	- wrapper, dann "auf" einem Objekt,
		- direkt der ressource, wenn sie ein objekt ist, sonst
		- einem boilerplate objekt
	- methodendings, äquivalent zu wrapper für ganze methode auf `this`
- `volatile` ist `synchronized` light (Race Conditions passieren noch, aber kein Caching sondern es wird direkt mit RAM geschrieben und gelesen)
- Race Conditions -> Monitor -> Deadlock -> Semaphor, Lock, etc.
	- `Semamphore(n)` mit `n` als Anzahl Permits
		- `acquire()` nimmt 1 Permit, wartet falls 0 ist
		- `release()` gibt 1 Permit zurück
- [[JVM Intricacies]]
# Teil 11: GUIs
my tip gui


bis Bubble Sort von Isaac



[[Altklausur 2017]]