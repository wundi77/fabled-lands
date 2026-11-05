# design/ – Optik-Entwürfe (Design-Canvas)

Hier liegt die versionierte Kopie des Design-Canvas **„Fabled Lands – iPad Redesign“**. Die Originalansicht (grafisch ansehen und bearbeiten) lebt weiterhin auf claude.ai:

https://claude.ai/artifact/DkwfobReC7WsjYv2KPt1Qv

## Inhalt

```
design/canvas/project/
├── canvas.json            ← Index: Position/Größe aller Artboards, Reihenfolge, Notizen
├── Web.dc.html            ← Hauptkomponente (die gesamte App als Entwurf, ~156 KB)
└── Web*.dc.html           ← 20 Artboards (dünne Hüllen um Web.dc.html)
                             Desktop 1920: Character, Book, Bookmark, Check, Codewords, Quests, Saves, Ships
                             Phone 390:    Character, Bookmark, Create, Death, Discard, Export, Fight, Quests, Saves, Ships, Spare
                             Tablet 834:   Character
```

Nicht enthalten, weil nicht Teil des Projekts: `support.js`, Editor und Runtime. Sie gehören zum Artifact-Typ „Design“ und werden von claude.ai bereitgestellt. Hochgeladene Assets nutzt der Canvas nicht (Asset-Speicher leer, keine `_blob/`-Verweise).

## Sync-Stand

| | |
|---|---|
| Letzter Abgleich | 05.11.2026 |
| Artifact-Version | `1793646911-1d78` |
| Code-Stand | `index.html` aus Commit `a58125d` |

Hat sich der Canvas auf claude.ai nach diesem Datum geändert (z. B. per Hand), ist diese Kopie veraltet. Vor jeder Design-Arbeit deshalb zuerst neu herunterladen.

## Arbeitsablauf

1. **Vor der Arbeit:** Dateiliste mit dem Artifact-Tool `list` (`scope: "files"`) holen und alle `project/`-Pfade daraus mit `read` und `paths` laden (so werden auch neue Artboards gefunden). Nach `design/canvas/project/` kopieren, was sich unterscheidet. Lokale Dateien, die im Listing fehlen, wurden auf claude.ai entfernt und werden auch hier gelöscht, sonst bringt eine Wiederherstellung sie zurück. Ist die Asset-Liste (`scope: "assets"`) nicht mehr leer, Assets ebenfalls sichern.
2. **Ändern:** entweder direkt in den Dateien hier oder im Canvas auf claude.ai.
3. **Veröffentlichen/ansehen:** Artifact-Tool `publish` mit `url` = Canvas-URL, `root` = `design/canvas`, `file_path` = eine geänderte Datei, weitere geänderte Dateien in `files` (`"project/Name.dc.html": "project/Name.dc.html"`). `canvas.json` nur mitschicken, wenn Artboards hinzukommen, wegfallen oder verschoben werden.
4. **Nach jeder Canvas-Änderung:** geänderte Dateien zurück nach `design/` kopieren, Sync-Stand oben anpassen, committen.
5. **Entwurf in den Code übernehmen:** `index.html` anpassen, `NOTIZ.md`/`README.md` aktualisieren.

## Wiederherstellung (falls das Artifact verloren geht)

1. Neuen Canvas aus dem Artifact-Typ „Design“ anlegen (`type_url` https://claude.ai/artifact/QKN21svewxgyPb6SYRqWnd, Titel „Fabled Lands – iPad Redesign“).
2. `canvas.json` und alle `.dc.html` in **einem** Publish-Aufruf auf die neue URL veröffentlichen, mit `root` = `design/canvas`.
3. Neue URL in `CLAUDE.md`, `NOTIZ.md` und dieser Datei eintragen.

## Bekannte offene Punkte

- `Web.dc.html` enthält am Ende (Zeile ~924) einen losen deutschen Satz („Ich brauche jetzt auch bitte einmal eine Visualisierung für das Ausklapp-Fähnchen „Where Am I“ …“), der auf jedem Artboard sichtbar ist. Ob er entfernt werden soll, ist noch nicht entschieden.
- Bewusste Unterschiede zum Code stehen in `NOTIZ.md` im Abschnitt „Design-Canvas“.
