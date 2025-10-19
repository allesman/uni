- `pwd` = Print Working Directory
- `cat` = Print File Content
- `mkdir`= Create Folder
- `rm`= Delete File
	- mit `-d`delete (empty directory) 
	- mit `-dr`delte recursively
- `touch`= eigentlich Zeitstempel anpassen, aber erstellt auch leere Dateien
- `mv`= Move Files
- `cp`= Copy File to different directory
- `sudo`(Substitute User do)

Control Operators
- `;`Trennung von Commands
- `&&`wenn exit code vom ersten erfolgreich, zweites wird auch ausgeführt
- `||` wenn exist code vom ersten fehlgeschlagen, zweites wird ausgeführt
- `&` Im Hintergrund laufen lassen
- `()` führt Inhalt in Subshell aus, z.B. mit eigenem CWD, aber "geerbt" von vorigem CWD
- `|` stdout des ersten *Programmes* -> stdin des zweiten *Programmes*

 Redirection Operators (wie `|`aber nicht Programm -> Programm)
 - `>` stdout -> Datei
 - `>>` stdout -> Datei angehängt
 - `<` sdtin <- Datei
 - `<<` sdtin <- Here-Document (braucht delimiter dahinter (für mehrere Here Documents))