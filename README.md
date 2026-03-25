# K12 Apps – Update Checker

Ein leichtgewichtiger, selbst gehosteter Update-Checker für Android-Apps, deployed auf [Netlify](https://www.netlify.com/).

## Live-URL

```
https://k12-updatechecker.netlify.app
```

## Funktionsweise

Die Android-App ruft beim Tippen auf „Update suchen“ folgende URL auf:

```
https://k12-updatechecker.netlify.app?hashi&v=1.0.0&requestUpdate
```

Die Seite liest das Versionsmanifest (`apps/Hashi/versions.json`), vergleicht die Versionen semantisch korrekt und bietet bei Bedarf den APK-Download an.

## Ordnerstruktur

```
index.html                    ← Update-Checker Seite
netlify.toml                  ← Netlify-Konfiguration
README.md
Release_download.txt          ← Anleitung: APK hosten
apps/
  Hashi/
    logo.png                  ← App-Icon (wird im Header angezeigt)
    versions.json             ← Versionsmanifest
    V1-0-0/
      .gitkeep                ← APK wird hier NICHT gespeichert (>25 MB)
```

## APK hosten (GitHub Releases)

Da APKs meist über 25 MB groß sind, werden sie als **GitHub Release Assets** gehostet (bis 2 GB kostenlos).

Siehe `Release_download.txt` für die vollständige Schritt-für-Schritt-Anleitung.

## Neue App hinzufügen

1. Ordner `apps/MeineApp/` anlegen
2. `logo.png` und `versions.json` hinzufügen
3. In `index.html` bei `icons` und `intentUrls` einen Eintrag ergänzen:

```js
const icons      = { hashi: 'hub', meineapp: 'star' };
const intentUrls = {
  hashi:    'intent://...;package=de.koblin12.hashi;end',
  meineapp: 'intent://...;package=de.koblin12.meineapp;end'
};
```

4. App aufrufen: `?meineapp&v=1.0.0&requestUpdate`

## Versionsvergleich

Der Vergleich läuft semantisch korrekt – jede Stelle wird als Zahl ausgewertet:

```
0.9 < 1.0 < 1.1 < 1.10 < 2.0
```

## URL-Parameter

| Parameter | Bedeutung |
|---|---|
| `hashi` (kein Wert) | App-Key |
| `v=1.0.0` | Installierte Version |
| `requestUpdate` | Trigger (optional, wird ignoriert) |
