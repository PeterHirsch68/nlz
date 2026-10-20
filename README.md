# SAD Football Performance – Version 1.0.0

Eine installierbare deutschsprachige Web-App (PWA) mit 15 digitalen Trainingsmodulen, Spielerprofilen, Trainer-Werkzeug, Ergebnishistorie, lokaler Datenspeicherung und GitHub-Pages-Deployment.

## Installation

Voraussetzung: Node.js 22+ und npm.

```bash
npm install
npm run dev
```

Lokale Entwicklung: Die in der Konsole angezeigte URL öffnen. Für eine veröffentlichungsfähige Version:

```bash
npm run build
npm run preview
```

## Veröffentlichung auf GitHub Pages

1. Neues GitHub-Repository `sad-football-performance` anlegen.
2. Den **Inhalt** dieses Projektordners (inkl. `.github`; eine `package-lock.json` wird beim ersten `npm install` erzeugt) auf Branch `main` pushen.
3. Unter **Settings → Pages → Build and deployment** als Source **GitHub Actions** auswählen.
4. Bei jedem Push auf `main` baut und veröffentlicht `.github/workflows/deploy.yml` automatisch die App.
5. Die veröffentlichte URL steht in der Pages-Konfiguration bzw. im Workflow.

## Updates

- App-Code und Version in `package.json`, `src/App.jsx` (`VERSION`) sowie `public/version.json` auf denselben neuen Versionswert setzen.
- Neue Versionshinweise in `public/version.json` hinterlegen.
- Änderungen nach GitHub pushen, GitHub Actions aktualisiert die veröffentlichte Version.
- Die App vergleicht im Einstellungsbereich die installierte Version mit `version.json`. Über „Neu laden“ kann die neue Version übernommen werden.
- Die PWA verwendet `public/sw.js` für Basis-Offlinefähigkeit. Für größere Updates den Cache-Bezeichner `CACHE` erhöhen, um alte App-Assets zu verwerfen.

**Wichtig:** Die Schaltfläche „Nach Updates suchen“ veröffentlicht nicht selbst neue Versionen und zieht keinen Quellcode direkt von GitHub; GitHub Actions muss zuerst erfolgreich deployen.

## Umfang der 15 Module

1. Visual Scanning: kurz sichtbare Spielerpositionen erfassen
2. Cognitive Decision: Entscheidungsfragen
3. Peripheral Vision: seitliche Signale am Bildschirm unterscheiden
4. Multiple Object Tracking (vereinfachter Vorläufer): markierten Spieler kurz merken; kein echtes Bewegungs-Tracking
5. Antizipation: plausible nächste Spielaktion wählen
6. Reaktion: Reaktionszeit in Millisekunden
7. Tactical Decisions: taktische Entscheidungsfragen
8. Dual Task: Farbsignal und Richtung gleichzeitig unterscheiden
9. Passwinkel: freie Anspielstation identifizieren
10. Positionsspiel: schematische Breite/Tiefe verändern
11. Pressing: Pressingauslöser beurteilen
12. Occlusion: textbasierte, verdeckte Spielsituation; keine echten Videos mit zeitgesteuertem Abschneiden
13. Working Memory: Farbfolgen merken
14. Small-Sided-Games: Kleinfeldspielform entwerfen
15. Regeneration: subjektive Erholung und sRPE-Belastung dokumentieren

## Datenspeicherung

Spieler und Testergebnisse werden per `localStorage` ausschließlich **auf dem jeweiligen Gerät und Browser** abgelegt. Keine Cloud-Synchronisation, kein Login, keine Rollenprüfung. Über Verwaltung sind JSON-Sicherungen mit allen Spielerinformationen exportier- und importierbar. Vor Cache-/Browserdaten-Löschung bitte sichern. Für produktiven Vereins-/Schulbetrieb mit Minderjährigen müssen vorab u.a. Rechteverwaltung, Datenschutzhinweise, Einwilligungs-/Rechtsgrundlage, sichere Speicherung, Löschung, zentrale Backups, Backend und weitere Schutzmaßnahmen ergänzt werden.

## Messqualität

Die Übungen sind **didaktische Demonstratoren**, keine klinisch oder sportwissenschaftlich normierten Tests. In einigen Modulen sind die Spielmodelle vereinfacht und Antworten sind nicht in jeder realen Spielsituation eindeutig. Die Durchschnittswerte verschiedener Module sind keine vergleichbare globale Sportleistungsmetrik. Keine Profispieler-Referenzwerte und keine medizinische Diagnostik enthalten.

## Projektstruktur

- `src/App.jsx`: Oberfläche, interaktive Module, Verwaltung, Export/Import
- `src/data.js`: Modulkatalog und Fragen
- `src/style.css`: responsive Oberfläche
- `public/version.json`: Update-Metadaten
- `public/sw.js`: Offline-/Update-Cache
- `.github/workflows/deploy.yml`: Deployment

## Roadmap für den produktiven Einsatz

Authentifizierung mit Trainer-/Administratorrollen; zentraler Datenbankserver und Backups; DSGVO-konforme Zugriffs-, Lösch- und Einwilligungsprozesse; echte animierte Objektverfolgung; Videoclip-Upload und Occlusion; validierte Vergleichstests; Trainingsplan-Sammlungen; QR-Onboarding für Camps; automatisierte Tests; barrierearme Eingabeformen.
