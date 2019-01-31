# inovex class: Paketverwaltung

## Ziel:

Installation des Webservers NGINX durch die Ubuntu Paketverwaltung mit `apt` und Inbetriebnahme des Dienstes mithilfe von `systemd`

## Aufgaben

Bitte bearbeite folgende Aufgaben chronologisch. Alle notwendigen Informationen sind in den Folien zu finden. Ansonsten gerne Fragen.

### Installation eines Pakets

Benutze das Paketverwaltungstool `apt` um das Paket `nginx` zu installieren.

### Status eines Dienstes

Stelle mithilfe `systemd` sicher, dass der Dienst `nginx` läuft.
Überprüfe, ob der Webserver läuft, indem du die auf eurem System gehosteten Webseite aufrufst.

### Deaktiveren einer Webseitenkonfiguration

Deaktivierte die Webseitenkonfiguration `default`.
Überprüfe, ob die Webseite verschwindet, indem du die gleiche Seite, wie zuvor aufrufst.

Hinweis:
* Die neue Konfiguration muss erst geladen werden, bevor Änderungen sichtbar werden.

### Aktivieren einer Webseitenkonfiguration

Reaktiviere die `default` Konfiguration.
Überprüfe, ob die Webseite wieder erreichbar ist.

### Reload vs Restart I

Lade die Konfiguration des Dienstes neu.
Anschließend starte den Dienst neu.
Was fällt dir auf?

### Reload vs Restart II

Füge in der Webseitenkonfiguration eine schließende geschweifte Klammer an `}`.
Lade die Konfiguration des Dienstes neu.
Anschließend starte den Dienst neu
Was fällt dir auf?

### Vollständige Deinstallation von Paketen

Entferne das Paket `nginx` inklusive aller Abhänigkeiten und Konfigurationen.
Überprüfe ob das Verzeichnis `/etc/nginx` noch existiert.

## Bonus

### Überprüfen einer Paketversion
Finde raus welche Version des Pakets `nginx` in den Paketquellen enthalten ist.

### Installation eines Pakets aus Drittquellen
Installiere die aktuellste stable Version von `nginx`.
Anschließend schau dir die Konfiguration in `/etc/nginx` an.
Was fällt dir auf?

### Anpassen der Default Seite von NGINX
Verändere den Inhalt der Webseite.

Hinweis:
* Sieh dir die Webseitenkonfiguration an, um herauszufinden wo der Quellcode der Seite abgelegt ist.
