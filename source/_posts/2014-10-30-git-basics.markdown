---
layout: post
title: "Git Basics"
date: 2014-10-30 15:10:08 +0100
comments: true
categories: [Software Development, Version Control, Source Control, Commands]
---

entfernt eine Datei vom Git Index

```
git rm 
```


entfernt eine schon getrackte Datei aus Git
```
git rm --cached 
```


fügt eine Datei zum Index hinzu
```
git add 
```

alle geänderten Dateien in einem Verzeichnis und Unterverzeichnis adden

```
# ins Verzeichnis gehen

git add *
```


zeigt die im index markierten Dateien an

```
git status
```


commit

```
git commit -m "Commit Meldung"
```


## Merge

zum initialisieren eines neuen clones

```
git clone 
```


erstelle einen branch

```
git branch 
```


branch benutzen

```
git checkout <branch-name>
```


im aktiven branch (master zb) eingeben und dev nach master mergen

```
git merge dev
```


zeigt das git log an (letzte commits)

```
git log
git log --stat
gitk --all
```
