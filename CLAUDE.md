# Projekt: parteiencheck.org

Statische Website (kein Build-Schritt). Live über **Netlify**, Deploy automatisch aus `main`.
Domain: www.parteiencheck.org (bei Netlify als Primary). Betreiber: viumqq.

## Dateien
- `index.html` — Wahlversprechen-Check (8 Parteien, ~100 Karten). Vergleichsblock oben.
- `steuergelder.html` — Steuergeld-Check (27 Karten, 6 Themen, Haushalts-Balken).
- `style.css` — gemeinsames CSS beider Seiten.
- Seitenmenü oben verbindet beide Seiten.

## Design
Schwarz-Weiß-Dashboard, Parteifarben nur als Akzent, Ampelfarben für Status. Nur Inter-Font,
heller Modus. Mobil: Partei-Kacheln im 2-Spalten-Raster, Status-Filter klebt. Statistiken
werden per JS live aus den Karten berechnet (nicht hartkodiert).

## Quellen-Regel (wichtig)
NUR offizielle Quellen: bundestag.de, dip.bundestag.de, bundesregierung.de, Ministerien,
bundesrechnungshof.de, bundesverfassungsgericht.de, destatis, bmz.de — und Partei-Wahlprogramme.
Keine Medien/Zeitungen/Blogs. Bewertungen = Prüfergebnisse, keine Meinung.

## Arbeitsweise (Workflow)
1. Entwicklung immer auf Branch `claude/docker-setup-workflow-9j55aj`.
2. Commit + Push → Pull Request → Netlify Deploy Preview.
3. Nutzer sieht Vorschau, gibt frei → PR mergen → live.
4. Nutzer nie ohne Freigabe live schalten. Screenshots (Desktop+Mobil) vor Freigabe zeigen.
5. Lokaler Test: `python3 -m http.server 8080` + Playwright/Chromium unter /opt/pw-browsers/chromium.

## Offener Stand (bei Sessionstart prüfen)
- PR #6 „Vergleichsblock" offen: zeigt je Partei den % umgesetzter Versprechen als Balken,
  sortiert. Wartet auf Freigabe. Optionale Erweiterung noch offen: Hinweis/Kategorie für
  Oppositions-Erfolge (z. B. erfolgreiche Verfassungsklage der Union).
- Aktuellen Stand mit `list_pull_requests` / offener PR prüfen, nicht den Chat durchsuchen.
