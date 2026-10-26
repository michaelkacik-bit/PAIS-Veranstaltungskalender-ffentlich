# PAIS Veranstaltungsradar – kostenlose Einrichtung

## Enthalten
- `index.html`: responsive Web-App mit Filtern, Merkliste und ICS-Export
- `scripts/update_events.py`: sucht öffentliche Google-News-RSS-Ergebnisse
- `.github/workflows/update-events.yml`: täglicher Lauf um 06:17 UTC sowie manueller Start
- `data/events.json`: Ergebnisdatei, wird beim ersten Lauf befüllt

## Einmalige Einrichtung (PC oder Browser im Desktop-Modus)
1. Erstelle/öffne ein GitHub-Konto: https://github.com/
2. Erstelle ein **öffentliches** Repository namens `pais-veranstaltungsradar` (GitHub Free benötigt für Pages ein öffentliches Repository).
3. Lade alle Dateien und Ordner aus diesem ZIP in das Repository hoch. Wichtig: `.github` ist ein versteckter Ordner; falls er beim Dateiupload nicht sichtbar ist, erstelle `.github/workflows/update-events.yml` im GitHub-Webeditor.
4. Öffne **Actions** im Repository und aktiviere Workflows, falls GitHub dies anbietet.
5. Wähle **Update PAIS event data** → **Run workflow**. Warte, bis der Lauf grün abgeschlossen ist. Dadurch wird `data/events.json` mit Suchergebnissen befüllt.
6. Öffne **Settings → Pages**. Unter **Build and deployment** wähle **Deploy from a branch**, Branch `main`, Ordner `/(root)`, dann **Save**.
7. Warte, bis Pages veröffentlicht ist. Unter **Settings → Pages** wird die Webadresse angezeigt, typischerweise `https://DEIN-BENUTZER.github.io/pais-veranstaltungsradar/`.
8. Öffne die Webadresse auf dem Android-Handy. Optional im Chrome-Menü **Zum Startbildschirm hinzufügen**.

## Täglicher Betrieb
- Der Workflow läuft täglich um 06:17 UTC (in Deutschland normalerweise 07:17 Winterzeit / 08:17 Sommerzeit).
- In der App bedeutet „Daten neu laden“: zuletzt gespeicherte JSON-Daten erneut laden. Die Websuche selbst läuft serverseitig im GitHub-Workflow.
- Für einen sofortigen Suchlauf: GitHub → Repository → Actions → Update PAIS event data → Run workflow.
- Bei den Treffern ist das Veröffentlichungsdatum nicht automatisch der Veranstaltungstag. Vor dem ICS-Export das tatsächliche Veranstaltungsdatum auf der Originalseite kontrollieren.
- ICS-Datei wird pro Veranstaltung heruntergeladen und anschließend in den Kalender importiert.

## Grenzen und Datenschutz
- Google News RSS ist eine öffentliche Suchquelle, keine vollständige Veranstaltungsdatenbank. Manuelle Kontrolle der verlinkten Originalquellen bleibt wichtig.
- Die Einstufung von Thema und Typ erfolgt anhand von Suchbegriffen und kann falsch liegen.
- Ein öffentliches GitHub-Repository macht den Quellcode öffentlich. Keine Zugangsdaten oder persönlichen Informationen in dieses Repository laden.
- GitHub Pages ist für statische Dateien gedacht. Die Lösung braucht für den beschriebenen Umfang keine Datenbank und keinen API-Schlüssel.
