# Fabled Lands – Projektanweisungen für Claude

## Bei Sitzungsstart / Fortsetzung

Zu Beginn jeder (neuen oder fortgesetzten) Sitzung zuerst den Stand ermitteln, bevor mit der eigentlichen Aufgabe begonnen wird:

1. `git fetch origin` und lokalen Stand mit `origin/main` vergleichen (Branches, letzte Commits). Liegt GitHub vorn (z. B. Uploads über den Browser), `git pull --ff-only` ausführen. Lehnt Git das ab, weil lokale und GitHub-Commits auseinanderlaufen, beide Seiten dem Nutzer zeigen und vor Merge oder Rebase nachfragen, nie stillschweigend mergen.
2. `NOTIZ.md`, `README.md` und `design/README.md` lesen.
3. Weicht der lokale Stand von GitHub ab (lokale Commits, die noch nicht gepusht sind), dem Nutzer kurz sagen, was lokal noch aussteht.

## Kontext-Management

Sobald die Kontextnutzung ca. 40% erreicht, den bisherigen Chatverlauf zusammenfassen und komprimieren, damit die Konversation übersichtlich bleibt.

## Lokal arbeiten, Push nur auf Anweisung

Der Nutzer bearbeitet das Projekt lokal. GitHub (`wundi77/fabled-lands`) bleibt die Sicherung und liefert den aktuellen Stand.

- Änderungen direkt auf `main` committen, **nicht pushen**, bevor der Nutzer es ausdrücklich verlangt. Keine Feature-Branches anlegen, außer der Nutzer verlangt es ausdrücklich.
- **Vor jedem Push** zuerst `NOTIZ.md` (Projektstatus, neue Features, offene Aufgaben, technische Notizen) und `README.md` (Kurzbeschreibung) auf den neuen Stand bringen; haben sich Canvas-Dateien geändert, auch den Sync-Stand in `design/README.md`. Beide Dateien müssen den neuen Stand widerspiegeln, bevor der Push-Commit erstellt wird.
- Ein Stop-Hook kann nach Commit und Push verlangen, wenn Dateien unversioniert oder Commits ungepusht sind. Commits darf ich dann anlegen, gepusht wird trotzdem nur nach Rückfrage beim Nutzer.
- In Cloud-Sitzungen (claude.ai) ist der Container vergänglich: ungepushte Commits gehen mit dem Container verloren. Deshalb vor dem Ende einer Cloud-Sitzung den Nutzer ausdrücklich fragen, ob gepusht werden soll, und auf das Risiko hinweisen.

## Design-Canvas (Optik-Entwürfe)

Basis für Optik-Anpassungen ist der Design-Canvas „Fabled Lands – iPad Redesign“: https://claude.ai/artifact/DkwfobReC7WsjYv2KPt1Qv. Die Quelldateien liegen versioniert im Repo unter `design/canvas/project/` (Aufbau, Sync-Stand, Wiederherstellung: `design/README.md`). Auf claude.ai wird der Canvas grafisch angesehen und bearbeitet, im Repo ist er gesichert. Es darf nichts nur auf claude.ai liegen.

Ablauf bei Layout-Wünschen:

1. Canvas neu laden, da der Nutzer ihn von Hand geändert haben kann: erst Artifact-Tool `list` mit `scope: "files"`, dann alle `project/`-Pfade aus dem Ergebnis mit `read` und `paths` holen (so werden auch neue Artboards gefunden). Lokale Dateien in `design/canvas/project/`, die im Listing fehlen, wurden auf claude.ai entfernt und werden auch lokal gelöscht (sonst bringt eine Wiederherstellung sie zurück). Ist `list` mit `scope: "assets"` nicht mehr leer, die Assets ebenfalls sichern. Abweichungen zuerst nach `design/` übernehmen.
2. Änderung am Canvas vornehmen: Dateien in `design/canvas/project/` bearbeiten und mit `root` = `design/canvas` auf die Canvas-URL veröffentlichen (bei neuen oder verschobenen Artboards auch `canvas.json`).
3. Nach jeder Canvas-Änderung: Stand in `design/README.md` (Datum, Artifact-Version) aktualisieren und committen.
4. Gefällt der Entwurf, ihn in `index.html` übertragen, Doku aktualisieren und committen. Gepusht wird nur auf Anweisung.

Der Canvas kann vom Code abweichen. Bewusste Unterschiede stehen in `NOTIZ.md`. Im Zweifel `index.html` mit dem Canvas vergleichen und den Nutzer fragen, welche Fassung gilt.

## Skills prüfen

Bei jeder Bearbeitung kurz prüfen, ob es sinnvolle, bereits installierte Skills gibt, die für die Aufgabe passen, oder ob auf skills.sh weitere passende Skills verfügbar wären. Falls ja, dem Nutzer einen Hinweis geben und nachfragen, ob diese installiert/genutzt werden sollen.
