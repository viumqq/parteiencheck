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
3. Nutzer sieht Vorschau, gibt frei → PR mergen → live. Nie ohne Freigabe live schalten.
4. **Keine Screenshots im Chat zeigen** — dem Nutzer genügt die Netlify-Vorschau.
   (Playwright trotzdem intern zur Prüfung nutzen, nur nicht mit SendUserFile posten.)
5. Lokaler Test: `python3 -m http.server 8080` + Playwright/Chromium unter /opt/pw-browsers/chromium.

## Nutzer-Präferenzen (wichtig)
- Token sparen: NICHT den Chatverlauf durchsuchen — diese Datei ist die Quelle für den Stand.
- Bei „**merk dir den Stand**": Wichtigstes hier knapp festhalten, dann dem Nutzer sagen
  „Stand gesichert — Chat kann weg". (Chat-Löschen macht der Nutzer selbst / `/clear`.)

## Offener Stand (bei Sessionstart prüfen)
- Nichts offen. Zuletzt live gemergt: Vergleichsblock (Prozent-Balken je Partei), CLAUDE.md.
- Optional-Idee noch offen: Kategorie/Hinweis für Oppositions-Erfolge
  (z. B. erfolgreiche Verfassungsklage der Union) — nur auf Wunsch umsetzen.
- Aktuellen Stand mit `list_pull_requests` / offenem PR prüfen, nicht den Chat durchsuchen.
