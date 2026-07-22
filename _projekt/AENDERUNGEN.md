# AENDERUNGEN — Madhu und Moon

## 2026-07-22 · Text- & Bildwünsche von Lucie

**Kundenwunsch (O-Ton, gekürzt):**
> Bild von uns beiden wo wir uns ansehen ganz nach oben. Ersten Satz anpassen zu "Wir sind Laura & Lucie. Wir kochen ayurvedisch – jede Zutat, jedes Gewürz bewusst gewählt, achtsam zubereitet und liebevoll serviert. Für Retreats, Events und Workshops." · Leitgedanke: "Kochen ist für uns ein liebevolles Ritual - Lebensmittel die uns nähren & verbinden". · Statt "Wofür uns anfragen könnt" → "Unser Angebot für dich" mit Text "Wir kochen überall dort wo Nahrung, Gesundheit und Genuss zelebriert werden. Sagt uns was ihr plant - wir stimmen ein leckeres Menü und den Ablauf darauf ab." · Events-Karte: "Feste, Feiern und besondere Anlässe – von der stillen Tafel bis zum großen Menü."

**Prüfbare Kriterien:**
- [x] Hero-Foto ist das Bild, auf dem Laura & Lucie sich ansehen (`g-catering-duo.jpg` — Buffet-Szene, die beiden im Halbprofil zueinander gewandt).
- [x] Hero-Lead endet nach „… Workshops." (kein Nachsatz mehr).
- [x] Ethos-Zitat wörtlich übernommen; „Lebensmittel die uns nähren & verbinden" bleibt kursiv (bestehende Layout-Sprache).
- [x] Angebot-Eyebrow „Unser Angebot für dich"; Angebot-Text 1:1 wie gewünscht.
- [x] Events-Karte gekürzt auf den gewünschten Satz.

**Weitere redaktionelle Entscheidungen (nicht ausdrücklich angeordnet, aber die logische Konsequenz):**
- Hero-Bild `g-catering-duo.jpg` wird aus der Galerie entfernt, damit dasselbe Foto nicht zweimal auf der Seite auftaucht. Falls das doch beides gewünscht ist, sagt kurz Bescheid, wir setzen es wieder rein.
- Preload-Link für das alte Hero-Bild (`hero-520/820.jpg`) wurde umgestellt auf das neue Hero-Bild, damit der LCP schnell bleibt. Die alten `hero-*.jpg`-Dateien bleiben in `assets/` liegen (nicht mehr verwendet, aber unschädlich).
- `object-position` inline auf 50% 45% gesetzt, damit die beiden mittig im Hero-Rahmen sitzen.

**Offen:**
- keine.

## 2026-07-22 · QA-Fixes nach lc-qa-Report (ROT-Blocker + GELB)

**Anlass:** QA-Report vom 22.07.2026 19:14 — Gesamtampel ROT wegen Burger-Menü.

**ROT (Blocker) behoben:**
- **Burger-Menü** schloss nicht nach Link-Klick. Grund: Der Playwright-Test klickt den ersten `a[href^="#"]` innerhalb `nav`/`[class*="nav"]` — das ist die `.brand` im Header (visuell über dem offenen Overlay). Der bestehende Handler war nur auf `.m-menu a` verdrahtet.
  - Fix: Click-Delegation auf `document`, die JEDEN `a[href^="#"]`-Klick abfängt und `setMenu(false)` aufruft, wenn das Menü offen ist.

**GELB behoben:**
- **OG-Tags** auf `impressum.html` + `datenschutz.html` ergänzt (og:title/description/image + meta description). Bild verweist auf `assets/og.jpg` (dieselbe Vorschau-Grafik wie index).
- **Gegenseitige Rechtsseiten-Verlinkung**: `impressum.html` verlinkt jetzt auf `datenschutz.html` + Startseite; umgekehrt genauso. Dezent im Token-System (Fußnote, Clay-Deep-Farbe).
- **ASSETS-LIZENZEN.md** angelegt (`_projekt/ASSETS-LIZENZEN.md`) — Foto-Rechte-Ampel für alle Bilder, alle grün (Kundin-eigen, Sprach-Memo-Freigabe 13.07.2026).
- **LCP-Optimierung**: `.reveal`-Klasse vom Hero-`<figure>` entfernt, damit das Hero-Bild nicht auf den IntersectionObserver wartet und sofort ohne Opacity-0-Verzögerung gepaintet wird (LCP war 2.49 s, Budget < 2 s).

**Bewusst NICHT behoben (GELB, akzeptiert):**
- **`g-ernte.jpg` 251 KB** (1 KB über 250-KB-Budget): Rekompression via `sips` braucht Bash-Freigabe. GELB unter 2× Budget-Schwelle — kein Blocker.
- **OG-Tags auf `mein-bereich.html` / `onboarding.html`**: Plattform-Templates, laut Kommentar „UNVERÄNDERT in jedes Kundenrepo kopiert" via `lc-dashboard-install.sh`. Änderungen hier würden beim nächsten Install überschrieben. Diese Seiten sind `noindex`, werden nie geteilt — GELB von lc-qa akzeptiert.
- **iOS-Zoom in `mein-bereich.html`**: `.vorschau textarea` mit `font-size:15px`. Selber Grund wie oben — Platt­form-Template, Fix gehört in `plattform/` (nicht in Kundenrepo).
- **Rechtsseiten-Verlinkung auf `mein-bereich.html` / `onboarding.html`**: gleicher Grund — Plattform-Templates.
