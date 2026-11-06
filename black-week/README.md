# Black Week Wedding Edition · Landingpage

Aktions-LP für 24.–30.11.2026, Ziel-URL `https://prettywoman-termine.velonify.de/black-week/`.

**Aufbau und Code** sind von der Termin-LP (`/index.html`) übernommen: gleiche Section-Layouts, gleiches Tracking, gleicher BridalLive-Kalender.
**Farben und Schriften** folgen dem Pretty-Woman-Brandguide: Playfair Display + Inter (selbst gehostet in `fonts/`), Creme `#f7f2ea` / Weiß im Wechsel, Gold `#ab8148`, Text `#141414` / `#311c12`, keine dunklen Flächen.

- `index.html`: die LP, eine Datei, CSS und JS inline
- `fonts/`: Playfair Display und Inter (OFL)
- `img/`: neue Kollektion aus Drive „Brautkleid Bilder“ (WebP). Galerie in `img/galerie/01–16.webp` (764–900 px breit, nur vom Kunden freigegebene Bilder: Curvy-Ordner 36xxx, IMG_9576, Lasabina Kiara-21/Sindy-3, Novabella 31110, Prinzessin); die alten 510-px-Herstellerbilder nutzt nur noch das Archiv
- `PROMPT_Black-Week-LP.md`: ursprüngliches Briefing
- `_archiv/variante-a-brandguide.html`: verworfene Variante mit eigenem Layout. Der Ordner beginnt mit `_`, GitHub Pages (Jekyll) veröffentlicht ihn nicht.

## Aufbau

Hero → Termin (Tagesübersicht, BridalLive, „Wann heiratet Ihr?“) → Angebote (3 Preisspalten) → Galerie der neuen Kollektion (16 Bilder, Lightbox mit Pfeiltasten/Wischen, mobil erst 6 + „Alle 16 Bilder ansehen“) → Ablauf → Bewertungen → Curvy → FAQ → Abschluss.

## Inhalt (vom Kunden bestätigt)

- 200 € Rabatt auf **alle** Modelle der neuen Kollektion, nur bei Bestellung vom 24. bis 30.11.
- Ausgewählte Brautkleider 799 € zum Mitnehmen
- Komplette Hochzeitsanzüge für maximal 250 € (zweiteilig max. 150 €). Nie „ab“-Preise schreiben. Der Partner braucht einen **eigenen Termin** (Termintyp „Anprobe Anzug Bräutigam“), keine gemeinsamen Termine
- Termine: Di 24., Mi 25., Do 26., Fr 27., Mo 30.11. je 9/11/15/17 Uhr · Sa 28.11. 9/11/13/15 Uhr · So zu (24 Termine)

## Schalter im Script

- `CONFIRM_26 = true` (26.11. am 06.11. bestätigt). Tage und Terminanzahl rechnen sich selbst.
- `START` / `END`: Countdown („Startet in …“, „Läuft noch …“). Nach `END` erscheint oben ein Hinweis mit Link zur Termin-LP `/`.
- Test: `?now=2026-11-27T12:00:00%2B01:00` simuliert ein Datum.

## Buchungs-iframe

Die Höhe folgt der BridalLive-Nachricht `bridallive.height_change` (Inhaltshöhe + 32 px, mind. 300 px). Sobald das Formular den Fokus bekommt, mind. 620 px, weil die Terminart-Liste als Overlay ohne Höhenmeldung aufklappt. Kommt nach 8 s keine Höhe, fällt der Rahmen auf 1040 px zurück. `bridallive.scroll-to-top` holt den Formularanfang wieder ins Bild.

## Tracking

Wie Termin-LP (Consent Mode v2, GTM `GTM-PLBF7LSN` nach Zustimmung, Meta-Pixel nach Zustimmung, CAPI-Relay und Clarity cookielos ohne Zustimmung, gleicher `pw_consent`-Schlüssel). Zusätzlich:
- `lp_variant: 'black_week'` im dataLayer, an allen Events, als Meta-`custom_data` und als Clarity-Tag
- BridalLive-iframe mit `pw_src=bw`
- neue Events: `lp_day_click` (day), `lp_booking`, `lp_gallery_open` (image)
- `data-cta` wie Termin-LP: `hero`, `reviews`, `curvy`, `close`, `dock`, `fallback`

## Offen vor Livegang

1. Mo. 30.11. in BridalLive für Online-Buchung freischalten (Stand 05.11. gesperrt; Termintyp-Text sagt „Montag nur via Mail“) und im Kalender prüfen
2. GTM: Data-Layer-Variable `lp_variant` + Trigger für `lp_day_click` / `lp_booking` anlegen
3. Keine Streichpreise/Prozente ohne niedrigsten 30-Tage-Preis (§ 11 PAngV)
4. Anzahl Google-Bewertungen (266) kurz vor Livegang aktualisieren
5. Live testen: CAPI-Relay (nimmt nur `https://prettywoman-termine.velonify.de` an), Pixel, Buchung

## Galerie: noch einzubauen

Vom Kunden freigegeben, aber über die Drive-Anbindung nicht ladbar (über 10 MB): `6028`, `6070`, `6087`, `6089`, `6090`, `6091` (je mit `_v1`, `_back`, `_back1`) und `IMG_6412–6414`. Lokal herunterladen, auf 900 px Breite als WebP exportieren und in `img/galerie/` ergänzen.
Nicht verwendet: `IMG_9590–9592` (Handy-Screenshots mit eingeblendeten Pfeilen), `IMG_9583/9584` (nur 600 px breit).
