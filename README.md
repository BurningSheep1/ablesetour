# Ablesetour

Ein kleines 3D-Browserspiel über den Alltag im Messdienst. Du bist auf Herbsttour für den „Zählwerk Messdienst“: Wasserzähler ablesen, Heizkostenverteiler tauschen, Rauchwarnmelder prüfen. Und das so schnell wie möglich, ohne Bewohner umzurennen oder über Spielzeug zu stolpern.

Das ganze Spiel steckt in einer einzigen HTML-Datei. Es gibt keinen Build-Schritt und keine Installation.

## Starten

`Ablesetour-Desktop.html` im Browser öffnen, fertig.

Für die 3D-Grafik wird [three.js](https://threejs.org/) (r128) von cdnjs geladen, die Schriften kommen von Google Fonts. Beim ersten Start braucht das Spiel deshalb eine Internetverbindung.

## Steuerung

| Aktion | Tastatur | Touch |
| --- | --- | --- |
| Laufen / Fahren | `WASD` oder Pfeiltasten | links ziehen |
| Arbeiten (Gerät ablesen, tauschen, prüfen, parken) | `Leertaste`, `E` oder `Enter` gedrückt halten | rechts „Halten“ |
| Pause | `P` oder `Esc` | Pause-Knopf |
| Auftrag im Menü wählen | `1` bis `9`, `0` | antippen |
| Auftrag starten / nochmal | `Enter` | |
| Nächster Auftrag (Ergebnisbildschirm) | `N` | |
| Zurück zur Übersicht | `Esc` | |

## Spielprinzip

Jeder Auftrag ist ein Haus, in dem alle Geräte abgearbeitet werden müssen. Gewertet wird die Gesamtzeit aus **Laufzeit + Strafzeit**. Strafzeit gibt es zum Beispiel für Zusammenstöße mit Bewohnern und Tieren, für Unfälle beim Fahren, für Blitzer und geschlossene Schranken, für eine ausgelöste Alarmanlage oder wenn das Baby aufwacht.

Je nach Gesamtzeit gibt es einen Rang:

- **Obermonteur**
- **Monteur**
- **Azubi**
- **Praktikant**

Die Bestzeiten pro Auftrag speichert der Browser lokal (`localStorage`).

Jeder Auftrag hat außerdem eine eigene **Rangliste** mit den zehn schnellsten Läufen. Schafft eine Zeit es in die Top 10, kann man auf dem Ergebnisbildschirm seinen Namen eintragen. Die Top 3 stehen zusätzlich im Auftragsbriefing. Auch die Rangliste liegt nur im Browser (`localStorage`) und gilt deshalb pro Gerät.

### Geräte

| Gerät | Tätigkeit |
| --- | --- |
| Wasserzähler | Ablesen |
| Heizkostenverteiler | Tauschen |
| Rauchwarnmelder | Prüfen |
| Heizungsanlage | Ablesen |
| Rohrbruch | Abdichten |
| Parkplatz | Parken (in den Fahrleveln) |

### Aufträge

1. **Lindenweg 4**: Einfamilienhaus
2. **Hafenstraße 12**: Mehrfamilienhaus, 2. OG
3. **Stadtfahrt**: Innenstadt im Feierabendverkehr
4. **Am Schlossberg 7**: Altbau, 5er-WG
5. **Gartenstraße 3**: Messiewohnung, EG
6. **Baustellenfahrt**: Großbaustelle zur Rushhour
7. **Uferweg 1**: Atriumbungalow am Fluss
8. **Mühlweg 21, Keller**: Kellergeschoss mit Heizungsraum, im Dunkeln
9. **Hafenfahrt**: Containerhafen im Regen
10. **Birkenallee 9**: Doppelhaushälfte, Baby schläft
11. **Villa Sonnenhang**: Smart Home mit Alarmanlage
12. **Weihnachtsfahrt**: Altstadt bei Nacht im Schnee
13. **Hof Brandstätter**: Vierseithof im Januar

In den Fahrleveln steuerst du den Firmenwagen durch den Verkehr und musst am Ende einen Parkplatz finden.

## Technik

- Reines HTML, CSS und JavaScript in einer Datei
- 3D-Darstellung mit three.js r128
- Läuft am Rechner und auf dem Smartphone (Touch-Steuerung, Vibration, Safe-Area-Unterstützung)

## Lizenz

[MIT](LICENSE)
