# Grocery Icon Card

Custom Lovelace Card für Home Assistant. Zeigt eine oder mehrere `todo`-Entitäten
(z. B. Bring! und Mealie) als umschaltbares Icon-Raster an, mit automatischer
Symbol-Zuordnung anhand des Artikelnamens. Voll bedienbar: Artikel abhaken und
neue hinzufügen. Rein clientseitig, keine externen Dienste.

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

Die Zuordnung Stichwort → Icon liegt in `grocery-icon-card.js` in der Konstante
`ICON_RULES`. Neue Zeile im Format ergänzen:

```js
{ keys: ["stichwort"], icon: "mdi:icon-name" },
```

## Lizenz

MIT
