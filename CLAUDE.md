# Fabled Lands – Projektanweisungen für Claude

## Bei Sitzungsstart / Fortsetzung

Zu Beginn jeder (neuen oder fortgesetzten) Sitzung zuerst das Repository `wundi77/fabled-lands` ansehen (Branches, letzte Commits, aktuelle Dateien wie `NOTIZ.md`/`README.md`) und sich so einen Überblick über den aktuellen Stand verschaffen, bevor mit der eigentlichen Aufgabe begonnen wird.

## Kontext-Management

Sobald die Kontextnutzung ca. 40% erreicht, den bisherigen Chatverlauf zusammenfassen und komprimieren, damit die Konversation übersichtlich bleibt.

## Vor jedem Git-Push

**Immer** vor einem `git push` zuerst die folgenden Dateien mit aktuellen Informationen aktualisieren:

- **NOTIZ.md** – Projektstatus, neue Features, offene Aufgaben, technische Notizen
- **README.md** – Kurzbeschreibung des aktuellen Stands für Außenstehende

Beide Dateien müssen den neuen Stand widerspiegeln, bevor der Push-Commit erstellt wird.

## Branch-Strategie

Änderungen **nicht** über Feature-Branches einreichen, sondern direkt auf `main` committen und pushen. Keine neuen Branches für dieses Projekt anlegen, außer der Nutzer verlangt es ausdrücklich.

## Design-Canvas (Optik-Entwürfe)

Basis für Optik-Anpassungen ist der Design-Canvas „Fabled Lands – iPad Redesign“: https://claude.ai/artifact/DkwfobReC7WsjYv2KPt1Qv (Artboards für Web, Desktop, Tablet, Phone). Ablauf bei Layout-Wünschen: zuerst den Canvas lesen und dort die Änderung vornehmen, danach den Entwurf in `index.html` übertragen, Doku aktualisieren und auf `main` pushen. Der Canvas zeigt das Layout vor der Umsetzung und kann vom aktuellen Code abweichen; im Zweifel zuerst den Code (`index.html`) mit dem Canvas vergleichen.

## Skills prüfen

Bei jeder Bearbeitung kurz prüfen, ob es sinnvolle, bereits installierte Skills gibt, die für die Aufgabe passen, oder ob auf skills.sh weitere passende Skills verfügbar wären. Falls ja, dem Nutzer einen Hinweis geben und nachfragen, ob diese installiert/genutzt werden sollen.
