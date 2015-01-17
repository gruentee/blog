---
layout: post
title: "Einfaches Suchen und Ersetzen mit Vim"
date: 2015-01-10 19:23:33 +0100
comments: true
categories: 
- vim
- Linux
- Software
- Tips
- Editor
---

Das `substitute`-Kommando ist ein sehr mächtiges Werkzeug zum Suchen & Ersetzen von Mustern in Text. 
Die allgemeine Syntax des Befehls lautet:

:[_adr1_[,_adr2_]]s/_alt_/_neu_/[_flags_]

Wird der Ersetzungsteil weggelassen (`:s/muster//`), wird das Muster durch "nichts" ersetzt, also _gelöscht_.

### Grundlegende Optionen

`%s/foo/bar/g` Findet jedes Vorkommen von "foo" auf allen Zeilen und ersetzt es mit "bar".

`s/foo/bar/g` Findet jedes Vorkommen von "foo" in der aktuellen Zeile und ersetzt es mit "bar".

`%s/foo/bar/gc` Alle "foo"s durch "bar" erstetzen, vor Ersetzen nach Bestätigung fragen

`%s/\<foo\/>/bar/gc` Nur exakte Treffer ersetzen, dabei nach Bestätigung fragen (`c`)

### Flags

**Flag &nbsp;&nbsp;** |**Bedeutung**
-----|----------
c    | Jede Ersetzung muss bestätigt werden
g    | Alle Vorkommen von _alt_ werden in jeder Zeile zu _neu_ geändert (global).
p    | Die Zeile wird ausgegeben, nachdem die Veränderung vorgenommen wurde.



*****
Siehe auch ["vi und Vim - kurz & gut" (Amazon.com)](http://www.amazon.com/s/?tag=duc0c-20&url=search-alias%3Daps&field-keywords=9783897213210)
