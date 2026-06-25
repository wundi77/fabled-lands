# Fabled Lands – Interaktiver Charakterbogen

Eine offline-fähige PWA als digitaler Charakterbogen für die **Fabled Lands** Gamebook-Serie (Dave Morris & Jamie Thomson).

**Live:** https://wundi77.github.io/fabled-lands/

## Features
- Charakterblatt mit 6 Fähigkeiten, Stamina, Possessions
- Quest-Tracker, Schiffsmanifest
- 239 Codewörter mit Checkbox-Tracking
- Paragraphen-Tracker für Bücher 1–7 mit Originalnotizen
- Mehrere Spielstände via localStorage, JSON-Export/Import
- Vollständig offline (kein CDN, kein Framework)
- Installierbar als PWA (iOS/Android)

## Dateistruktur
```
index.html    – gesamte App (HTML + CSS + JS)
manifest.json – PWA-Manifest
sw.js         – Service Worker (Offline-Cache)
NOTIZ.md      – detaillierte Projektnotizen
CLAUDE.md     – Anweisungen für Claude Code
```

## Entwicklung
Nach Änderungen an `index.html` einfach committen und pushen – GitHub Pages deployed automatisch.
