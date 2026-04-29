# office-ws.de — Redirect-Repository

**Domain:** [office-ws.de](https://office-ws.de/)
**Verhalten:** Leitet auf `https://wolfgang-schmidt.eu/` weiter, mit Matomo-Source-Tracking-Parametern.

## Architektur-Hintergrund
office-ws.de ist die persönliche E-Mail-/Visitenkarten-Domain für `info@office-ws.de`. Die Domain leitet auf wolfgang-schmidt.eu weiter — symmetrisch zur GmbH-Struktur:

- **Privat:** wolfgang-schmidt.eu ← office-ws.de & schmidt-hamburg.de leiten weiter
- **GmbH:** wwsadvisory.com ← wws-advisory.de leitet weiter

## Inhalt
- `index.html` — meta-refresh + JS-Redirect auf `https://wolfgang-schmidt.eu/?mtm_source=office-ws.de&mtm_medium=redirect`
- `404.html` — gleicher Redirect
- `CNAME` — `office-ws.de`

## Matomo-Source-Tracking
Statt einer eigenen Site ID wird der Redirect-Traffic über URL-Parameter an die Zielseite mitgegeben. Im Matomo-Backend erscheinen Besucher von office-ws.de unter Acquisition → Campaigns mit Source `office-ws.de` und Medium `redirect`. Site ID 4 ist für die Zukunft reserviert, falls office-ws.de wieder eine eigenständige Seite mit eigenem Inhalt werden sollte.

## Repo-Historie
- Bis 2026-04-29: Repo hieß `office-ws-redirect`
- 2026-04-29: Versuch einer eigenständigen Landing-Page (verworfen). Repo umbenannt zu `office-ws`.
- 2026-04-29: Zurück auf reinen Redirect (mit Source-Tracking).

## DNS
- Registrar: STRATO
- A-Records: 185.199.108–111.153
- CNAME www: wowas007.github.io

## Wenn der Redirect angepasst werden muss
In `index.html` und `404.html` die Refresh-URL und `window.location.replace`-Aufrufe synchron anpassen.
