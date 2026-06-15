# D4RYL — Website Build Brief (für Claude Code)

Auftrag: eine **statische Single-Page-Artist-Website** für D4RYL bauen, deploybar
auf GitHub Pages oder Porkbun Static Hosting, Domain `kernelrec.com`.
Diese Datei ist die Vorgabe — lies sie und setze die Seite danach um.

## Ziel & Deliverable

- Eine schnelle, mobile-first Single-Page-Site (ein `index.html` + `style.css`).
- **Kein Build-Schritt, kein Framework** — reines HTML/CSS (+ minimal JS falls nötig),
  damit es auf jedem Static-Host ohne Setup läuft.
- Dunkle, reduzierte „System/Terminal"-Optik (siehe Design-Richtung).

## Markenkontext

- **DNZ OS** = Studio-System (intern, nicht auf der Seite).
- **Kernel** = Label / Imprint → erscheint im Footer (℗ 2026 Kernel) + Kontaktadressen.
- **D4RYL BAND** = der Artist, öffentliches Gesicht der Seite (Trap & Lofi, Hamburg).

## Seitenstruktur (8 Blöcke, in dieser Reihenfolge)

Reihenfolge = abnehmende Dringlichkeit. Zwei Blöcke sind **launch-kritisch** (müssen
zum Release 24.07.2026 stehen), der Shop ist **Phase 2** (Platzhalter, nach Launch).

1. **Nav** — Logo „D4RYL" links, Anker-Links rechts (Musik · Shop · Links).
2. **Hero** — „D4RYL BAND", Tagline „Trap & Lofi · Hamburg", Primär-Button „Jetzt hören".
   Platz für das Waveform/DNA-Logo als zentrales Element.
3. **Neue Single** *(launch-kritisch)* — Cover, Titel, „out 24. Juli", Buttons Pre-save + Spotify.
4. **Musik** — Platzhalter für Spotify-Player-Embed (kommt, wenn der Track live ist).
5. **Shop** *(Phase 2)* — Produktkarten (Beats, Sample-Packs, exkl. Tracks) mit Preis +
   „Kaufen". Buttons **verlinken nach außen** (Gumroad/Bandcamp/Telegram) — KEIN
   Checkout auf der Seite. Vorerst als sichtbarer Platzhalter/„coming soon" bauen.
6. **Links** — Link-Hub (Spotify, Apple Music, YouTube, Instagram, …), je Button mit Icon.
7. **Newsletter** *(launch-kritisch)* — eingebettetes **Brevo-Anmeldeformular**
   (E-Mail-Feld + „Anmelden"). Platzhalter für den Brevo-Embed-Code / Form-Action.
8. **Footer** — „Kernel", „℗ 2026 Kernel · kernelrec.com", Kontakt:
   `hello@` · `sync@` · `press@` (@kernelrec.com).

## Design-Richtung

- **Dunkel & nächtlich** — fast schwarzer Hintergrund, heller Text. (Optional: zusätzlich
  ein Light-Mode, aber Dark ist die Hauptidentität.)
- **System/Terminal-Anleihen** — Sektions-Labels in Monospace, klein, uppercase,
  leicht gesperrt (letter-spacing), wie in der Wireframe-Skizze.
- **Eine Akzentfarbe** als „Signal"-Farbe für Buttons/Hovers. Default: kühles Teal.
  Als CSS-Variable `--accent` oben definieren, damit leicht änderbar (Alternativen: Amber, Violett).
- **Flach** — keine Verläufe, keine Schlagschatten. Klare Kanten, viel Ruhe.
- **Mobile-first**, responsiv bis Desktop (zentrierte schmale Spalte, max ~480px).
- Typografie: serifenlose Grundschrift, Monospace nur für Labels/Akzente. Zwei Schriftgewichte.
- Sauberes, semantisches HTML; alt-Texte; gute Performance (keine schweren Libs).

## Integrationen (Platzhalter lassen, klar markiert)

- **Brevo-Formular:** Newsletter-Block bekommt das eingebettete Brevo-Formular.
  Platzhalter-Kommentar `<!-- BREVO FORM EMBED HIER -->` + ein funktionierendes
  Fallback-Markup (E-Mail-Input + Button), das ich später durch den echten Embed ersetze.
- **Streaming-Links:** als Variablen/Konstanten oben sammeln (Spotify-URL, Apple, YouTube,
  Instagram), damit ich nur eine Stelle pflegen muss. Vorerst `#`-Platzhalter.
- **Shop-Links:** pro Produkt eine externe URL (Gumroad/Bandcamp/Telegram), `#`-Platzhalter.

## Inhalte (Platzhalter, fülle ich später)

- Track-Titel, Cover-Bild (Platzhalter-Bild einbinden), Release-Datum 24.07.2026.
- Kurze Bio (2–3 Sätze, Platzhaltertext).
- Logo/Waveform-Grafik (Platzhalter-SVG, ersetze ich durch mein Tron-inspiriertes Logo).

## Datei-Struktur

```
/ (Repo-Wurzel)
  index.html
  style.css
  assets/        (Logo, Cover, Bilder)
  CNAME          (Inhalt: kernelrec.com  — nur für GitHub Pages)
  README.md
```

## Deployment

Beide Wege ziehen die Seite aus dem GitHub-Repo — Seitencode ist identisch.

- **GitHub Pages (gratis, bevorzugt):** Repo anlegen, Pages aktivieren. `CNAME`-Datei mit
  `kernelrec.com`. Bei Porkbun **nur die Web-Records manuell** ergänzen
  (A-Records auf GitHub-Pages-IPs + `www`-CNAME) — die „Quick DNS Config" NICHT nutzen,
  weil sie bestehende Records überschreiben kann.
- **Porkbun Static Hosting (Alternative):** „Static Hosting" → „GitHub Connect" → Repo wählen.

### ⚠️ DNS-Sicherheit (wichtig)

Das E-Mail-Setup auf `kernelrec.com` läuft bereits (Porkbun-Weiterleitung + Brevo).
Beim Hinzufügen der Web-Records **dürfen MX und die Brevo-Einträge (Brevo-Code, DKIM,
DMARC) NICHT entfernt oder überschrieben werden.** Nur A/CNAME fürs Web ergänzen,
E-Mail-Records unangetastet lassen.

## Reihenfolge der Umsetzung

1. Grundgerüst `index.html` + `style.css` mit allen 8 Blöcken (Platzhalter-Inhalte).
2. Dark-System-Design feinschleifen (Akzentfarbe, Monospace-Labels, Hero).
3. Brevo-Form-Fallback + Link-Konstanten einbauen.
4. `CNAME` + `README` ergänzen, lokal testen.
5. Erst danach: Repo pushen, Hosting verbinden, bei Porkbun Web-Records setzen.
