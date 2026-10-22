# Fabled Lands – Companion App

Offline-fähige PWA als digitaler Begleiter für die **Fabled Lands** Gamebook-Serie (Dave Morris & Jamie Thomson): Abenteuerbogen, Codewörter, Paragraphen-Tracker und Würfel.

**Live:** https://wundi77.github.io/fabled-lands/

## Features
- Charakterbogen mit Stamina, Defence, 6 Fähigkeiten, Besitztümern, Segen, Titeln und Wiederbelebung
- Quest-Tracker und Schiffsverwaltung
- 239 Codewörter mit Suche und Filter
- Paragraphen-Tracker für Bücher 1–7 mit Lesezeichen, Verlauf, Orten und Notizen
- Würfel-Dialog: Fähigkeitsprobe mit Wahrscheinlichkeit und Kampf-Simulator (auch mit echten Würfeln)
- Mehrere Spielstände und Snapshots, Backup als Datei oder Zwischenablage
- Charakter-Assistent mit Beispiel-Charakter beim ersten Start
- Installierbar als App (iOS/Android), funktioniert offline

## Dateien
```
index.html     – gesamte App (HTML + CSS + JS)
manifest.json  – PWA-Manifest
sw.js          – Service Worker (Offline-Cache)
icon*.png/svg  – App-Icons
NOTIZ.md       – detaillierte Projektnotizen
CLAUDE.md      – Arbeitsanweisungen für Claude
```

## Entwicklung
Kein Build nötig. Nach Änderungen committen und auf `main` pushen, GitHub Pages deployed automatisch.
