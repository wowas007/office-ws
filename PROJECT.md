# office-ws.de — Redirect-Repository

**Domain:** [office-ws.de](https://office-ws.de/)
**Verhalten:** Leitet auf `https://wwsadvisory.com/?lang=de` weiter, mit Matomo-Source-Tracking-Parametern.

## Architektur-Hintergrund
office-ws.de gehört zur **GmbH-Sphäre** und ist eine zweite Domain der WWS Advisory GmbH (zusammen mit der primären `wws-advisory.de`). Beide Domains leiten auf wwsadvisory.com weiter:

- **GmbH-Sphäre:** wwsadvisory.com ← wws-advisory.de & office-ws.de leiten weiter
- **Privat-Sphäre:** wolfgang-schmidt.eu ← schmidt-hamburg.de leitet weiter

E-Mail unter `info@office-ws.de` läuft separat über iCloud+ Custom Domain und ist von dieser Web-Weiterleitung nicht betroffen.

## Inhalt
- `index.html` — meta-refresh + JS-Redirect auf `https://wwsadvisory.com/?lang=de&mtm_source=office-ws.de&mtm_medium=redirect`
- `404.html` — gleicher Redirect
- `CNAME` — `office-ws.de`

## Matomo-Source-Tracking
Statt einer eigenen Site ID wird der Redirect-Traffic über URL-Parameter an die Zielseite mitgegeben. Im Matomo-Backend erscheinen Besucher von office-ws.de unter Acquisition → Campaigns mit Source `office-ws.de` und Medium `redirect` — dort gegen Site ID 3 (wwsadvisory.com).

## Repo-Historie
- Bis 2026-04-29: Repo hieß `office-ws-redirect`, leitete auf wolfgang-schmidt.eu
- 2026-04-29 vormittags: Versuch einer eigenständigen Landing-Page (verworfen). Repo umbenannt zu `office-ws`.
- 2026-04-29 nachmittags: Zurück auf reinen Redirect, zunächst auf wolfgang-schmidt.eu.
- 2026-04-29 abends: Korrigiert auf wwsadvisory.com (office-ws.de gehört zur GmbH-Sphäre, nicht zur Privatsphäre).

## DNS
- Registrar: STRATO
- A-Records: 185.199.108–111.153
- CNAME www: wowas007.github.io

## Wenn der Redirect angepasst werden muss
In `index.html` und `404.html` die Refresh-URL und `window.location.replace`-Aufrufe synchron anpassen.
