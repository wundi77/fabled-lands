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

## Skills prüfen

Bei jeder Bearbeitung kurz prüfen, ob es sinnvolle, bereits installierte Skills gibt, die für die Aufgabe passen, oder ob auf skills.sh weitere passende Skills verfügbar wären. Falls ja, dem Nutzer einen Hinweis geben und nachfragen, ob diese installiert/genutzt werden sollen.
