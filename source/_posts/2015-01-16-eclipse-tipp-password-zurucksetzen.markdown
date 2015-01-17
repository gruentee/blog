---
layout: post
title: "Eclipse-Tipp: Passwort zurücksetzen"
date: 2015-01-16 02:25:51 +0100
comments: true
categories: 
- Eclipse
- Software
- Linux
- Java
- Tipp
---

Eclipse ermöglicht es, ein Master-Passwort zu vergeben, damit man die u.U. zahlreichen Passwörter für Git-Repositories oder ähnliches benötigt, nicht bei jedem Einloggen erneut abrufen muss, sondern in einer Art Datenbank speichern kann.
Manchmal kommt es vor, dass man dieses Passwort vergisst…

Für diesen Fall kann man es wie folgt zurücksetzen.
<!--more-->
### Über die Einstellungen
In der Menü-Toolbar:

_Fenster > Benutzervorgaben > Allgemein > Security > Secure Storage_

Hier im Reiter *Contents* den Eintrag löschen, fertig!

Sollte diese Methode nicht funktionieren, kann man es auch manuell versuchen.

### Manuell
1. Falls Eclipse läuft, beenden!
2. Das Verzeichnis ```~/.eclipse/org.eclipse.equinox.security``` löschen
3. Eine neue Text-Datei mit einem neuen Passwort, vorzugsweise im ```~/.eclipse```-Verzeichnis erstellen, `echo "password" > ~/.eclipse/master`
4. Im Eclipse-Programmverzeichnis (oft `/usr/share/eclipse`) in der Datei `eclipse.ini` folgende Parameter *ganz oben* ergänzen:
```
-eclipse.password
/home/user/.eclipse/master
```

Nach dem Neustart von Eclipse wird das neue Passwort verwendet
*****
Quelle: [StackOverflow: Eclipse secure storage](https://stackoverflow.com/questions/4223059/eclipse-secure-storage)

