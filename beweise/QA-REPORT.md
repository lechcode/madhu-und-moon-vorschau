# QA-Report: madhu-und-moon

**Gesamtampel: 🟡 GELB** · 0 rot / 7 gelb / 8 grün · 22.07.2026 19:25 · Dauer 33 s · lc-qa.py

## 5-Minuten-Abnahme (Mensch)
1. Alle 🔴 unten abgearbeitet? 2. Screenshots in `qa-shots/` überflogen — „würde ich das verschicken?"
3. ROT-Assets in ASSETS-LIZENZEN.md ok für Vorschau? 4. MAIL-KUNDE/VERSAND-NACHRICHT gelesen? 5. Link einmal am eigenen Handy antippen.

## 🔴 ROT (Blocker)
- —

## 🟡 GELB (prüfen/dokumentieren)
- **OG-Tags mein-bereich.html**: fehlt: og:title, og:description, og:image
- **OG-Tags onboarding.html**: fehlt: og:title, og:description, og:image
- **Bild-Budget**: g-ernte.jpg: 251 KB (> 250)
- **impressum.html nicht verlinkt von**: mein-bereich.html, onboarding.html
- **datenschutz.html nicht verlinkt von**: mein-bereich.html, onboarding.html
- **LCP**: 2.48 s (Budget < 2 s)
- **iOS-Zoom mein-bereich.html**: 1 Eingabefeld(er) mit font-size < 16px

## 🟢 GRÜN
- **Interne Links & Assets**: alle Verweise in 5 Seiten existieren
- **Externe Requests**: keine (cookiefrei/0 Tracker bestätigt)
- **OG-Tags**: index/vorschau vollständig
- **Grep-Fallen & noindex**: clamp/calc sauber, noindex gesetzt
- **Lighthouse Performance (mobil)**: 97 (Budget ≥ 95)
- **Lighthouse A11y**: 100 (Ziel 100; 90–99 = Hinweis, < 90 blockt)
- **Burger-Menü index.html**: öffnet, navigiert, schließt
- **Playwright-Screenshots**: 5 Seiten × 3 Breiten → qa-shots/
