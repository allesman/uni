- Verbindung mit Shell eines anderen Geräts
- Secure, auch in ungesicherten Netzwerken
- Fingerprint zur Überprüfung ob Host stimmt
- Authentifizierung via
	- Passwort (nicht so nice)
		- `ssh benutzername@service`
	- [[SSH#SSH Keys|Keys]]
		- `ssh -i publickeypfad benutzername@service`
- Authentifizierungsmethode in config file (bei default name für key nicht zwingend nötig)
	- dann `ssh alias`


# SSH Keys
`ssh-keygen`
- erstellt public und private key
- optional passphrase, aber ist empfehlenswert für sicherheit
`ssh-copy-id -i publickeypfad benutzername@service` oder in web-interface