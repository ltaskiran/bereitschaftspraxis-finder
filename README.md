# Nächste Bereitschaftspraxis finden – Landkreis Neunkirchen

Eine statische Web-App (eine HTML-Datei, keine Installation nötig). Leser geben ihre Adresse ein und sehen die nächsten Bereitschaftspraxen mit Luftlinie, Fußzeit (Schätzung), Autozeit und ÖPNV-Dauer.

## Auf GitHub Pages veröffentlichen
1. Repository anlegen und `index.html` sowie `README.md` hochladen.
2. Im Repository: **Settings → Pages → Source: Deploy from a branch → main / (root)**.
3. Die App ist danach unter `https://<nutzername>.github.io/<repo>/` erreichbar.

## Standorte pflegen
In `index.html` im Abschnitt `CONFIG.praxen` eintragen. Einträge ohne `adresse` werden nicht angezeigt. Nach jeder Änderung die Angaben gegen kvsaarland.de prüfen.

## Hinweis zum Hinweistext
Der Hinweis zur Schließung in Neunkirchen-Kohlhof steht im HTML oben auf der Seite. Er muss aktualisiert werden, sobald die KV Saarland die endgültige Entscheidung bekannt gibt.

## Datenquellen und Grenzen
- **Adresssuche:** OpenStreetMap Nominatim. Richtlinie: max. 1 Anfrage pro Sekunde. Bei vielen Zugriffen einen eigenen Dienst verwenden.
- **Auto:** OSRM-Demoserver (`router.project-osrm.org`). Für den Dauerbetrieb mit vielen Nutzern eigenen Server oder kommerziellen Dienst einplanen (z. B. OpenRouteService, HERE).
- **Zu Fuß:** Schätzung aus Luftlinie × 1,25 bei 4,5 km/h.
- **ÖPNV:** transport.rest (v6, DB-basiert). Die Abdeckung regionaler Busse im Saarland ist nicht garantiert.
- **Karte:** Leaflet mit OpenStreetMap-Kacheln.

## Lizenz
Vorschlag: MIT (eigene `LICENSE`-Datei mit Namen ergänzen).
