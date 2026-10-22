# Hinweise für KI-Assistenten

## Worum es geht

Kleines 3D-Browserspiel über den Alltag im Messdienst: in 13 Aufträgen Geräte
ablesen, tauschen und prüfen, so schnell wie möglich. Das ganze Spiel steckt in
`Ablesetour-Desktop.html` (HTML, CSS und JavaScript, three.js r128 von cdnjs),
ohne Build-Schritt.

## Befehle

- Starten: `Ablesetour-Desktop.html` im Browser öffnen.

## Regeln

- Nie selbst committen, das macht der Nutzer. Nach jeder Änderung an Dateien
  einen Commit-Text vorschlagen: kurze Betreffzeile auf Deutsch, bei Bedarf
  ein paar Zeilen dazu. Den Text ohne Anführungszeichen ausgeben, nur den
  Text selbst, damit er sich direkt kopieren lässt.

<!-- dec:start -->
## Entscheidungen dokumentieren

Entscheidungen zu diesem Projekt liegen in `decisions/` und werden mit dem
Kommandozeilenwerkzeug `dec` gepflegt.

**Vorher nachsehen.** Vor Änderungen an Architektur, Datenformat,
Abhängigkeiten oder grundlegendem Verhalten prüfen, ob eine bestehende
Entscheidung betroffen ist: `dec search` mit den Begriffen der Aufgabe und
eigenen Synonymen und Oberbegriffen — die Suche vergleicht nur Text, was eine
Entscheidung mit anderen Worten sagt, findet sie nur so. Beispiel CSV-Export:
`dec search csv export format bibliothek abhängigkeit`. Treffer mit
`dec show <nr>` ansehen. `dec list --file <pfad>` zeigt, welche
Entscheidungen eine Datei betreffen, `dec check`, was zur Prüfung ansteht,
`dec list -l` den Überblick. Nicht stillschweigend gegen eine bestehende
Entscheidung arbeiten — wenn die Aufgabe eine ändern würde, das dem Nutzer
sagen.

**Was festhalten.** Wahl von Technologie, Bibliothek, Datenformat oder
Schnittstelle; Architektur; bewusste Abwägungen und Einschränkungen, die man im
Code nicht sieht; naheliegende, aber verworfene Alternativen. Nicht: Bugfixes,
Benennungen, Details, die der Code selbst erklärt. Festhalten, was der Nutzer im
Gespräch entschieden hat, und was du im Rahmen der Aufgabe selbst entscheiden
musstest — Letzteres in der Antwort nennen, damit der Nutzer widersprechen kann.

**Wie ausführlich.** Architektur, Technologie, Datenformat und Schnittstellen
vollständig wie ein Architecture Decision Record (ADR): Frage mit Kontext,
Begründung, Konsequenzen (auch die Nachteile, die man in Kauf nimmt) und
verworfene Alternativen. Bei kleineren Entscheidungen genügen Entscheidung und
Begründung.

**Wie.** Immer alle Inhalte als Optionen übergeben, `dec` darf nicht auf
Eingaben warten (kein `dec edit` ohne Optionen, kein `dec ui`).

```bash
dec new "Ergebnis als Titel" -q "Was war zu entscheiden?" -d "Was jetzt gilt" \
  -r "Warum so" -k "Was daraus folgt, auch Nachteile" -a "Verworfene Alternativen" \
  --on 2,3 -t architektur --files src/db.js
dec new "Offener Punkt" -q "Was der Nutzer noch klären muss"     # ohne -d: offen
dec decide 3 -d "Neuer Stand" -r "Warum geändert"   # nur nach Zustimmung des Nutzers
dec edit 3 -r "Ergänzte Begründung"                 # Korrektur, keine neue Version
dec drop 3 --by 9 -m "Grund"                        # vollständig ersetzt
```

- Titel nennt das Ergebnis („PostgreSQL als Datenbank“), keine Frage.
- `--on` setzt die Grundlagen: Entscheidungen, deren Änderung diese hier
  infrage stellen würde.
- `--files` nennt Dateien oder Ordner, in denen die Entscheidung umgesetzt
  ist (auch `datei:symbol`), wenn sich das klar eingrenzen lässt. `dec check`
  meldet, wenn eine davon verschwindet; nachtragen mit `dec edit <nr> --files …`.
  Meldet es Commits oder nicht committete Änderungen an diesen Dateien seit
  der Entscheidung, siehe Abschluss.
- `--decided-by` nennt, wer entschieden hat, wenn der Nutzer das sagt und es
  nicht der Nutzer selbst war (z. B. „Kunde im Termin am 2026-10-02“). Gilt je
  Version, bei `dec decide` also erneut angeben.
- Ändert sich eine bestehende Entscheidung, `decide` statt `new`.
- `dec new` nennt verwandte Entscheidungen (gleiche Tags, ähnliche Begriffe).
  Auf Widerspruch prüfen und ggf. mit dem Nutzer klären; ist eine davon
  Grundlage, mit `dec link <neu> <grundlage>` verknüpfen.

**Bevor eine bestehende Entscheidung geändert wird** — auf Wunsch des Nutzers
oder weil die Aufgabe es verlangt: `dec show <nr> --impact` zeigt die
Folgeentscheidungen im Wortlaut. Jede einschätzen: bleibt, muss angepasst
werden oder unklar, je mit einem Satz Begründung. Das dem Nutzer vorlegen,
bevor `dec decide` läuft. Für Folgen, die angepasst werden müssen, dasselbe
eine Ebene tiefer (`darauf baut auf:` in der Ausgabe).

**Nach einer Neuentscheidung** meldet `dec`, welche Folgeentscheidungen zu
prüfen sind. Was der Nutzer in der Folgenabschätzung als „bleibt“ gesehen hat:
`dec confirm <nr> -m "Warum"`. Sonst mit dem Nutzer klären und neu
entscheiden. Nur bestätigen, was wirklich geprüft ist.

**Abschluss.** Die Dateien in `decisions/` gehören zur selben Änderung wie der
Code (gleicher Commit). Daher vor dem Commit `dec check`. Meldet es
Änderungen an betroffenen Dateien: jede Entscheidung gegen die Änderung prüfen
und dem Nutzer vorschlagen, welche weiterhin passen, je mit einem Satz
Begründung, z. B. „#3 bestätigen? cli.js: nur Hilfetext geändert“. Erst nach
seiner Zustimmung `dec confirm <nr> -m "Warum"`, dann kommt die Bestätigung
in denselben Commit. Passt eine nicht mehr, das sagen und mit dem Nutzer
klären. In der Antwort nennen, was festgehalten wurde, z. B.
„Festgehalten als #9, #4 bestätigt“. Wurden Dateien geändert, aber keine
Entscheidung festgehalten, kurz sagen, warum, z. B. „Keine Entscheidung
festgehalten: reiner Bugfix“.
<!-- dec:end -->
