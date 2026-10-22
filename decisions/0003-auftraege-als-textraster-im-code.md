---
status: entschieden
version: 1
datum: 2026-10-03
basiert-auf: 1@v1
tags: datenformat
betrifft: Ablesetour-Desktop.html:LEVELS
---

# Aufträge als Textraster im Code

## Frage

Wie werden die Häuser und Fahrlevel beschrieben?

## Entscheidung

Jeder Auftrag ist ein Eintrag in LEVELS mit Name, Hausart, Notiz, drei Zeitschwellen (par) und einem Raster aus Textzeilen (map), in dem jedes Zeichen für Wand, Tür, Möbel oder Gerät steht; dazu die Laufwege der Bewohner und Tiere (npcs).

## Begründung

Ein Level lässt sich ohne Editor direkt im Code bauen und lesen, und es bleibt in der einen Datei.

## Konsequenzen

Neue Bauteile brauchen ein neues Zeichen und eine Bauanweisung (build…-Funktion).

## Verlauf

- 2026-10-03 · v1 entschieden · Manuel
