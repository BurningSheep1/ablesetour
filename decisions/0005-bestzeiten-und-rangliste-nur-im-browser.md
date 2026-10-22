---
status: entschieden
version: 1
datum: 2026-10-20
basiert-auf: 1@v1, 4@v1
tags: daten
betrifft: Ablesetour-Desktop.html, README.md
---

# Bestzeiten und Rangliste nur im Browser

## Frage

Wo werden Bestzeiten und Ranglisten gespeichert?

## Entscheidung

Im localStorage des Browsers: Bestzeit je Auftrag (ablesetour.best), Rangliste mit den zehn schnellsten Läufen je Auftrag (ablesetour.rank) und der zuletzt eingetragene Name. Schafft eine Zeit die Top 10, kann man auf dem Ergebnisbildschirm seinen Namen eintragen, die Top 3 stehen im Auftragsbriefing.

## Begründung

Kein Server nötig, das Spiel bleibt eine Datei. Für Familie und Freunde am selben Gerät reicht das.

## Konsequenzen

Ranglisten gelten nur pro Gerät und Browser und gehen beim Löschen der Browserdaten verloren. Ist localStorage gesperrt, läuft das Spiel ohne Speichern weiter.

## Verlauf

- 2026-10-20 · v1 entschieden · Manuel
