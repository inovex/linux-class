# inovex class: Linux /Bash Basics

Ziel:

- Vertraut machen mit dem Bash Handling.

## Aufgaben

- Falls du eine einfache Shell gestartet hast, starte eine bash.  
  - `/bin/bash` oder permanent `usermod <username> -s /bin/bash`
- Schau dir mit "history" bereits abgesetzte Befehle an.
  - `history`
- Navigiere mit den Pfeiltasten durch alte Befehle
- Der Befehl "top" zeigt interaktiv den Systemzustand an. Starte ihn, schick ihn in den Hintergrund und hole ihn wieder nach vorne.
  - `top`
  - STRG+Z
  - `fg $1`
- Benutze die Reverse-Search
  - STRG+R
  - Suchanfrage eingeben
  - STRG+O <Kommando wiederholen und erneut eintippen>/ Enter <Kommando wiederholen>/ STRG+R <Rückwärtssuche fortsetzen>


## Bonusaufgaben

- Was ist der Unterschied zwischen "less" und "more"? 
  - `more <file>`: basic pager -> kein backscrolling
  - `less <file>`: more advanced pager -> inkl. backscrolling und Suchfunktion
- mit "alias" lassen sich Commands vereinfachen. Probiere die Commands "ll", "la" und "l" auss
  - `nano ~/.bash_aliases` bzw. `nano ~/.bashrc`
  - eigene Befehle definieren
  - `source ~/.bashrc`
  - eigene Befehle ausführen
