# Fabled Lands – Companion App

Offline-fähige PWA als digitaler Begleiter für die **Fabled Lands** Gamebook-Serie (Dave Morris & Jamie Thomson): Abenteuerbogen, Codewörter, Paragraphen-Tracker und Würfel.

**Live:** https://wundi77.github.io/fabled-lands/

## Features
- Charakterbogen mit Stamina, Defence, 6 Fähigkeiten, Besitztümern, Segen, Titeln und Wiederbelebung
- Quest-Tracker (What / From / Where) und Schiffsverwaltung
- 239 Codewörter mit Suche und Filter
- Paragraphen-Tracker für Bücher 1–7 mit Lesezeichen, Verlauf der letzten 12 Orte, Orten und Notizen sowie Häusern (eingelagerte Gegenstände) und Banken (investiertes Geld) je Buch
- Würfel-Dialog: Fähigkeitsprobe mit Wahrscheinlichkeit, Kampf-Simulator und freie Würfel (Spare dice, 1–6 W6), auch mit echten Würfeln
- Mehrere Spielstände, nur manuelles Speichern („Save“ / „Save as“), Export als Backup-Datei (JSON) oder PDF-Übersicht, Backup auch über die Zwischenablage
- Charakter-Assistent mit Beispiel-Charakter beim ersten Start
- Installierbar als App (iOS/Android), funktioniert offline

## Dateien
```
index.html     – gesamte App (HTML + CSS + JS)
manifest.json  – PWA-Manifest
sw.js          – Service Worker (Offline-Cache)
icon*.png/svg  – App-Icons
design/        – Optik-Entwürfe (Quelldateien des Design-Canvas, siehe design/README.md)
NOTIZ.md       – detaillierte Projektnotizen
CLAUDE.md      – Arbeitsanweisungen für Claude
```

## Entwicklung
Kein Build nötig. Lokal arbeiten und auf `main` committen; gepusht wird nur auf Anweisung, danach deployed GitHub Pages automatisch.
