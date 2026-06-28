# flowzz-data — Ablage für die öffentliche Flowzz-App

Diese Repo versorgt die öffentliche Version der App mit Daten und Updates.
Drei Dateien liegen im Wurzelverzeichnis (Branch `main`):

## 1. strains.json  (die Sorten-Daten)
Wird von deinem Scraper (Pi / lokal) erzeugt und hierher hochgeladen.
Format: `{ "scraped_at": "...", "count": 1234, "products": [ ... ] }`
Die App lädt sie beim Start von:
`https://raw.githubusercontent.com/Vagnis/flowzz-data/main/strains.json`

## 2. version.json  (Update-Hinweis)
Steuert den Update-Check im Splash. Felder:
- `version`       — neueste Version, z. B. "1.0.1" (muss höher sein als die installierte)
- `installer_url` — direkter Download-Link zum Installer (.exe)
- `notes`         — kurze Änderungsnotiz (optional)

Solange `version` ≤ der installierten App-Version ist, erscheint kein Hinweis.
Erhöhe `version` erst, wenn der neue Installer wirklich erreichbar ist.

## 3. Installer (.exe)
Am besten als GitHub **Release** anhängen (Tab „Releases" → „Draft a new release").
Dann zeigt `installer_url` auf den Release-Download, z. B.:
`https://github.com/Vagnis/flowzz-data/releases/latest/download/FlowzzAppSetup.exe`

## Ablauf eines Updates
1. Neue App bauen, Installer erzeugen, als Release hochladen.
2. In `version.json` die `version` erhöhen und `installer_url` setzen.
3. Beim nächsten Start sehen alle Nutzer im Splash den Update-Hinweis.

## Wichtig
- Nur öffentliche Sorten-Daten hier ablegen — niemals Login-Daten.
- Die Repo bleibt public, damit die App ohne Token darauf zugreifen kann.
