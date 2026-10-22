# Fabled Lands – Companion App
## Projektstand & Entwicklungsnotizen

**Letzter Stand:** 22.10.2026 – Komplette Überarbeitung der Oberfläche (aus einem anderen Chat) ist auf `main`; Doku auf neuen Stand gebracht  
**Live-URL:** https://wundi77.github.io/fabled-lands/  
**Repository:** https://github.com/wundi77/fabled-lands  

---

## Was ist das?

Eine offline-fähige PWA als digitaler Begleiter für die **Fabled Lands** Gamebook-Serie von Dave Morris & Jamie Thomson: Abenteuerbogen, Codewörter, Paragraphen-Tracker und Würfel. Eine einzelne HTML-Datei, gehostet auf GitHub Pages, installierbar auf dem iPad/iPhone als Home-Screen-App.

---

## Projektstruktur

```
fabled-lands/
├── index.html              ← Gesamte App (HTML + CSS + JS, ~1275 Zeilen)
├── manifest.json           ← PWA-Manifest (start_url ./, Icons any + maskable)
├── sw.js                   ← Service Worker (Cache fabled-lands-v2 + Font-Cache)
├── icon.svg                ← Favicon
├── icon-192.png            ← PWA-Icon
├── icon-512.png            ← PWA-Icon
├── icon-maskable-512.png   ← PWA-Icon (maskable)
├── apple-touch-icon.png    ← iOS-Home-Screen-Icon
├── CLAUDE.md               ← Arbeitsanweisungen für Claude
├── NOTIZ.md                ← Diese Datei
└── README.md               ← Kurzbeschreibung
```

---

## Implementierte Features

### Navigation
- Menü am rechten Rand (feste Tabs) mit Stamina-Anzeige, Seitenmarken „On this page" und Direktsprung zu Books 1–7 (mit Fortschritt je Buch)
- Eigene Tab-Schaltflächen für Lesezeichen (§) und Würfel
- Seiten: Character, Quests, Ships, Codewords, Book 1–7, Saves & Backup, New adventure (Assistent)

### Character
- Name, Beruf, Gott, Rang
- Stamina (aktuell/max) mit Leiste, Defence mit Anpassung, Geld
- 6 Fähigkeiten (Charisma, Combat, Magic, Sanctity, Scouting, Thievery) mit Berufs-Startwerten
- Besitztümer mit Typ und Bonus (fließen in Fähigkeiten/Defence ein)
- Segen (6 Fähigkeiten, Immunity to Disease, Safety from Storms), Titel & Ehren, Wiederbelebung (Text + Buch/Paragraph)

### Quests / Ships
- Quests mit What / From / Where / For, abhakbar (erledigt), Zähler im Menü
- Mehrere Schiffe: Type, Name, Crew (Poor/Average/Good/Excellent), Kapazität, Ladung, Liegeplatz, Notizen

### Codewords
- 239 Codewörter (Acid – Gush), nach Buchstaben gruppiert
- Suchfeld, Filter „Marked only", Sprungmarken pro Buchstabe, Zähler „x of 239 marked"

### Books 1–7
- Paragraphen-Tracker aus dem Original-Abenteuerbogen mit Notizen (z. B. „Town House", „Money Invested")
- Mehrfach-Kästchen (z. B. 4×, 3×) als Zähler mit Punkten
- Filter: All / Not yet / Ticked, Fortschrittsbalken je Buch
- Lesezeichen (Buch + §) mit Verlauf, „Known places" (Orte merken, antippen setzt Lesezeichen)
- Freies Notizfeld je Buch

### Würfel-Dialog
- **Ability check:** 2d6 + Fähigkeit gegen Schwierigkeit, zeigt nötigen Wurf und Erfolgswahrscheinlichkeit, Neuwurf mit passendem Segen (verbraucht ihn)
- **Fight:** Kampf-Simulator (Gegner mit Combat/Defence/Stamina, wer zuerst schlägt, Runden, Kampflog, Flucht, Sieg/Niederlage)
- Option „I roll physical dice": echte Würfel eingeben statt App-Wurf

### Speichern / Backup
- Mehrere Spielstände (Slots) in **localStorage**, Autosave nach 250 ms
- Snapshots („Save copy") zum Zurückgehen, z. B. vor riskantem Kampf
- Export als Datei, Import aus Datei, Backup in die Zwischenablage kopieren
- Backup-Format: `{ format: 'fabled-lands-companion', v: 1, exportedAt, active, slots }`
- Beim ersten Start wird der Beispiel-Charakter „Aldric Vane" angelegt
- Hinweis in der App, falls der Browser Speicherung blockiert
- Charakter-Assistent (3 Schritte): Name, Beruf, Gott; Start mit 9 Stamina, 16 Shards, Sword, Leather jerkin

### Design
- Pergament-Seiten, Lederrahmen, Siegelrot als Akzent, Gold für Hervorhebungen
- Schriften: Cinzel (Überschriften), EB Garamond (Text) über Google Fonts
- Ein festes helles Design (kein Dark Mode), `prefers-reduced-motion` wird beachtet
- Safe-Area-Insets für iPhone/iPad, responsives Spaltenlayout bis 1920 px

### PWA
- Service Worker: App-Dateien im Cache `fabled-lands-v2`, Google-Fonts in eigenem Cache, Navigation „network first" mit Offline-Fallback auf `index.html`
- `apple-mobile-web-app-*` Meta-Tags, Installation über Safari → Teilen → Zum Home-Bildschirm

---

## Offene Punkte / Mögliche Erweiterungen

- [ ] Alte Spielstände (`fl_saves` der Vorversion) werden **bewusst nicht übernommen** (nicht mehr benötigt)
- [ ] Fonts sind nur nach dem ersten Online-Laden offline verfügbar (Fallback: Palatino/Georgia)
- [ ] Dark/Light-Mode-Toggle
- [ ] Druckansicht / PDF-Export des Charakterbogens
- [ ] Mehrsprachigkeit (aktuell: Englisch)
- [ ] Alter Branch `claude/awesome-allen-uet0qq` auf GitHub manuell löschen (Löschen per Tool/Push wurde mit 403 abgelehnt)

---

## Technische Details

- **Keine Frameworks, kein Build** – reines HTML/CSS/JavaScript, nur Google Fonts extern
- Zustand in einem Objekt `G` (aktueller Spielstand) und `slots` (alle Stände); Oberfläche wird per Template-Strings neu gerendert (`render()`, `renderLayer()`)
- Eingaben über `data-bind` (Pfad in `G`/`UI`), Aktionen über `data-act`
- localStorage-Schlüssel: `flc_slots`, `flc_active`
- Regeldaten im Code: `AB` (Fähigkeiten), `PROFS` (Berufe), `BLESS`, `BOOKS` (Paragraphen, Notizen, Mehrfach-Kästchen), `CW` (Codewörter), `BOOK_TITLES`
- Wahrscheinlichkeit einer 2d6-Probe: `pAtLeast(n)` mit Tabelle `WAYS`

---

## Weiterentwicklung mit Claude

Arbeitsregeln stehen in `CLAUDE.md` (Repo-Überblick zu Sitzungsbeginn, Doku vor jedem Push aktualisieren, direkt auf `main` arbeiten, Skills prüfen).

```bash
git clone https://github.com/wundi77/fabled-lands.git
cd fabled-lands
```

GitHub Pages deployed automatisch nach jedem Push auf `main` (ca. 1–2 Minuten).
