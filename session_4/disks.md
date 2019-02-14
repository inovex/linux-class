# Disks, Filesystems & Co.


## Ziel

Wir wollen eine größere Datenmenge auf unserer Linux-Maschine ablegen
Die verbaute Festplatte hat nicht ausreichend Kapazität
Eine zusätzliche Festplatte wurde verbaut und verkabelt

## Aufgaben

- Finde heraus, welchen Namen die neue Festplatte hat
- erzeuge eine Auflistung über die Partitionen auf der neuen Festplatte
- lege eine Partition auf der neuen Festplatte an
- Erzeuge ein ext4-Dateisystem auf der neuen Festplatte
- Erzeuge einen Einhängepunkt (“mountpoint”) auf dem System
- Hänge die Festplatte ins System ein
- Sorge dafür, dass die Festplatte nach einem System-Neustart automatisch eingehängt wird


## Cheatsheet

- lsblk - lists information about all available or the specified block devices
- fdisk - Partition table manipulator for Linux
- mkfs - create an ext4 filesystem 
- mkdir - make directories 
- mountpoint - see if a directory is a mountpoint
- mount - mount a filesystem
- umount - unmount file systems