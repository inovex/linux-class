# inovex class: Paketverwaltung

## Ziel:

Installation des Webservers NGINX durch die Ubuntu Paketverwaltung mit `apt` und Inbetriebnahme des Dienstes mithilfe von `systemd`

## Aufgaben

Bitte bearbeite folgende Aufgaben chronologisch. Alle notwendigen Informationen sind in den Folien zu finden. Ansonsten gerne Fragen.

### Installation eines Pakets

Benutze das Paketverwaltungstool `apt` um das Paket `nginx` zu installieren.  
Lösung:
- `sudo apt-get update`
- `sudo apt-get install nginx`/ `sudo apt install nginx`

### Status eines Dienstes

Stelle mithilfe `systemd` sicher, dass der Dienst `nginx` läuft.
Überprüfe, ob der Webserver läuft, indem du die auf deinem System gehosteten Webseite aufrufst.  
Lösung:
- `sudo systemctl status nginx` => running
- von lokal mit Browser die URL der VM aufrufen => welcome to nginx...

### Deaktiveren einer Webseitenkonfiguration

Deaktivierte die Webseitenkonfiguration `default`.
Überprüfe, ob die Webseite verschwindet, indem du die gleiche Seite, wie zuvor aufrufst.  
Lösung:
- `sudo rm /etc/nginx/sites-enabled/default`
- von lokal mit Browser die URL der VM aufrufen => welcome to nginx...
- `sudo systemctl reload nginx` => connection refused


Hinweis:
* Die neue Konfiguration muss erst geladen werden, bevor Änderungen sichtbar werden.

### Aktivieren einer Webseitenkonfiguration

Reaktiviere die `default` Konfiguration.
Überprüfe, ob die Webseite wieder erreichbar ist.  
Lösung:
- `sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/`
- `sudo systemctl reload nginx`
- von lokal mit Browser die URL der VM aufrufen => welcome to nginx...

### Reload vs Restart I

Lade die Konfiguration des Dienstes neu.
Anschließend starte den Dienst neu.
Was fällt dir auf?  
Lösung:
- `sudo systemctl reload nginx`
- `sudo systemctl restart nginx`
- reload ist etwas schneller als restart

### Reload vs Restart II

Füge in der Webseitenkonfiguration eine schließende geschweifte Klammer an `}`.
Lade die Konfiguration des Dienstes neu.
Anschließend starte den Dienst neu
Was fällt dir auf?  
Lösung:
- `sudo nano /etc/nginx/sites-available/default`, `}` einfügen
- `sudo systemctl reload nginx`
- `sudo systemctl status nginx` => Dienst läuft noch
- `sudo systemctl restart nginx` => Dienst läuft nicht mehr

### Vollständige Deinstallation von Paketen

Entferne das Paket `nginx` inklusive aller Abhänigkeiten und Konfigurationen.
Überprüfe ob das Verzeichnis `/etc/nginx` noch existiert.  
Lösung:
- `sudo apt-get purge nginx`
- `sudo apt-get autoremove --purge`
- `ls -l /etc/ | grep nginx` => kein nginx Ordner mehr vorhanden

## Bonus

### Überprüfen einer Paketversion
Finde raus welche Version des Pakets `nginx` in den Paketquellen enthalten ist.  
Lösung:
- `sudo apt-get update`
- `sudo apt-cache show nginx`

### Installation eines Pakets aus Drittquellen
Installiere die aktuellste stable Version von `nginx`.
Anschließend schau dir die Konfiguration in `/etc/nginx` an.
Was fällt dir auf?  
Lösung:
- `lsb_release -c` => bionic
- `sudo nano /etc/apt/sources.list.d/nginx.list`
- Folgende Zeilen hinzufügen:
    - deb http://nginx.org/packages/ubuntu/ bionic nginx
    - deb-src http://nginx.org/packages/ubuntu/ bionic nginx
- `sudo apt-get update`
- `sudo apt-get install nginx`
- `ls /etc/nginx/`
    - es existieren keine Debian/Ubuntu spezifischen Ordner `sites-available` und `sites-enabled`
    - die Webseitenkonfiguration liegt unter `conf.d`

### Anpassen der Default Seite von NGINX
Verändere den Inhalt der Webseite.  
Lösung:
- `less /etc/nginx/conf.d/default` => root /var/www/html
- `sudo nano /var/www/html/default` => beliebige html Anpassungen
- von lokal mit Browser die URL der VM aufrufen => sich über seine Änderungen freuen :)

Hinweis:
* Sieh dir die Webseitenkonfiguration an, um herauszufinden wo der Quellcode der Seite abgelegt ist.
