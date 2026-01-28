---
tags: orga
fertig: false
---
# Einführung, Teil 1-2
ts is free vro
# Teil 3: Testen
## Testklassen
# Teil 4: Kontrollstrukturen  
broooo free
# Teil 5: Felder 
auch free außer
## Matrixmultiplikation
# Teil 6: Einige Abstrakte Datentypen
## Allgemein
## Liste
## Queue
## Stack
# Teil 7: Objektorientierung 
## Vererbung
## Polymorphie!
## Abstraktion/Interfaces
# Teil 8: Rekursion
rekursion schmekursion sag ich immer
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
***
[^1]: datentypen können weggelassen werden, (aber nur wenn man es mit allen macht), dann wird inferred
## Berühmte Interfaces (aus `java.util.function`)
- `Supplier<T>`: hat Methode `get()`, gibt Objekt vom Typ `T` zurück
- `Consumer<T>`: hat Methode `accept()`, konsoomiert Objekt vom Typ `T` und macht damit was
- `Function<T,R>`: hat Mehode `apply()`,  nimmt ein Objekt `T` und gibt ein Objekt `R` zurück
- `Predicate<T>`: hat Methode `test()`, nimmt ein Objekt `T` und gibt `boolean` zurück
- `Comparator<T>`: hat Methode `compare()`, vergleicht zwei Objekte `T` und gibt `int` zurück, der sich zu 0 verhält wie der erste Wert zum zweiten
## Streams
- **! Stream kann nur eine terminale Operation bekommen, aber wird auch erst durch diese ausgeführt**
- *Erstellen*
	- `Stream.of(n,m,...)` aus festen Werten
	- `Stream.generate(insertSupplierName)` aus Supplier (infinite amount of elements!)
	- `StreamSupport.stream(insertIterableName.spliterator(), false)` aus Iterables
	- `Arrays.stream(insertArrayName)` aus Array
	- `insertCollectionName.stream()` aus Collections (Listen, Sets, ...) 
- *Intermediate*
	- `map()` macht shit auf jedem Element des streams und gibt neuen zurück (**Function**)
		- Datentyp ändern mit casting oder auch z.B. `mapToInt()` bei supported Typen
			- (Dann kriegt man auf Datentyp ausgerichteten Stream mit extra Methoden wie `avg()`)
		- **braucht terminale Option zum funktionieren**
		- `flatMap()` hat als 2. argument nicht wieder ein `T` Objekt sondern, einen `Stream<T>`, so können pro Wert >1 neue Werte entstehen
	- `filter()` filtered nach **Predicate**
	- `takeWhile()` nimmt Werte weiter solange **Predicate** zutrifft, dann stopp
	- `limit(n)` nimmt die ersten `n` Elemente
	- `distinct()` self explanatory
	- `peek()` wie `foreach()` aber consumed nicht -> **braucht terminale Option zum funktionieren**
- `sorted` braucht `Comparator`, es gibt standard aber an kann auch seinen eigenen machen
- `toArray()` braucht Referenz für Konstruktor der Klasse
- *Terminal*
	- `foreach()` macht generell shit ohne return **Consumer**
	- `collect()` in Collection speichern (z.B. `Collectors.toList()`)
	- `count()`
	- `findAny()` beliebiges Element finden (als Optional)
	- `max`/`min(comparator)`
	- `reduce(startWert,accumulator)` reduziert auf einen Wert (using accumulator, erst Startwert mit Element 1, dann das Ergebnis mit Element 2, ...)
- `parallel()` parallele Bearbeitung, nicht deteministisch!
- Debugging
	- Erst am Ende parallelisieren, damit ensured ist dass der Rest funzt
	- In IntellJ ist ass, lieber print
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
# Teil 11: GUIs
my tip gui