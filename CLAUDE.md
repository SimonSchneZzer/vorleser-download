# vorleser-download – Hinweise für AI-Assistenten

Öffentliche Download-Seite (GitHub Pages: https://simonschnezzer.github.io/vorleser-download/) und
Releases der Desktop-App **Vorleser**. Der Quellcode der App liegt im privaten Repo `SimonSchneZzer/vorleser`
(lokal `../vorleser`); Entscheidungen und Begründungen stehen dort in `docs/DECISIONS.md`.

- **Eine Datei:** `index.html` (CSS + JS inline, kein Build). Icons: `icon.png`, `favicon.png`.
- **Sprache:** Deutsch steht im HTML (Grundfassung für Suchmaschinen/ohne JS). Ist die Browsersprache nicht
  Deutsch, ersetzt das Skript die Texte über das Objekt `EN` (CSS-Selektor → englisches HTML) und
  `FEATURES_EN`. Neue Texte immer in **beiden** Sprachen pflegen. Testen: `?lang=en` / `?lang=de`.
- **Download-Links** zeigen auf `releases/latest/download/Vorleser-mac.dmg` bzw.
  `…/Vorleser-windows-setup.exe` – diese Dateinamen sind fest (auch der Updater in der App nutzt sie).
- **Releases** werden vom Workflow im App-Repo angelegt (Tag `vX.Y.Z`), nicht von Hand hier.
- **Animationen** orientieren sich am Onboarding der App (`--ease`, `--ease-out`, `--spring`) und laufen
  **einmal** ab (Wunsch des Nutzers, keine Endlosschleifen). `prefers-reduced-motion` wird respektiert.
- Mitlese-Demo: **eine** Markierungs-Box gleitet von Wort zu Wort (wie in der App), kein Überblenden.
- Installationsschritte: Umschalter Mac | Windows mit animierten Szenen statt Akkordeon (Wunsch des Nutzers).
