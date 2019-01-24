# inovex class: Linux

Ziel:

- Einloggen auf einem bereitgestellten Server mit einem eigenen Benutzer per SSH mit dem Public Key Verfahren.

## Aufgaben

Bitte bearbeitet folgende Aufgaben chronologisch. Alle notwendigen Informationen sind in den Folien zu finden. Ansonsten gerne Fragen.

### Eigenen SSH Key generieren

Als Vorbereitung für spätere Aufgaben wird im ersten Schritt ein SSH Key Paar erzeugt um damit später die Authentifizierung durchzuführen. SSH bietet neben der Passwort Authentifizierung auch ein Public Key Verfahren an, das auf zwei Keys (public, private) basiert.

- Ein SSH Key Paar erzeugen

Hinweis:

- Windows: Putty unterstützt bei der Erzeugung
- macOS/OSX/Linux/[WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win11) > Terminal.app > `ssh-keygen -t rsa -b 4096  -f my_key.id_rsa`

### SSH via User+Passwort

Die Authentifizierung der SSH Verbindung zur Kursumgebung basiert zunächst auf User und Passwort.

- SSH Verbindung zur Kurs-Umgebung per User + Passwort herstellen:
  - macOS/Linux[WSL]: `ssh ubuntu@<ip-address>`
  - Putty: Neue Verbindung anlegen.

Hinweis:

- Der Default Benutzer auf der Kursumgebung: `ubuntu`

### Eigenen Benutzer einrichten

Nachdem eine Session besteht, wird ein eigener Benutzer angelegt. Der neue Benutzer wird im Anschluss modifiziert und um eine "authorized_keys" Datei erweitert. Diese Datei enthält den oben erzeugten SSH Public Key.

- Eigenen Benutzer anlegen 
- Ein Passwort für den Benutzer vergeben
- Als neuer Benutzer anmelden
- Im eigenen Home Directory ein Verzeichnis für ssh config anlegen (Hinweis: `.ssh`)
- In diesem Ordner eine Datei "authorized_keys" erstellen
- Die "authorized_keys" soll nur der eigene Benutzer lesen und schreiben können und sonst niemand
- Den erstellten Public (!) key in die "~/.ssh/authorized_keys" einfügen

### SSH per Public Key

Bevor weitere Aktionen durchgeführt werden soll die Public Key Authentifizierung getestet werden. Dazu muss der eigene Client modifiziert werden um den oben erstellen SSH Private Key zu verwenden.

- Zusätzliche Session um sich per Public Key zu authentifizieren

Hinweis:

- Es sollte logischerweise keine Passwort Abfrage erscheinen.
- macOS/Linux[WSL]: `ssh <eigener-user>@<ip-address> -i my_key.id_rsa`
- Putty: Die bestehende Verbindung um den Key erweitern.

### SSH Dienst konfigurieren

Nachdem die Public Key Autentifizierung funktioniert wird die Passwort-Authentifizierung deaktiviert. Dazu sind Konfigurationsänderungen am SSH Dienst notwendig. Im Anschluss wird der SSH Dienst neu gestartet.

- Als einfaches Backup eine Kopie der SSH Daemon Config erstellen (`/etc/ssh/sshd_config`)
- In der SSHD Config folgende Zeilen editieren:
  - `PermitRootLogin yes` wird zu `PermitRootLogin no`
  - `PasswordAuthentication yes` wird zu `PasswordAuthentication no`
- Vergleiche die neue Datei mit dem Backup
- Neustarten des SSH Dienstes
- Status des SSH Dienste einsehen
- Mit einer zusätzlichen Session einloggen und über das Auth.log prüfen wie die Autentifzierung abläuft
  - `/var/log/auth.log`
- Versuchen sich per SSH ohne Public Key einzuloggen

## Bonus

Die folgenden Aufgaben sind zusätzlich falls am Ende noch Zeit übrig ist oder als Vertiefung für danach.

### Navigation im Filesystem

- Was machen die Befehle `pushd` & `popd` ? 
- Ich bin in `/etc/ssh` und tippe ein  `cd /home/`. Wie komme ich elegant nach `/etc/ssh` zurück?
- Bitte das erstellte Backup von /etc/ssh/sshd_config wieder löschen

### Benutzer & Berechtigungen

- Wieviele Sessions sind auf dem System gerade offen?
- Was bewirkt `chmod -R 777 /etc/` ?
- Wo ist das Home-Dir von `root`?

### Dateien

- Wie kann ich in der Ausgaben von `ls -l` die Größe in ein Menschenlesbares Format verwandeln? 
- Wie kann ich die Anzahl der Zeilen in einer Datei zählen? 
- Wie kann ich die Ausgabe von `ls -l` sortieren?

### Dienste

- Wie lange ist der SSH Dienst auf dem System gestartet?

### Shell

Per `history` lassen sich bereits eingegebene Befehle einsehen. 

- Wie kann man die gesamte History löschen?
- Wie kann man einzelne Befehle aus der History löschen?
- Wie kann ich interaktiv bereits einmal eingegebene Befehle durchsuchen? (Stichwort: Bash reverse search)