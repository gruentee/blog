---
layout: post
title: "SoFS per WebDAV auf dem Linux-Rechner (ArchLinux)"
date: 2014-11-24 22:01:56 +0100
comments: true
categories: ["SoFS", "Universität Köln", "Tips & Tricks", "Linux", "WebDAV", "Cloud", "Anleitung", "HowTo", "ArchLinux"]
---

> Mit SoFS stehen Studierenden und Beschäftigten der Universität zu Köln online und kostenlos 10 GB Speicherplatz zur Verfügung.
> Mit SoFS können Sie Dateien auf einem leistungsfähigen Server ablegen und in Ordnern verwal­ten. Diese können Sie zum gemeinsamen Arbeiten mit Anderen benutzen und zwar überall dort, wo Sie Zugang zum Internet haben

Das Rechenzentrum der Uni Köln (RRZK) bietet die Möglichkeit, per [WebDAV](https://de.wikipedia.org/wiki/WebDAV) auf diesen Online-Speicherplatz zuzugreifen.

Die WebDAV-Adresse für den "privaten Bereich" ist
``` bash
https://sofsdav.uni-koeln.de/private/<smail-Benutzername>
```
und muss dementsprechend in den Beispielen eingesetzt werden.

Ich habe das für meinen Linux-Desktop eingerichtet, auf dem [ArchLinux](https://archlinux.org) läuft.

Für das Einbinden von WebDav-Quellen ist die Software ```davfs``` notwendig, erhältlich in den [offiziellen Repositories](https://www.archlinux.org/packages/?name=davfs2).
<!--more-->
Die Installation könnte per Paketverwaltung mit dem Tool der Wahl so geschehen:
``` bash DAVfs installieren

pacman -S davfs2
```

Generell kann die Einbindung nun per ```mount```-Befehl erfolgen:
``` bash WebDAV-Ressourcen mit mount

mount.davfs http://localhost:8080/ /mnt/dav
mount -t davfs http://localhost:8080/ /mnt/dav
```

### Dauerhaftes Einbinden ohne Passwort
Um in Zukunft bequem per mount <Ordername> die entsprechende Ressource einbinden zu können, muss ein Eintrag in der ```/etc/fstab``` angelegt werden.
Beispielsweise folgender:

``` bash Eintrag in fstab
https://webdav.example.com /home/username/webdav davfs user,noauto,uid=username,file_mode=600,dir_mode=700 0 1
```

Um das mounten als regulärer Nutzer zuzulassen, müssen außerdem die Rechte des aktuellen Benutzers erweitert werden:
``` bash Nutzer zur Gruppe network hinzufügen
usermod -a -G network username
```

#### Passwort sicher in Datei hinterlegen
Damit nicht jedes Mal das Passwort neu eingegeben werden muss, kann es als Datei im Home-Ordner hinterlegt werden:

```bash davfs-Secrets in Datei hinterlegen
$ mkdir ~/.davfs2/
$ echo "https://webdav.example.com webdavuser webdavpassword" >> ~/.davfs2/secrets 
$ chmod 0600 ~/.davfs2/secrets
```

Nun kann man als regulärer Nutzer mit einem einfach ```mount```-Aufruf das SoFS-Verzeichnis einhängen.


***
Quellen:

- [Davfs im Archlinux Wiki](https://wiki.archlinux.org/index.php/Davfs)
- [RRZK - SoFS - Zugangswege](http://rrzk.uni-koeln.de/12274.html)
