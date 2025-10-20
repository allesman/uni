beinhaltet 3 Dinge
1. Terminal Emulator
   - Liest Eingabe und zeigt Ergebnisse an
2. PTY/TTY
   - Kommunikation zwischen Emulator und Shell
3. Shell
   - Interpretiert die eingegebenen Commands
   - z.B. PowerShell, Bash, zsh, (cmd)
   - POSIX (Standard für Shell Sprach, System Programme etc.), nur bash etc.
Eingaben und Ausgaben für Programme:
- Environment Variables (global)
	- PATH wird durchsucht nach Programmnamen
- CLI Arguments (bei Programmstart an Programm übergeben)
	- Options
		- Long Option (`--`) vs Short Option `-`
		- Option ohne Argument = Flag
	- Arguments (Dateien,cm Pfade, etc.)
- stdin/stdout/stderr (laufender Stream)