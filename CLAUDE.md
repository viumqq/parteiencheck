# Projekt: parteiencheck.org

Statische Website (kein Build-Schritt). Live über **Netlify**, Deploy automatisch aus `main`.
Domain: www.parteiencheck.org (bei Netlify als Primary). Betreiber: viumqq.

## Dateien
- `index.html` — Wahlversprechen-Check (8 Parteien, ~100 Karten). Vergleichsblock oben.
- `steuergelder.html` — Steuergeld-Check (27 Karten, 6 Themen, Haushalts-Balken).
- `teilen.html` — Zum Teilen: screenshotbare Social-Media-Karten (Post 1:1 / Story 9:16),
  Inhalte per `fetch()` live aus index.html/steuergelder.html gezogen, keine eigenen Daten.
  Kartendesign reichweiten-optimiert: Marken-Zeile, Vorher/Nachher (Versprochen/Ergebnis),
  Rang-Medaillen, Hashtags — Inhaltsdichte passt sich per Container-Query der Kartengröße an.
- `style.css` — gemeinsames CSS aller drei Seiten.
- `robots.txt`, `sitemap.xml` — SEO-Grundlagen.
- `og-index.png`, `og-steuergelder.png`, `og-teilen.png` — Social-Vorschaubilder (1200×630).
- Seitenmenü oben verbindet alle drei Seiten.

## Design
Schwarz-Weiß-Dashboard, Parteifarben nur als Akzent, Ampelfarben für Status. Nur Inter-Font,
heller Modus. Mobil: Partei-Kacheln im 2-Spalten-Raster, Status-Filter klebt. Statistiken
werden per JS live aus den Karten berechnet (nicht hartkodiert). Desktop: Versprechen-Karten
einspaltig (volle Breite des Hauptcontainers), nicht im 2er-Raster. Favicon: einfaches
schwarzes Balkendiagramm (Inline-SVG, kein Asset).

## Quellen-Regel (wichtig)
NUR offizielle Quellen: bundestag.de, dip.bundestag.de, bundesregierung.de, Ministerien,
bundesrechnungshof.de, bundesverfassungsgericht.de, destatis, bmz.de — und Partei-Wahlprogramme.
Keine Medien/Zeitungen/Blogs. Bewertungen = Prüfergebnisse, keine Meinung.

## Arbeitsweise (Workflow)
1. Entwicklung immer auf Branch `claude/docker-setup-workflow-9j55aj`.
2. Commit + Push → Pull Request → Netlify Deploy Preview.
3. Nutzer sieht Vorschau, gibt frei → PR mergen → live. Nie ohne Freigabe live schalten.
4. **Keine Screenshots im Chat zeigen** — dem Nutzer genügt die Netlify-Vorschau.
   (Playwright trotzdem intern zur Prüfung nutzen, nur nicht mit SendUserFile posten.)
5. Lokaler Test: `python3 -m http.server 8080` + Playwright/Chromium unter /opt/pw-browsers/chromium.

## Nutzer-Präferenzen (wichtig)
- Antworten immer so knapp wie möglich — nur das Nötige, keine unnötigen Erklärungen.
- Token sparen: NICHT den Chatverlauf durchsuchen — diese Datei ist die Quelle für den Stand.
- Bei „**merk dir den Stand**": Wichtigstes hier knapp festhalten, dann dem Nutzer sagen
  „Stand gesichert — Chat kann weg". (Chat-Löschen macht der Nutzer selbst / `/clear`.)

## Offener Stand (bei Sessionstart prüfen)
- Nichts offen. Zuletzt live (2026-07-19):
  - Desktop-Layout: Versprechen-Karten einspaltig, volle Containerbreite.
  - "Verfehlt"-Karte (400.000 Wohnungen, SPD) von `progress` auf `failed` (rot) korrigiert.
  - `teilen.html`-Karten überarbeitet: Marken-Zeile, Versprochen/Ergebnis-Format, Rang-Medaillen,
    Hashtags — Dichte je nach Kartengröße per Container-Query gesteuert.
  - Performance: Font-Preconnect, `no-cache` statt `no-store` beim Live-Fetch in teilen.html,
    effizientere Stats-Berechnung in index.html (keine Funktionsänderung).
  - Favicon (schwarzes Balkendiagramm, Inline-SVG).
  - SEO: robots.txt, sitemap.xml, Canonical-Tags, JSON-LD (WebSite), OG-/Twitter-Bilder,
    gestraffte Meta-Descriptions (keine Inhaltsänderung, nur Metadaten).
- Lokaler Shortcut eingerichtet: Funktion `parteiencheck` in `~/.zshrc` (cd + `claude` Start).
- Optional-Idee noch offen: Kategorie/Hinweis für Oppositions-Erfolge
  (z. B. erfolgreiche Verfassungsklage der Union) — nur auf Wunsch umsetzen.
- Aktuellen Stand mit `gh pr list` / offenem PR prüfen, nicht den Chat durchsuchen.
