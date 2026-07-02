# Fabled Lands – Interaktiver Charakterbogen
## Projektstand & Entwicklungsnotizen

**Letzter Stand:** 02.07.2026 – CLAUDE.md erweitert (Session-Start-Überblick, Kontext-Komprimierung ab 40%, direktes Arbeiten auf main statt Feature-Branches, Skill-Check)  
**Live-URL:** https://wundi77.github.io/fabled-lands/  
**Repository:** https://github.com/wundi77/fabled-lands  

---

## Was ist das?

Eine offline-fähige PWA (Progressive Web App) als interaktiver digitaler Charakterbogen für die **Fabled Lands** Gamebook-Serie von Dave Morris & Jamie Thomson. Entwickelt als einzelne HTML-Datei, gehostet auf GitHub Pages, installierbar auf dem iPad als Home-Screen-App.

---

## Projektstruktur

```
fabled-lands/
├── index.html      ← Gesamte App (HTML + CSS + JS in einer Datei)
├── manifest.json   ← PWA-Manifest für Home-Screen-Installation
├── sw.js           ← Service Worker für Offline-Fähigkeit
├── icon.png        ← App-Icon (optional, noch nicht vorhanden)
└── NOTIZ.md        ← Diese Datei
```

---

## Implementierte Features

### Seiten / Navigation
- **Character** – Hauptcharakterbogen (Startseite)
- **Quests** – Questtracker mit 4 Spalten (What / From / Where / For)
- **Ship's Manifest** – Schiffsverwaltung
- **Codewords** – Alle Codewörter alphabetisch gruppiert
- **Book 1–7** – Paragraphen-Tracker + Notizen je Buch (Book 7 in einer Seite)

### Character-Seite
- Name, Profession, God, Rank, Defence
- 6 Fähigkeiten mit nummerierten Medaillons (Charisma, Combat, Magic, Sanctity, Scouting, Thievery)
- Current / Maximum Stamina
- Possessions: dynamisch erweiterbar (+ Add Item / ✖ löschen)
- Money, Blessings, Resurrection Arrangements, Titles & Honours
- Alle Textfelder wachsen automatisch mit dem Inhalt

### Quests-Seite
- Zeilen mit 4 Feldern: What / From / Where / For
- Dynamisch erweiterbar (+ Add Quest)
- Einzelne Zeilen löschbar (✖)
- Alle Felder auto-resize

### Ship's Manifest
- Mehrere Schiffe möglich (+ Add Ship / ✖ Remove)
- Je Schiff: Type, Name, Crew Quality, Cargo Capacity, Current Cargo, Where Docked, Notes
- Automatische Nummerierung

### Codewords
- Alle ~239 Codewörter aus Fabled Lands (Acid – Gush)
- Alphabetisch nach Buchstaben gruppiert mit rotem Trenner
- Abgehakte Wörter: fett + rot (kein Durchstreichen)
- „Uncheck All"-Button

### Buch-Seiten (Book 1–7)
- Alle Paragraphen aus dem Original-PDF als Checkboxen
- Notizen aus dem PDF als kleine Hinweistexte (z.B. „Town House", „Money Invested")
- Mehrfach-Checkboxen wo im Original mehrere Haken vorgesehen (z.B. 4×, 3×)
- Abgehakte Paragraphen durchgestrichen
- Freies Notizfeld je Buch (auto-resize)

### Speichern / Laden
- Mehrere benannte Spielstände via **localStorage**
- **⬆ Export** – alle Spielstände als `.json`-Datei herunterladen
- **⬇ Import** – JSON einfügen um Spielstände wiederherzustellen
- „Reset All" setzt aktuelle Felder zurück (Spielstände bleiben erhalten)

### Design
- Holztisch-Hintergrund mit CSS-Maserungslinien
- Pergament-Karten (parchment gradient)
- Goldene Akzentfarben, rote Überschriften
- Schriften: Palatino (systemseitig, keine externe Abhängigkeit)
- Vollständig offline-fähig (keine CDN-Abhängigkeiten)

### PWA
- `manifest.json` mit korrekten Pfaden für `/fabled-lands/`
- Service Worker (`sw.js`) cached alle Dateien beim ersten Laden
- `apple-mobile-web-app-capable` Meta-Tags für iOS
- Installierbar über Safari → Teilen → Zum Home-Bildschirm

---

## Offene Punkte / Mögliche Erweiterungen

- [ ] App-Icon (`icon.png`) erstellen und hochladen
- [ ] Spielstand-Export direkt als benannte Datei (z.B. `held-name.json`)
- [ ] Farbmarkierungen für Paragraphen (z.B. grün = erledigt, gelb = offen)
- [ ] Suchfunktion für Codewörter
- [ ] Druckansicht / PDF-Export des Charakterbogens
- [ ] Dark/Light Mode Toggle
- [ ] Mehrsprachigkeit (aktuell: Englisch)

---

## Technische Details

- **Keine externen Abhängigkeiten** – alles inline in `index.html`
- **Keine Frameworks** – reines HTML/CSS/JavaScript
- **localStorage** für Spielstände (bleibt beim App-Update erhalten solange Origin gleich bleibt)
- Alle dynamischen Elemente (Schiffe, Quests, Possessions) werden über JS-Counter (`shipCount`, `questCount`, `possCount`) verwaltet
- Codewörter werden beim Init aus zwei Arrays zusammengeführt und alphabetisch gruppiert
- Buchparagraphen werden aus einem `BOOKS`-Objekt dynamisch gerendert

---

## Weiterentwicklung mit Claude Code

Das Projekt kann direkt mit Claude Code weiterbearbeitet werden:

```bash
git clone https://github.com/wundi77/fabled-lands.git
cd fabled-lands
```

Dann Claude Code starten und auf den Ordner verweisen. Nach Änderungen:

```bash
git add .
git commit -m "Beschreibung der Änderung"
git push
```

GitHub Pages deployed automatisch nach jedem Push (ca. 1–2 Minuten).
