# Projekt-Gerüst

So ist ein Projekt-Repo aufgebaut. Vorlage: `cad/` im DragonFist-Repo
(github.com/thomashacker/dragonfist).

```
cad/
  parameter.py     alle Maße und Mengen, ungeprüfte mit "# MESSEN"
  modell.py        Geometrie (build123d), liest nur parameter.py
  elektronik.py    Platinen, Klemmen, Adern mit Wegen
  build.py         erzeugt alles unten, schreibt Bericht.txt mit OK/!!
  pruefen.py       Kollisionsprüfung aller festen Teile, ERLAUBT-Liste
  pruefteile.py    Prüfstücke, aus echten Teilen herausgeschnitten
  stufen.py        Baustufen für Blender/Viewer
  viewer/          Browser-Viewer (glb), Druckphasen filterbar
  wokwi.py         Wokwi-Simulation aus derselben Pinbelegung
  schaltplan.py    KiCad-Schaltplan aus denselben Daten
  bestellt.json    privat (gitignore): Bestellungen, Status, Haken
  ausgabe/         erzeugt (gitignore): druck/, pruefdruck/, Bilder, glb, step
  LIESMICH.md      "Nach jeder Änderung": Schritte zum Neubauen
  Messliste.md     erzeugt: Modell- gegen Messwerte
  Pruefdruck.md    erzeugt: Prüfstücke, Prüffragen, Reihenfolge
  Einkaufsliste.md privat, erzeugt aus bestellt.json
  Verkabelung.md   erzeugt: jede Ader von → nach, Brücken, Pins
pico/  app/  monitor/  tests/   Firmware, Oberfläche, Live-Monitor, pytest
```

## Bausteine, die sich bewährt haben

- `quader(x0, x1, y0, y1, z0, z1)` und `zyl_z(x, y, z0, z1, d)` statt verschachtelter
  Locations: Koordinaten bleiben lesbar.
- `zerteilen(form)` an Trennfugen, wenn ein Teil größer als das Druckbett ist, mit
  Schwalbenschwänzen (Spiel als Parameter) zum Verkleben.
- `gramm(form, schale=0.9, fuellung=0.2)`: `min(volumen, fläche × schale)` voll, Rest mit
  Füllgrad, Dichte PLA 1,24.
- Prüfungen im Build, jede schreibt eine Zeile `OK` oder `!!`:
  Druckbett-Maß, Kollisionen, Kabellänge, Klemmen-Einlässe, Filament gegen Rollen,
  physikalische Grenzen des Projekts.
- Eine Pinbelegung (`pins.json`) für Firmware, Simulation, Schaltplan und Anleitung.

## Werkzeuge

- Python-Umgebung für build123d unter kurzem Pfad (z. B. `%USERPROFILE%\b123d`).
- Ausgabe mit `PYTHONIOENCODING=utf-8`, sonst brechen Umlaute auf Windows.
- Blender headless zum Rendern von Vorschaubildern; `blender_laden.py` ersetzt Collections.
- Bambu Studio als Slicer; Gramm und Zeit von dort zurück ins Modell.
