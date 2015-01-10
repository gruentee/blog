---
layout: post
title: "Vi/Vim: Datei als root speichern"
date: 2015-01-10 16:01:55 +0100
comments: true
categories: 
- Linux
- Software
- Tips
---

Manchmal kommt es vor, dass man – z.b. beim Editieren einer systemweiten Konfigurationsdatei – vergisst, Vim als
root-User auszuführen. Will man die Änderungen am Ende speichern, beschwert sich Vim über die fehlenden Rechte.

Doch es gibt einen Trick:

{% codeblock Datei als root speichern in Vi/Vim lang:bash %}
:w !sudo tee %
{% endcodeblock %}

* `:w` Das gewöhnliche Vi-Kommando zum Speichern einer Datei
* `!sudo` Das Shell-Kommando `sudo` ausführen
* `tee` Das UNIX-Kommando Schreibt die Ausgabe von `vim :w` als root nach `%`, was durch den aktuellen Dateinamen ersetzt wird.
