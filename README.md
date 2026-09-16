# gyftapp.de

Die Webseite zu **Gyft** — eine Landing-Page plus die drei Rechtstext-Seiten.
Wird von GitHub Pages aus dem Branch `main` ausgeliefert, `CNAME` zeigt auf
`gyftapp.de`.

**Hier gehören keine Zugangsdaten hin.** Das Repo ist öffentlich.

## Dateien

| Datei | Woher |
|---|---|
| `index.html` | von Hand |
| `datenschutz.html`, `nutzungsbedingungen.html`, `impressum.html` | **erzeugt** — nicht von Hand ändern |
| `CNAME`, `favicon.png` | fest |
| `assets/` | Screenshots (noch leer) |

## Rechtstexte ändern

Die drei Rechtstext-Seiten werden aus `lib/legal.ts` der App erzeugt, damit App
und Webseite nicht auseinanderlaufen — Apple und Google verlangen die Texte als
öffentliche URL, die App zeigt dieselben Texte im `LegalScreen`.

Also **immer in der App ändern**, dann im App-Repo:

```
npm run build:legal -- ../gyftapp-de
```

### Noch offen: Anbieterdaten

Name und Anschrift stehen noch als Platzhalter in `lib/legal.ts`
(`[VORNAME NACHNAME]`, `[STRASSE HAUSNUMMER]`, `[PLZ ORT]`). Solange sie fehlen,
markieren die erzeugten Seiten sie gelb und tragen oben den Hinweis „Entwurf".

**Ein Impressum mit Platzhaltern ist schlimmer als keins** — § 5 DDG verlangt
eine ladungsfähige Anschrift. Entweder vor dem Veröffentlichen füllen oder
in Kauf nehmen, dass die Seiten sichtbar als Entwurf online stehen.

## Screenshots nachrüsten

Die alten Screenshots sind **entfernt**: Sie zeigten den Feed, die Storys und
den Tab „Eigene Posts" — alles im September-Pivot abgeschafft — und trugen
oben noch die Wortmarke „Giftly".

Neue Screenshots müssen vom Gerät kommen (Expo Go auf einem echten iPhone; auf
diesem Mac gibt es keinen iOS-Simulator). **Nur Mock-Daten, keine echten
Nutzer.** Sinnvoll sind drei:

1. `assets/swipe.jpg` — Swipe-Screen mit einer Produktkarte
2. `assets/profil.jpg` — Freundesprofil mit Wunschliste und „Bereits reserviert"
3. `assets/events.jpg` — Nachrichten und Events

Danach in `index.html` die vorbereiteten Blöcke einkommentieren (Suche nach
`SCREENSHOT-SLOT`) und beim jeweiligen Feature-Block die Klasse `textonly`
entfernen. CSS und Layout dafür stehen schon drin.

## Lokal ansehen

```
python3 -m http.server 8000
```
