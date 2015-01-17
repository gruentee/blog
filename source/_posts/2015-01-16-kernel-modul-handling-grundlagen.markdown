---
layout: post
title: "Kernel-Modul Handling: Grundlagen"
date: 2015-01-16 15:35:35 +0100
comments: true
categories: 
- Linux
- Kernel
- ArchLinux
- Befehle
---

{% blockquote  Artikel "Kernel modules" im ArchLinux Wiki https://wiki.archlinux.org/index.php/Kernel_modules ArchLinux Wiki (EN) %}
Kernel-Module sind Code-Fragmente, die bei Bedarf nachgeladen werden können. Sie erweitern die Funktionaliät des Kernels, ohne dass das System neugestartet werden muss.
{% endblockquote %}

### Informationen über Module bekommen
Mithilfe der folgenden Kommandos lassen sich verschiedene Informationen über Module anzeigen.

Anzeigen der _aktuell geladenen_ Module:
```
$ lsmod
```

Informationen über ein bestimmtes Modul anzeigen
```
$ modinfo modul_name
```

Aktuell _gesetzte Optionen_ für ein geladenes Modul anzeigen:
```
$ systool -v -m module_name
```

Ausführliche List der _Konfiguration aller Module_ anzeigen (Ausgabe wird nach `less` gepiped):
```
$ modprobe -c | less
```

Konfiguration _eines bestimmten Moduls_ anzeigen:
```
$ modprobe -c | grep module_name
```

_Abhängigkeiten eines Moduls_ anzeigen, das Modul selbst eingeschlossen:
```
$ modprobe --show-depends module_name
```


### Laden und blacklisten beim Systemstart

In Archlinux liegen die Konfigurationsdateien zum Laden zusätzlicher Kernelmodule im Verzeichnis `/etc/modules-load.d./`. 
Das Namensschema für neue Konfigurationsdateien ist `<programm>.conf`. 
In dieser Datei können Module einfach _zeilenweise_ eingetragen werden, (Kommentare sind mit `#` oder `;` möglich) und werden dann beim Systemstart berücksichtigt:

{% codeblock lang:bash /etc/modules-load.d/overlay.conf %}
# overlay-Modul beim Start laden
overlay
{% endcodeblock %}


