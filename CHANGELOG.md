# Changelog

## v1.2.0

- Card liest jetzt {icon, category}-Objekte aus dem icon_sensor (mit Abwärtskompatibilität zu reinen String-Werten aus v1.1.0)
- Kategorie-Ansicht gruppiert jetzt nach der Integration-gepflegten Kategorie statt nur nach dem eingebauten Fallback

## v1.1.0

- Emoji als Standard, MDI optional, Kategorie-Ansicht

## v1.0.0

- Erste Veröffentlichung

## v1.3.0

- Neu: Langes Klicken/Halten auf einen Artikel öffnet ein Bearbeiten-Formular (Label/Icon/Kategorie), sofern icon_sensor konfiguriert ist - speichert über die neuen Grocery-Icon-Map-Services

## v1.3.1 (nachträglich, HACS-Validierung)

- README: Vorschau-Bild ergänzt (docs/preview.png) - HACS verlangt mindestens ein Bild im Readme für Frontend/Plugin-Repos
- Hinweis: Repository-Topics müssen zusätzlich in den GitHub-Repo-Einstellungen gesetzt werden (kein Datei-Fix möglich)

## v1.3.2

- Fix: Icon-Änderungen über das Bearbeiten-Formular (langes Klicken) kamen teils gar nicht oder erst durch Zufall an - die Karte reagiert jetzt aktiv auf jede Änderung des icon_sensor (egal ob durch die Karte selbst, die Options-Flow-UI, oder sonstwas), statt sich auf ein festes Timeout zu verlassen
- Neu: `default_view: flat|category` - legt die Startansicht der Karte fest, ohne dass man den Umschalter jedes Mal antippen muss

## v1.3.3

- Fix: "CustomElementRegistry ... already been used" Crash, falls die Karte versehentlich doppelt geladen wird (z.B. gleichzeitig als eigenständiges Paket UND über grocery-icon-map installiert) - customElements.define() läuft jetzt nur noch, wenn "grocery-icon-card" nicht schon registriert ist

## v1.4.0

- Besseres Matching: bei mehreren passenden Stichwörtern gewinnt jetzt das spezifischste (längeres/mehrteiliges Label, Bonus wenn es am Ende des Artikeltextes steht - im Deutschen sitzt das Grundwort bei Komposita meist dort), statt einfach das zuerst gefundene. Angelehnt an das Scoring-Prinzip aus rynecoop/ha-grocery-learning.

## v1.4.1

- Bearbeiten-Dialog (langes Klicken): Kategorie-Feld ist jetzt ein Dropdown mit den über die Integration bereits bekannten Kategorien statt freiem Text - plus "➕ Neue Kategorie…"-Option, die bei Bedarf ein Textfeld einblendet

## v1.4.2

- Fix: Ansicht (flach/nach Kategorie) wird jetzt im Browser gemerkt (localStorage, je Karte anhand ihrer Listen) - springt nicht mehr bei jedem Neuladen/Update auf den Standard zurück
- Fix: Label im Bearbeiten-Dialog umbenennen entfernt jetzt zuverlässig die alte Zuordnung, statt sie parallel bestehen zu lassen (die alte konnte durchs Scoring weiterhin gewinnen, wodurch die Änderung wirkungslos aussah)
- Fix: "Entfernen" im Bearbeiten-Dialog löscht jetzt immer das ursprüngliche Label, nicht den ggf. schon editierten Feldinhalt
