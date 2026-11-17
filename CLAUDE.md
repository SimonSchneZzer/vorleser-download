# vorleser-download – Hinweise für AI-Assistenten

Öffentliche Download-Seite (https://simon.schnetzer.at/vorleser/, seit 2026-11-17 auf dem Homeserver) und
Releases der Desktop-App **Vorleser**. Der Quellcode der App liegt im öffentlichen Repo `SimonSchneZzer/vorleser` (GPL-3.0)
(lokal `../vorleser`); Entscheidungen und Begründungen stehen dort in `docs/DECISIONS.md`.

- **Eine Datei:** `site/index.html` (CSS + JS inline, kein Build). Icons: `site/icon.png`, `site/favicon.png`.
- **Hosting:** `site/` wird auf dem Homeserver mit `~/vorleser/deploy.sh` veröffentlicht (nginx-Container
  `vorleser-web`, Caddy `handle_path /vorleser/*`). GitHub Pages (Branch `main`, Wurzel) liefert nur noch
  `latest.json` für den Updater der App (alte Versionen fragen nur dort – **nie verschieben oder löschen**) und
  `index.html` = Weiterleitung auf die neue Adresse (Suche + Hash bleiben). Die Seite lädt latest.json von dort
  (CORS offen). Root-`icon.png`/`favicon.png` bleiben für alte Vorschaukarten liegen.
- **Sprache:** Deutsch steht im HTML (Grundfassung für Suchmaschinen/ohne JS). Ist die Browsersprache nicht
  Deutsch, ersetzt das Skript die Texte über das Objekt `EN` (CSS-Selektor → englisches HTML) und
  `FEATURES_EN`. Neue Texte immer in **beiden** Sprachen pflegen. Testen: `?lang=en` / `?lang=de`.
- **Download-Links** zeigen auf `releases/latest/download/Vorleser-mac.dmg` bzw.
  `…/Vorleser-windows-setup.exe` – diese Dateinamen sind fest (auch der Updater in der App nutzt sie).
- **Releases** werden vom Workflow im App-Repo angelegt (Tag `vX.Y.Z`), nicht von Hand hier.
- **Animationen** orientieren sich am Onboarding der App (`--ease`, `--ease-out`, `--spring`) und laufen
  **einmal** ab (Wunsch des Nutzers, keine Endlosschleifen). `prefers-reduced-motion` wird respektiert.
- **Logo statisch:** dunkle Fläche `--logo` #25292D, Balken `--logo-bar` #5FB7CB (mittel, hoch, mittel, kurz) – in
  jedem Modus gleich: oben, Mini-App der Anleitung, „Mit deiner eigenen Stimme“, `icon.png`, `favicon.png`.
  Icons erzeugt `../vorleser/packaging/make_icon.py` (Favicon mit `--tight`, ohne Rand). Neues Favicon →
  Zähler im Link erhöhen (`favicon.png?v=N`), Browser halten das alte sonst lange im Cache.
- **Hintergrund-Welle** (`voiceBg`): bleibt in der Höhe immer in der Fenstermitte, folgt der Maus nur seitlich;
  jede Mausbewegung (auch hoch/runter) lässt sie stärker schwingen. Bewusst dezent, Stellschrauben oben im Skript.
- Mitlese-Demo: **eine** Markierungs-Box gleitet von Wort zu Wort (wie in der App), kein Überblenden.
- Installationsschritte: Umschalter Mac | Windows mit animierten Szenen statt Akkordeon (Wunsch des Nutzers).
- Nach Klick auf einen Download-Knopf: Reiter des Systems wählen, zur Anleitung scrollen, Schritte leuchten
  einmal auf. (Das Ende eines Browser-Downloads ist für Webseiten nicht erkennbar – bewusst beim Start.)
- Abkürzungen: Mac `xattr -cr …` (Quarantäne), Windows `Unblock-File …` (Mark of the Web) – beide mit Kopierknopf.
