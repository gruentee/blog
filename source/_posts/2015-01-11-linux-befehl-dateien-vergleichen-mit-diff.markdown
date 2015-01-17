---
layout: post
title: "Linux-Befehl: Dateien vergleichen mit diff"
date: 2015-01-11 23:38:02 +0100
comments: true
categories: 
- linux
- programmierung
- software
---
Bei der gemeinsamen Arbeit an einem Software-Projekt kommt es oft vor, dass man die Änderungen anderer Entwickler auf die eigene Kopie der des Quellcodes übertragen muss. Damit man nicht von Hand jede einzelne geänderte Stelle heraussuchen muss, existiert das Werkzeug `diff`, mit dem Unterschiede in Dateien angezeigt und *Patches* erstellt werden können<sup>1</sup>.

### Beispiel
Die Original-Datei:
{% codeblock lang:text spruch.txt %}
Wer Ander'n eine Grube gräbt, fällt selbst herein.
{% endcodeblock %}

Nun legen wir eine Kopie der Datei an: ```cat spruch.txt > neu.txt```.
Ein schnelles ```:%s/her/hin/g``` in Vim macht "hinein" aus "herein".

Mit ```diff``` kann nun ein Patch erzeugt werden:

{% codeblock lang:bash Patch erstellen mit diff %}
diff -u spruch.txt neu.txt > korrektur.patch

cat korrektur.patch
--- spruch.txt2015-01-12 00:27:43.165909867 +0100
+++ neu.txt2015-01-12 00:28:17.965721341 +0100
@@ -1 +1 @@
-Wer Andern eine Grube gräbt, fällt selbst herein.
+Wer Andern eine Grube gräbt, fällt selbst hinein.
{% endcodeblock %}

### Verzeichnisse vergleichen
Mit ```diff``` können auch Verzeichnisse verglichen werden:
```
diff verzeichnis1 verzeichnis2
```

Mit dem ```-r```-Flag (*recursive*) werden darüber hinaus alle darin enthaltenen Unterverzeichnisse und Dateien verglichen.


-----
<sub>1</sub>Patches können dann mit dem Werkzeug `patch` auf die betreffende Datei angewendet werden.
