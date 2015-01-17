---
layout: post
title: "Linux-Befehl: patch – Änderungen an einer Datei vornehmen"
date: 2015-01-11 21:28:14 +0100
comments: true
categories: 
- linux
- befehl
- software
- programmierung
---

{% blockquote Linux man pages für patch https://www.mankier.com/1/patch online verfügbar auf mankier.com %}
patch takes a patch file patchfile containing a difference listing produced by the diff program and applies those differences to  one or  more original files, producing patched versions.
{% endblockquote %}

`patch` ermglicht es, zuvor mit dem `diff`-Befehl erstellte Patch-Dateien auf die Original-Datei anzuwenden, für welche die Änderungen gedacht sind.

Die Grundlegende Syntax lautet

```
patch < patch_datei
```

Da in der Patch-Datei die zu verändernde Datei bereits vermerkt ist, ist eine Nennung beim Aufruf nicht mehr nötig.

Mit der Option `-b` oder `--backup` kann eine Sicherungsdatei erstellt werden. Die Originaldatei wird dann umbenannt oder kopiert, anstatt sie zu löschen.

### Änderungen auf ganze Verzechnisse anwenden
Genau wie das `diff`-Werkzeug kann auch `patch` rekursiv auf Verzeichnisse und darin enthaltene Dateien angewendet werden:

{% codeblock lang:bash Mehrere Dateien patchen %}
patch -p1 < recipes.patch                                      
patching file recipes/README
patching file recipes/MelanzaneParmigiana.txt
{% endcodeblock %}

Das `-p`-Flag (alternativ `--strip`) gibt dabei an, wieviele Verzeichnis-Ebenen vom Anfang des Pfades zu den zu patchenden Dateien "abgeschnitten", d.h. ignoriert werden sollen. Syntax: -p*N*, wobei *N* die Anzahl der Ebenen ist.
Im Patch-File sind folgende Pfade angegeben, die ohne `--strip`-Parameter einen Fehler beim Patch auslösen würden:
```
--- a/recipes/README
+++ b/recipes/README
```

Da wir uns bereits auf einer Ebene mit dem Verzeichnis *recipes* befinden, sollen *a/* und *b/* beim Patchen ignoriert werden.


Mehr Infos gibt es auf der [Manpage für patch](https://www.mankier.com/1/patch).


-----
*Beispiele übernommen von den [OpenHatch Tutorial-Missionen](https://openhatch.org/missions/diffpatch/recursive_patch).*
