# inovex class: Grundlagen Benutzerverwaltung

## Ziel:

Einführung in die Linux Benutzerverwaltung und Übersicht der wichtigsten Kommandos.


## Aufgaben

* wende das Kommando __*stat -c "%A %n"*__ auf eine beliebige Datei an, welche Ausgabe erhälst Du? Ergänze die Parameter damit du zusätzlich die Ausgabe der Zugriffsrechte in Octaler Schreibweise erhälst. Hinweis: lies die Manual Page (__*man*__ Kommando)  

Lösung:
- `stat --help`
- `stat -c "%A %a %n`
* welche Option des Kommandos __*who*__ erzeugt eine ähnliche Ausgabe zu __*whoami*__? Hinweis: Verwende die Hilfeoption __*--help*__ oder lies die Manual Page (__*man*__ Kommando)  

Lösung:
- `man who`
- `who am i`/ `who bin ich`
* Was ist der Unterschied zwischen den Kommandos __*chmod u=rw-,g=---,o=---*__ und __*chmod 0600*__? Teste beides an einer beliebigen Datei. Hinweis: __*touch spielwiese.txt*__ erzeugt Dir eine  

Lösung:
- `touch spielwiese.txt`
- `chmod u=rw-,g=---,o=--- spielwiese.txt`/ `chmod u=rw,g=-,o=- spielwiese.txt`
- `chmod 0600 spielwiese.txt` Oktalschreibweise lässt sich schneller angeben


## Bonusaufgaben

* was bedeutet das sogenannte "SUID Bit" (-rwsr-xr-x) bei den Dateirechten des Eigentümers von __*/usr/bin/passwd*__? Hinweis: verwende __*ls -l*__ und google nach __*linux man setuid*__  

Lösung:
- bei Ausführung der Datei werden immer die Rechte des Dateibesitzer verwendet - nur verwenden wenn man weiß was man tut! - damit kann das Sicherheitskonzept des Dateisystems umgangen werden
