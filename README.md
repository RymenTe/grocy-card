# Grocery Icon Card

Custom Lovelace Card für Home Assistant. Zeigt eine oder mehrere `todo`-Entitäten
(z. B. Bring! und Mealie) als umschaltbares Icon-Raster an, mit automatischer
Symbol-Zuordnung anhand des Artikelnamens. Voll bedienbar: Artikel abhaken und
neue hinzufügen. Rein clientseitig, keine externen Dienste.

> Suchst du zusätzlich eine GUI zum Pflegen der Icon-Zuordnungen (statt
> Code-Änderungen)? Dann ist [grocery-icon-map](https://github.com/RymenTe/grocery-icon-map)
> die bessere Wahl – ein einziges Paket, das diese Karte automatisch mitbringt.
> Dieses Repo hier bleibt die schlanke Variante ganz ohne Python-Backend.

## Installation (via HACS)

1. HACS → Frontend → oben rechts die drei Punkte → **Custom repositories**
2. Repository-URL eintragen, Kategorie **Dashboard**
3. "Grocery Icon Card" suchen und installieren
4. HA neu laden (HACS trägt die Ressource automatisch ein)

## Konfiguration

```yaml
type: custom:grocery-icon-card
title: Einkaufsliste
lists:
  - entity: todo.einkaufsliste
    name: Bring
  - entity: todo.mealie_einkaufsliste
    name: Mealie
```

## Icons erweitern

Zwei Wege, kombinierbar:

1. **Ohne weitere Installation:** Zuordnung Stichwort → Icon liegt in
   `grocery-icon-card.js` in der Konstante `ICON_RULES`. Neue Zeile im
   Format ergänzen:
   ```js
   { keys: ["stichwort"], icon: "mdi:icon-name" },
   ```
2. **Mit GUI-Pflege, ohne Codeänderung:** die Begleit-Integration
   [Grocery Icon Map](https://github.com/RymenTe/grocery-icon-map)
   installieren – die bringt diese Karte gleich automatisch mit (ein Install
   für beides) – und in der Karten-Config referenzieren:
   ```yaml
   type: custom:grocery-icon-card
   icon_sensor: sensor.grocery_icon_map_zuordnungen
   lists:
     - entity: todo.einkaufsliste
       name: Bring
   ```
   Zuordnungen aus der Integration haben Vorrang vor `ICON_RULES`. Ohne
   `icon_sensor` funktioniert die Karte unverändert eigenständig.

## Versionierung

Diese Karte folgt [Semantic Versioning](https://semver.org/). Releases über
GitHub-Tags, HACS zeigt verfügbare Updates automatisch an.

## Lizenz

MIT, siehe [LICENSE](LICENSE)
