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

