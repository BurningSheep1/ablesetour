---
status: entschieden
version: 1
datum: 2026-10-03
basiert-auf: 1@v1
tags: technologie
betrifft: Ablesetour-Desktop.html, README.md
---

# three.js r128 und Schriften aus dem Netz

## Frage

Womit wird die 3D-Grafik dargestellt, und woher kommen Bibliothek und Schriften?

## Entscheidung

three.js r128 wird von cdnjs geladen, die Schriften kommen von Google Fonts.

## Begründung

three.js nimmt die WebGL-Arbeit ab; per CDN bleibt die Datei klein und es gibt nichts zu installieren.

## Konsequenzen

Beim ersten Start braucht das Spiel eine Internetverbindung. Die Version ist fest auf r128, neuere three.js-Versionen haben Schnittstellen geändert.

## Verlauf

- 2026-10-03 · v1 entschieden · Manuel
