---
status: entschieden
version: 1
datum: 2026-10-03
tags: architektur
betrifft: Ablesetour-Desktop.html, README.md
---

# Das ganze Spiel in einer HTML-Datei ohne Build

## Frage

Wie wird das Spiel ausgeliefert und gestartet?

## Entscheidung

Alles steckt in einer einzigen Datei Ablesetour-Desktop.html: HTML, CSS und JavaScript, kein Build-Schritt, keine Installation. Starten durch Öffnen im Browser.

## Begründung

Das Spiel lässt sich ohne Werkzeuge weitergeben und überall öffnen, auch per Doppelklick ohne Server.

## Konsequenzen

Grafiken, Icons und Texturen werden im Code erzeugt (SVG-Pfade, Canvas), Töne über Web Audio. Die Datei ist groß (rund 3000 Zeilen) und schwer zu überblicken.

## Verlauf

- 2026-10-03 · v1 entschieden · Manuel
