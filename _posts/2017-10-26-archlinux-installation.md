---
layout: post
title: Archlinux Installation Leitfaden
categories: Linux
---
Nach dem ich heute erfolgreich den Blog aufgesetzt habe kommt auch schon 
der erste richtige Post. :-)

Wie man am Titel erkennen kann, handelt es sich um einen Leitfaden für 
eine Archlinux installation.

Im großen und ganzen nach folgender Anleitung vorgehen 
[Anleitung](https://wiki.archlinux.de/title/Anleitung_f%C3%BCr_Einsteiger)

### genfstab
- bei genfstab -UP verwenden --> fstab wird mit UUID erzeugt 

### syslinux als Bootloader
- syslinux funktioniert nicht auf ext4-Partitionen --> seperate ext2 
Partition für den Bootloader (~500MB)
- syslinux auf UUID umstellen, statt root=/dev/sd.., root=UUID=... (UUID 
erhält man von "/etc/fstab" bzw. "sudo blkid"

### Ruhezustand
- SWAP gleich groß/größer als RAM
- resume nach udev bei HOOKS in /etc/mkinitcpio.conf hinzufügen
- resume=UUID=... zu /boot/syslinux/syslinux.cfg hinzufügen

### Pacman/Yaourt
sudo paccache -rk 3 && sudo paccache -ruk 0 ... pacman-cache aufräumen behalte nur 3 alte Versionen von installierten sachen und 0 von nicht installierten

oder

yaouer -S pacman-cleanup-hook .. selbe nur über pacman hooks
