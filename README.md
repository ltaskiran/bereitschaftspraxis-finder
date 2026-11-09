# Nächste Bereitschaftspraxis finden – Landkreis Neunkirchen

Eine statische Web-App (eine HTML-Datei, keine Installation nötig). Leser geben ihre Adresse ein und sehen die nächsten Bereitschaftspraxen mit Luftlinie, Fußzeit (Schätzung), Autozeit und ÖPNV-Dauer. Die App funktioniert auf Desktop und Handy und passt sich dem hellen oder dunklen Design des Geräts an.

## Live-Adresse
https://itaskiran.github.io/bereitschaftspraxis-finder/

## In einen Artikel einbetten

Im Artikel (HTML-Modus des Redaktionssystems) diesen Code einfügen:

```html
<iframe
  src="https://itaskiran.github.io/bereitschaftspraxis-finder/"
  title="Nächste Bereitschaftspraxis finden – Landkreis Neunkirchen"
  width="100%"
  height="1000"
  style="border:0;max-width:100%;"
  loading="lazy"
  allow="geolocation">
</iframe>
```

Die App meldet ihre Höhe automatisch an die einbettende Seite. Damit das funktioniert, braucht es zusätzlich folgendes Skript direkt unter dem iframe (optional, aber empfohlen):

```html
<script>
  window.addEventListener('message', function (e) {
    if (e.data && e.data.type === 'bereitschaftspraxis-finder:height') {
      var f = document.querySelector('iframe[src*="bereitschaftspraxis-finder"]');
      if (f) f.style.height = (e.data.height + 16) + 'px';
    }
  });
</script>
```

Falls das Redaktionssystem keine Skripte erlaubt, bleibt die feste Höhe von 1000 Pixel. Auf kleinen Bildschirmen scrollt der Leser dann innerhalb des Rahmens.

## Auf GitHub Pages veröffentlichen
1. Repository anlegen und `index.html` sowie `README.md` hochladen. Die Datei muss exakt `index.html` heißen.
2. Im Repository: **Settings → Pages → Source: Deploy from a branch → main / (root)**.
3. Die App ist danach unter `https://<nutzername>.github.io/<repo>/` erreichbar.

## Standorte pflegen
In `index.html` im Abschnitt `CONFIG.praxen` eintragen. Einträge mit `aktiv: false` werden nicht angezeigt. Nach jeder Änderung die Angaben gegen kvsaarland.de prüfen.

## Hinweis zur Schließung
Der Hinweistext zur Schließung in Neunkirchen-Kohlhof steht oben auf der Seite. Er muss aktualisiert werden, sobald die KV Saarland die endgültige Entscheidung bekannt gibt. Der Standort selbst lässt sich über `aktiv: true` wieder einblenden.

## Datenquellen und Grenzen
- **Adresssuche:** OpenStreetMap Nominatim, Ausweichdienst Photon (komoot). Richtlinie: max. 1 Anfrage pro Sekunde. Bei vielen Zugriffen einen eigenen Dienst verwenden.
- **Auto:** OSRM-Demoserver (`router.project-osrm.org`). Für den Dauerbetrieb mit vielen Nutzern eigenen Server oder kommerziellen Dienst einplanen (z. B. OpenRouteService, HERE).
- **Zu Fuß:** Schätzung aus Luftlinie × 1,25 bei 4,5 km/h.
- **ÖPNV:** transport.rest (v6, DB-basiert). Die Abdeckung regionaler Busse im Saarland ist nicht garantiert.
- **Karte:** Leaflet mit OpenStreetMap-Kacheln.
- **Hinweis:** Die Dienste funktionieren nur, wenn die Seite über eine echte Webadresse aufgerufen wird (z. B. GitHub Pages), nicht in einer Vorschau mit strikter Sicherheitsrichtlinie.

## Lizenz
Vorschlag: MIT (eigene `LICENSE`-Datei mit Namen ergänzen).
