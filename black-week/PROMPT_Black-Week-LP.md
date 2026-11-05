# Prompt: Landingpage „Black Week Wedding Edition“ · Pretty Woman Wedding Styles

> Diesen Prompt komplett in einer neuen Claude-Code-Session im Repo `LP-prettywoman` ausführen.
> Stand: 05.11.2026

---

## 1. Auftrag

Baue eine Aktions-Landingpage für die **Black Week Wedding Edition** von Pretty Woman Wedding Styles (Brautmoden in Mühlacker), gültig vom **24.11. bis 30.11.2026**.

- **Referenz für Aufbau, Conversion-Logik, Tracking und Code:** die bestehende Termin-LP von Julian in diesem Repo (`/index.html`, live unter https://prettywoman-termine.velonify.de). Lies sie vollständig, bevor Du anfängst.
- **Gestaltung:** Julians LP nutzt eigene Farben und Schriften (Bodoni Moda, Jost, Gold `#cf9529`). Die neue Seite folgt stattdessen dem **Pretty-Woman-Brandguide** (Abschnitt 4). Übernimm also die Struktur, aber nicht den Look.
- **Inhalt:** Forme die LP zu einer Black-Week-Seite um (Abschnitte 3 und 5). Was nicht zur Aktion passt, fliegt raus.
- **Zieldatei:** `black-week/index.html` (eine Datei, CSS und JS inline wie bei Julian). Die bestehende `/index.html`, `CNAME` und `worker/` **nicht verändern**. Die Seite läuft später unter `https://prettywoman-termine.velonify.de/black-week/`.
- Seite auf `noindex`.

---

## 2. Die Aktion (Fakten, verbindlich)

**Name:** Black Week Wedding Edition
**Zeitraum:** Di. 24.11. bis Mo. 30.11.2026

**Die drei Angebote:**

1. **Neue Kollektion: 200 € Rabatt** (der wichtigste USP, steht ganz oben)
   Die neueste Kollektion ist frisch eingetroffen. Wer in der Black Week bestellt, bekommt darauf bereits 200 € Rabatt.
2. **Ausgewählte Brautkleider für 799 €, direkt zum Mitnehmen**
   Ideal für Paare, die bald heiraten: Kleid aussuchen und gleich mitnehmen, keine Lieferzeit.
3. **Ausgewählte Hochzeitsanzüge reduziert:** zweiteilig 150 €, vierteilig 250 €

**Botschaft (vom Kunden, sinngemäß umsetzen, nicht wörtlich als Fließtext abschreiben):**
- Letzte Chance des Jahres auf große Rabatte
- Perfekt für alle Bräute, die **nächstes Jahr (2027)** heiraten: jetzt die neue Kollektion mit 200 € Rabatt bestellen, die Lieferzeit von 6–9 Monaten passt genau
- Perfekt für Paare, die **zeitnah** heiraten: 799-€-Kleider und reduzierte Anzüge direkt zum Mitnehmen

**Black-Week-Termine** (Startzeiten der Beratungstermine; Namen der Beraterinnen gehören nicht auf die Seite):

| Tag | Termine |
|---|---|
| Di. 24.11. | 9, 11, 15, 17 Uhr |
| Mi. 25.11. | 9, 11, 15, 17 Uhr |
| Do. 26.11. | *noch offen:* 9, 11, 15, 17 Uhr |
| Fr. 27.11. | 9, 11, 15, 17 Uhr |
| Sa. 28.11. | 9, 11, 13, 15 Uhr |
| So. 29.11. | geschlossen |
| Mo. 30.11. | 9, 11, 15, 17 Uhr |

- Den **26.11. noch nicht anzeigen**. Baue ihn so ein, dass er per einer Zeile (z. B. `data-confirmed="false"` oder ein Flag im JS) freigeschaltet werden kann.
- Darstellung als ruhige Tagesübersicht (Tag + Uhrzeiten als kleine Chips), **nicht** als Tabelle mit Rahmen. Die Buchung selbst läuft weiterhin über den BridalLive-Kalender, die Übersicht ist nur Orientierung („So viele Termine gibt es in der Black Week“). Ein Klick auf einen Tag scrollt zum Kalender.
- Die Termine sind begrenzt (20 Slots, mit dem 26.11. 24). Das darf ehrlich gesagt werden („Nur 20 Termine in der Black Week“, mit dem 26.11. sind es 24). Keine erfundenen Zähler, keine Fake-Countdowns.

**Ein Countdown ist erlaubt**, aber nur ein echter: bis zum Start (24.11., 9 Uhr) „Startet in …“, während der Aktion „Endet in …“ (bis 30.11., 19 Uhr), danach blendet sich die Aktion aus und es erscheint ein Hinweis „Die Black Week ist vorbei“ mit Link zur normalen Termin-LP (`/`). Dezent, im Header oder unter der Hero-Zeile, keine rote Alarmoptik.

---

## 3. Seitenstruktur

Kein Menü. Alle CTAs springen auf `#termin`. Hintergründe wechseln **Creme / Weiß**.

0. **Header** wie bei Julian: Logo links (ohne Link), Telefon rechts. Darunter optional schmale Countdown-Zeile.

1. **Hero (Creme)**
   - H1 mit dem Aktionsnamen, z. B. „Black Week Wedding Edition“ und als zweite Zeile kursiv der Zeitraum oder der Hauptvorteil („200 € auf die neue Kollektion“)
   - Ein Satz Subline mit den drei Angeboten in Kurzform
   - Primär-Button „Black-Week-Termin sichern“ → `#termin`, darunter klein „24.–30. November · Beratung kostenlos“
   - Bewertungszeile 4,9 ★ / 266 Google-Bewertungen bleibt (Zahl vorher prüfen)
   - Bild rechts: ein Foto aus der **neuen Kollektion** (siehe Abschnitt 6)
   - Der Button muss bei 375 × 667 ohne Scrollen sichtbar sein

2. **Die drei Angebote (Weiß)**
   Drei Karten nebeneinander (mobil untereinander), Reihenfolge wie in Abschnitt 2. Pro Karte: Linien-Icon in Gold (kein Emoji), Preis bzw. Rabatt groß in Playfair, ein Satz „für wen“. Die Karte „Neue Kollektion“ ist leicht hervorgehoben (z. B. feiner Goldrahmen), nicht größer und nicht dunkel.

3. **Termin (Creme)** · `id="termin"`
   - H2, z. B. „Sichere Dir Deinen Black-Week-Termin“
   - Die Black-Week-Termin-Übersicht (Abschnitt 2)
   - Darunter der **BridalLive-Kalender** exakt wie bei Julian (gleiches iframe, gleicher Fallback-Link, gleiches Lazy-Loading, Hinweis zum Termintyp). Hänge an die iframe-URL `pw_src=bw` statt `pw_src=lp`.
   - Julians „Wann heiratest Du?“-Planer bleibt, bekommt aber eine Black-Week-Ausgabe: Hochzeit in mehr als 9 Monaten → Empfehlung „Neue Kollektion mit 200 € Rabatt“; Hochzeit in weniger als 6 Monaten → „799-€-Kleider zum Mitnehmen“; dazwischen beides nennen. Event `lp_wedding_month` beibehalten.

4. **Neue Kollektion (Weiß)**
   Galerie bzw. Swiper mit 6–10 Bildern der neuen Kollektion, gruppiert nach Schnitt (A-Linie, Fit & Flare/H-Linie, Prinzessin, Curvy). Text: frisch eingetroffen, in der Black Week schon 200 € günstiger, 6–9 Monate Lieferzeit, passt für Hochzeiten 2027.

5. **Für wen ist die Black Week? (Creme)**
   Zwei Spalten: „Du heiratest 2027“ (→ neue Kollektion −200 €) und „Ihr heiratet bald“ (→ 799-€-Kleider + Anzüge zum Mitnehmen). Je ein CTA.

6. **Hochzeitsanzüge (Weiß)**
   Kurzer Block: ausgewählte Hochzeitsanzüge, zweiteilig 150 €, vierteilig 250 €, direkt zum Mitnehmen. Hinweis, dass der Partner gleich mitkommen kann. Bild aus dem Drive-Ordner „Anzug Bilder“ (siehe Abschnitt 6).

7. **So läuft Dein Termin ab (Creme)**
   Julians 5 Schritte, auf 4 gekürzt (Termin wählen → Wir melden uns → Separee & Anprobe → Die Glocke). Den Satz mit „Martina, Caro und das Team“ ersetzen durch „Martina und ihr Team“.

8. **Bewertungen (Weiß)**
   Julians Google-Rezensionen wörtlich übernehmen (Rezensionen bleiben in Originalschreibweise, auch „Artemis“). Etwa 4 statt 7 auswählen.

9. **Curvy (Creme)**
   Stark gekürzt: Gr. 30 bis 66 zum Anprobieren, eine Rezension, kein eigener CTA nötig.

10. **FAQ (Weiß)**, native `<details>` wie bei Julian, neu geschrieben für die Aktion:
    - Gilt der Rabatt von 200 € auf alle Kleider der neuen Kollektion? *(Antwort mit Platzhalter, siehe Abschnitt 8)*
    - Muss ich in der Black Week auch bestellen, um den Rabatt zu bekommen?
    - Welche Kleider gibt es für 799 €? (ausgewählte Einzelstücke, direkt zum Mitnehmen, Größenauswahl begrenzt)
    - Brauche ich einen Termin? (ja, Beratung im Separee nur mit Termin; Telefonnummer nennen)
    - Kann mein Partner einen Anzug anprobieren?
    - Wo kann ich parken? → wörtlich: „Wir haben unsere firmeneigenen kostenlosen Parkplätze direkt vor unserem Haus.“ plus Adresse

11. **Abschluss-CTA (Creme)** + Footer wie bei Julian (Adresse, Telefon, Impressum, Datenschutz, Cookie-Einstellungen).

12. **Mobil:** fester Button unten „Black-Week-Termin sichern“ (wie Julians Dock), blendet sich aus, solange der Kalender im Bild ist.

---

## 4. Brandguide Pretty Woman (verbindlich, ersetzt Julians Design-Tokens)

### Farben (exakt diese Variablen auf `:root`)
```css
--cream:     #f7f2ea;   /* Section-Hintergrund A */
--white:     #ffffff;   /* Section-Hintergrund B */
--ink:       #141414;   /* Text */
--ink-alt:   #311c12;   /* warmer Text-Akzent, Überschriften */
--muted:     #5c5344;   /* Sekundärtext */
--gold:      #ab8148;   /* Akzent, Buttons, Sterne, Linien */
--gold-soft: #cfaf7c;   /* zarte Akzente, Hover */
--gold-deep: #7c5a2c;   /* Button-Hover, kleiner Gold-Text */
--line:      rgba(20,20,20,.13);
--line-gold: rgba(171,129,72,.45);
```
- **Keine dunklen Flächen.** Auch nicht für „Black Week“. Kein schwarzer Hero, kein schwarzes Banner, kein Dark Mode. Das „Black“ entsteht nur über Typografie: das Wort „Black“ in `--ink`, groß in Playfair, gern mit Gold-Haarlinie. Das ist der zentrale Unterschied zu üblichen Black-Friday-Seiten und gewollt.
- Hintergründe ausschließlich Creme und Weiß im Wechsel, Gold nur als Akzent.
- Weiß auf `#ab8148` hat nur 3,5:1 → Gold-Buttons mit Text ab 19 px fett (zählt als großer Text). Kleiner Gold-Text nur in `--gold-deep`.

### Schrift
- Überschriften: **Playfair Display** (500/600/700, Kursiv 500/600 für einzelne betonte Wörter)
- Fließtext und UI: **Inter** (400/500/600/700)
- Selbst gehostet als woff2 (keine Google-Fonts-Abfrage, DSGVO). Die Dateien liegen bereits unter
  `~/Documents/Claude/Projects/Pretty Woman Brautmoden/Website/assets/brautkleid-beratung/fonts/` → nach `black-week/fonts/` kopieren.

### Form und Bewegung
- Radien 24 / 14 / 8 px. Schatten weich und warm: `0 14px 34px rgba(20,20,20,.10)`. Easing `cubic-bezier(.22,.61,.36,1)`.
- Section-Abstand 88 px, mobil 56 px. Max. Inhaltsbreite 1220 px, Gutter 24 px (mobil 18 px).
- Dünne goldene Linien als Trenner und Rahmen sind das Erkennungszeichen.
- Bewegung sparsam: sanftes Einblenden, leichtes Anheben beim Hover. **Keine bewegungsintensiven Scroll-Effekte** (Parallax, Scroll-Jacking): der Kundin wird davon übel. Alles hinter `prefers-reduced-motion`.
- Icons: Linien-Icons in Gold (36–48 px, Strich 1,4 px). **Keine Emojis** vor Aufzählungen, Schritten oder Benefits. In H1/H2 sparsam erlaubt (🤍).

### Minimalismus
- Keine redundanten Infos und keine dekorativen Großbuchstaben-Labels wie „BLACK SALE 2026“ oder „LIMITED OFFER“ über Überschriften. Jede Zeile muss eine Information tragen.
- Kein Prozent-Feuerwerk, keine roten Preisschilder, keine Durchstreich-Orgie.

### Tonalität
- Warm, ehrlich, ruhig, nie marktschreierisch. Kurze Sätze. Dringlichkeit nur über echte Fakten (Zeitraum, begrenzte Termine).
- **Das Wort „Druck“ nicht verwenden** (Kundenwunsch vom 27.10.). Stattdessen: „Persönliche, kompetente und empathische Beratung.“
- **Ansprache IMMER großschreiben:** Du, Dich, Dir, Dein/Deine/Deinen/Deinem/Deiner, Ihr, Euch, Euer/Eure. Auch mitten im Satz, in Buttons, FAQ, Alt-Texten und Meta-Description. Julians LP schreibt klein („du“), das muss überall korrigiert werden. Ausnahme: wörtliche Google-Rezensionen. Vor Abgabe Wort für Wort prüfen.
- Großschreibung nach Doppelpunkt, wenn ein ganzer Satz folgt.

### Fakten, die auf der ganzen Website gelten
- Über 400 Kleider, Gr. 30 bis 66
- Über 15.000 Kundinnen und Kunden
- Seit 30 Jahren in Mühlacker
- 2 Stunden Beratung im eigenen Separee, bis zu 5 Begleitpersonen, kostenlos
- Outlet sonst ab 500 €
- Schreibweise „In-House-Juwelier“, „gelernte Goldschmiedin“ (nur falls erwähnt)
- Adresse: Stuttgarter Straße 37, 75417 Mühlacker · Telefon 07041 810225

---

## 5. Was aus Julians LP übernommen wird und was nicht

**1:1 übernehmen (Funktion, nicht Optik):**
- Consent-Banner, Google Consent Mode v2, GTM `GTM-PLBF7LSN` erst nach Zustimmung, `localStorage`-Key `pw_consent`
- Meta-Pixel `350174173102316` nach Zustimmung, Conversions-API-Relay (cookielos ohne Zustimmung), Clarity (cookielos ohne Zustimmung)
- Alle `dataLayer`-Events und `data-cta`-Attribute. Ergänze überall `lp_variant: 'black_week'`, damit die Aktion in GTM, Meta und Clarity getrennt auswertbar ist. Neue CTA-Werte: `hero`, `offers`, `audience_2027`, `audience_soon`, `suits`, `close`, `dock`.
- BridalLive-iframe inkl. Fallback, Termin-gebucht-Event
- Mobile-Dock, Logik „Kalender direkt nach dem Hero erreichbar“

**Raus bzw. ersetzen:**
- Preis-Section „Was kostet ein Brautkleid bei uns?“ → ersetzt durch die Angebotskarten
- Bodoni Moda, Jost, Julians Farbtokens
- Kleinschreibung der Anrede, das Wort „Druck“, „Caro“

---

## 6. Bilder

**Neue Kollektion** (Google Drive, Shared Drive Velonify):
`07_Client-Share / Pretty Woman Brautmoden (shared) / Brautkleid Bilder`
https://drive.google.com/drive/folders/1MPNTLs1A05KnUtIKOW9XSKVredqGl7te

Unterordner, angelegt am 29.10.2026:
- A-Linie (31 Bilder) · https://drive.google.com/drive/folders/1tccjZTYW-pjARnAheyXw1Y5aj-6mU1CZ
- Fit & Flair und H-Linie (21) · https://drive.google.com/drive/folders/1imEyZ_C_UmVDqwq2sRekTMjW42GVvvRM
- Prinzessin (17) · https://drive.google.com/drive/folders/14RCzld6TEDNi_YZkoSKl7pQzYCySOkD8
- Curvy (31) · https://drive.google.com/drive/folders/1I5GULfonwDvMpitJhAbUP7iQOjoBRPub

Dateien mit `M26` im Namen (z. B. `SY8341-M26-CAT-SY-03-510x765.jpg`) sind die Modelle 2026. **Vor dem Einbau mit Johannes klären, welche Bilder genau die frisch eingetroffene Kollektion zeigen.** Bis dahin die M26-Bilder verwenden.

**Anzüge:** `Pretty Woman Brautmoden (shared) / Anzug Bilder`
https://drive.google.com/drive/folders/1iIE8R90_wNXelyug-pMRTWHM3s9rvZTJ

**Verarbeitung:** Die Bilder nicht von Drive verlinken. Herunterladen, als WebP in 720 und 1200 px Breite exportieren (Originale sind teils 20 MB groß), unter `black-week/img/` ablegen, mit `srcset`, `width`/`height`, `loading="lazy"` (außer Hero) und deutschen Alt-Texten (Schnitt + Detail, Anrede groß). Herstellerbilder nicht beschneiden, sodass Logos oder Wasserzeichen sichtbar bleiben.

---

## 7. Technik und Qualität

- Eine Datei `black-week/index.html`, Fonts und Bilder als Assets im selben Ordner. Externe Skripte nur die, die Julian schon lädt.
- Meta: Title „Black Week Wedding Edition · Pretty Woman Mühlacker“, Description mit Zeitraum und den drei Angeboten, OG-Bild aus der neuen Kollektion, `noindex`.
- Mobile first. Prüfen bei 320, 375, 430, 768, 1280 und 1440 px: keine horizontale Scrollleiste, Hero-Button ohne Scrollen sichtbar.
- Lighthouse mobil: Performance ≥ 90, Accessibility ≥ 95. Fokus-Stile sichtbar, Kontraste WCAG AA.
- Countdown, Termin-Übersicht und 26.11.-Flag mit simuliertem Datum testen (vor, während, nach der Aktion).
- Am Ende: kurze `black-week/README.md` (Aufbau, Flags, offene Punkte) und ein Screenshot Desktop + Mobil.
- **Nichts committen oder pushen**, bis Johannes die Seite abgenommen hat.

---

## 8. Offene Punkte (als sichtbare Platzhalter `[[…]]` markieren, nicht raten)

1. **Preisangabe (rechtlich):** Für „reduziert auf 799 €“ und „reduzierte Anzüge“ keine durchgestrichenen Altpreise und keine Prozentangaben verwenden, solange der niedrigste Preis der letzten 30 Tage nicht vorliegt (§ 11 PAngV). „Für 799 €“ / „ab 150 €“ als Black-Week-Preis ist unkritisch.
2. **200-€-Rabatt:** Gilt er auf alle Kleider der neuen Kollektion? Ab welchem Kleidpreis? Nur bei Bestellung innerhalb der Black Week? Kombinierbar?
3. **26.11.:** Termine bestätigt ja/nein.
4. **Termintyp in BridalLive:** Gibt es einen eigenen Termintyp „Black Week“? Sonst Hinweis wie bei Julian („1. Anprobe Brautkleid“).
5. **Bildauswahl** neue Kollektion (siehe Abschnitt 6).
6. **Anzahl Google-Bewertungen** am Tag vor Livegang aktualisieren.
