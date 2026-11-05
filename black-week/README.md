# Black Week Wedding Edition · Landingpage

Aktions-LP für 24.–30.11.2026, Ziel-URL `https://prettywoman-termine.velonify.de/black-week/`.

**Aufbau und Code** sind von der Termin-LP (`/index.html`) übernommen: gleiche Section-Layouts, gleiches Tracking, gleicher BridalLive-Kalender.
**Farben und Schriften** folgen dem Pretty-Woman-Brandguide: Playfair Display + Inter (selbst gehostet in `fonts/`), Creme `#f7f2ea` / Weiß im Wechsel, Gold `#ab8148`, Text `#141414` / `#311c12`, keine dunklen Flächen.

- `index.html`: die LP, eine Datei, CSS und JS inline
- `fonts/`: Playfair Display und Inter (OFL)
- `img/`: neue Kollektion aus Drive „Brautkleid Bilder“ (WebP)
- `PROMPT_Black-Week-LP.md`: ursprüngliches Briefing
- `_archiv/variante-a-brandguide.html`: verworfene Variante mit eigenem Layout. Der Ordner beginnt mit `_`, GitHub Pages (Jekyll) veröffentlicht ihn nicht.

## Aufbau

Hero → Termin (Tagesübersicht, BridalLive, „Wann heiratet Ihr?“) → Angebote (3 Preisspalten) → neue Kollektion (5 Linien, Desktop: Karten klappen beim Hovern in voller Bildbreite auf, mobil: Wisch-Slider) → Ablauf → Bewertungen → Curvy → FAQ → Abschluss.

## Inhalt (vom Kunden bestätigt)

- 200 € Rabatt auf **alle** Modelle der neuen Kollektion, nur bei Bestellung vom 24. bis 30.11.
- Ausgewählte Brautkleider 799 € zum Mitnehmen
- Ausgewählte Hochzeitsanzüge 150 € (2-tlg.) / 250 € (4-tlg.)
- Termine: Di 24., Mi 25., Fr 27., Mo 30.11. je 9/11/15/17 Uhr · Sa 28.11. 9/11/13/15 Uhr · Do 26.11. noch offen · So zu

## Schalter im Script

- `CONFIRM_26 = false` → auf `true`, sobald die Termine am Do. 26.11. bestätigt sind. Tage und Terminanzahl rechnen sich selbst.
- `START` / `END`: Countdown („Startet in …“, „Läuft noch …“). Nach `END` erscheint oben ein Hinweis mit Link zur Termin-LP `/`.
- Test: `?now=2026-11-27T12:00:00%2B01:00` simuliert ein Datum.

## Buchungs-iframe

Die Höhe folgt der BridalLive-Nachricht `bridallive.height_change` (Inhaltshöhe + 32 px, mind. 300 px). Sobald das Formular den Fokus bekommt, mind. 620 px, weil die Terminart-Liste als Overlay ohne Höhenmeldung aufklappt. Kommt nach 8 s keine Höhe, fällt der Rahmen auf 1040 px zurück. `bridallive.scroll-to-top` holt den Formularanfang wieder ins Bild.

## Tracking

Wie Termin-LP (Consent Mode v2, GTM `GTM-PLBF7LSN` nach Zustimmung, Meta-Pixel nach Zustimmung, CAPI-Relay und Clarity cookielos ohne Zustimmung, gleicher `pw_consent`-Schlüssel). Zusätzlich:
- `lp_variant: 'black_week'` im dataLayer, an allen Events, als Meta-`custom_data` und als Clarity-Tag
- BridalLive-iframe mit `pw_src=bw`
- neue Events: `lp_day_click` (day), `lp_booking`
- `data-cta` wie Termin-LP: `hero`, `reviews`, `curvy`, `close`, `dock`, `fallback`

## Offen vor Livegang

1. Mo. 30.11. in BridalLive für Online-Buchung freischalten (Stand 05.11. gesperrt; Termintyp-Text sagt „Montag nur via Mail“) und im Kalender prüfen
2. 26.11. bestätigen → `CONFIRM_26`
3. GTM: Data-Layer-Variable `lp_variant` + Trigger für `lp_day_click` / `lp_booking` anlegen
4. Keine Streichpreise/Prozente ohne niedrigsten 30-Tage-Preis (§ 11 PAngV)
5. Anzahl Google-Bewertungen (266) kurz vor Livegang aktualisieren
6. Live testen: CAPI-Relay (nimmt nur `https://prettywoman-termine.velonify.de` an), Pixel, Buchung
