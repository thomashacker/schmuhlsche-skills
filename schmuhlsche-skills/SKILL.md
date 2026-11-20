---
name: schmuhlsche-skills
description: Vorgehen für Maker- und Hardware-Projekte mit 3D-Druck, parametrischem CAD (build123d), Elektronik (Raspberry Pi Pico, Sensoren, Netzteile, Wago) und Einkauf. Verwenden, sobald ein neues Gerät, Gehäuse, eine Halterung, ein Messgerät oder Ähnliches geplant, konstruiert, bestellt, gedruckt oder verkabelt wird, und bei jeder Rückschau nach einem solchen Projekt.
---

# Hardware-Projekte nach Schmuhl-Art

Gewachsen aus DragonFist (Schlag-Messgerät, Herbst 2026). Ziel: Teile passen beim ersten
echten Druck, nichts wird doppelt gekauft, und jeder Fehler passiert nur einmal.

Lies je nach Phase zusätzlich:
- `lehren.md` – falsche Annahmen aus früheren Projekten, als Regeln. **Vor jeder Phase überfliegen.**
- `geruest.md` – Aufbau des Projekt-Repos (parameter.py, build.py, Prüfungen, Inventur).
- `druck.md` – FDM-Konstruktion und Bambu-A1-Praxis.
- `elektrik.md` – Strom, Masse, Klemmen, Verkabelungs-Anleitungen.
- `stil.md` – Look und Flair (Farben, Gravur, Schriften, Oberflächen).
- `rueckschau.md` – wie Lehren am Projektende in diesen Skill zurückfließen.

## Grundsätze

1. **Kernfunktion zuerst.** Früh festlegen, was das Projekt „geschafft“ macht (bei DragonFist der
   Sensorkäfig). Alles andere ist Bonus und wartet.
2. **Eine Quelle für jedes Maß.** Alle Maße stehen in `parameter.py`. Ungeprüfte Werte tragen
   `# MESSEN`. Nichts wird an zwei Stellen gepflegt.
3. **Alles wird erzeugt.** STLs, Bericht, Einkaufsliste, Verkabelungsplan, Prüfdruck-Anleitung,
   Blender-/Browser-Ansichten kommen aus einem `build.py`. Nach jeder Änderung neu bauen, dann
   sind alle Ansichten gleichzeitig aktuell.
4. **Der Rechner prüft, nicht das Auge.** Kollisionen, Kabelwege, Klemmen-Einlässe,
   Druckbett-Größe, Filamentbedarf und physikalische Grenzen (z. B. Übersprechwinkel) als
   Prüfungen in den Build. Ein `!!` im Bericht blockiert den Druck.
5. **Messen schlägt Datenblatt.** Kaufteile mit dem Messschieber messen, bevor die Geometrie
   eingefroren wird. Einheit immer mitnennen lassen.
6. **Klein testen, dann groß drucken.** Prüfstücke werden aus den echten Teilen
   *herausgeschnitten*, nicht nachgebaut. Ein Prüfstück testet genau eine Frage.
7. **Erst außerhalb, dann einbauen.** Elektrik zuerst simulieren (Wokwi), dann auf dem Tisch
   mit wenigen Teilen, dann komplett außerhalb des Gehäuses, erst dann verschrauben.
8. **Lösbar bauen.** Ans Gehäuse wird geschraubt, nicht geklebt. Geklebt werden nur Druckteile
   untereinander (Schwalbenschwanz-Fugen).

## Phasen

### 1. Idee und Rahmen
- Zweck, Nutzer (Kinder? Erwachsene?), Ort, Termin, Budget klären. Bewegungsablauf und
  Missbrauch mitdenken (bei DragonFist: Fuchteln statt Schlagen → Abstand der Ebenen).
- Kostentreiber sofort beziffern, inkl. Versand, Zoll und Einfuhrumsatzsteuer. Teure Bauteile
  zuerst auf Menge optimieren (weniger Sensoren durch klügeres Raster).
- Was selbst gebaut werden kann (Holzkiste), wird nicht gedruckt. Gedruckt wird nur, was
  Präzision braucht.
- Grober Bauplan mit Reihenfolge, z. B.: Software mit Simulator, solange Teile unterwegs sind →
  Gehäuse, sobald der Drucker da ist → Bonusteile zuletzt.

### 2. Einkauf und Inventur
- Links nur zu Herstellern oder seriösen Händlern, keine Marktplatz-Dubletten.
- Bestellstand in einer privaten `bestellt.json` (Shop, Datum, Inhalt, Preis, Status, Haken).
  Die Einkaufsliste wird daraus erzeugt und hakt automatisch ab.
- Beim Eintreffen: **Artikelnummer gegen Bestellung prüfen** (Wago 221-412 statt -415 kam vor)
  und die Inventur aktualisieren.
- Passung zwischen Kaufteilen vor dem Kauf prüfen (Stativ-Ø gegen Flansch-Ø).
- Private Daten (Bestellnummern, Adressen, IPs) nie ins öffentliche Repo: gitignore.

### 3. Messen
- Eine erzeugte `Messliste.md` mit Tabelle „im Modell / gemessen“, sortiert nach Dringlichkeit.
- Werte mit Einheit erfragen; bei Ungereimtheiten (Zoll? Kragen statt Körper?) nachfragen statt
  raten. Gehäusemaße nach dem Zusammenbau nachmessen und übernehmen.

### 4. CAD
- build123d, Python-Umgebung unter einem kurzen Pfad (OpenCascade mag keine langen
  Windows-Pfade). Aufbau siehe `geruest.md`.
- Kabel realistisch modellieren: Adern mit echten Wegen, nicht durch Strahlen, Griffbereiche
  oder ineinander. Kabellängen prüfen (Reserve ≥ 30 mm).
- Ansichten für den Menschen: Blender-Collections pro Baustufe, Browser-Viewer, 2D-Bohrpläne
  mit Maßen. Der Nutzer will jede Ebene verstehen, nicht nur das Ergebnis sehen.
- Vor größeren Umbauten committen (oder Backup), damit die funktionierende Version bleibt.

### 5. Prüfdruck
- Prüfstücke in Phasen ordnen, je Stück eine Prüffrage und die erwarteten Antworten
  (zu eng / passt / zu locker). Anleitung `Pruefdruck.md` wird erzeugt.
- Passungen als **Reihe** in einem Druck (z. B. 3 Öffnungen 9,9 / 10,0 / 10,1), nicht
  nacheinander.
- Ergebnisse direkt in `parameter.py`, neu bauen, nur das Betroffene nachdrucken.

### 6. Produktion
- Druckplan pro Platte: Datei, Anzahl, Farbe, Pausen, erwartete Gramm und Zeit.
- Filament-Stand mitführen: gedruckt + geplant gegen Rollen. Gramm-Schätzung gegen den Slicer
  eichen, 25 % Reserve für Fehldrucke.
- Jedes fertige Teil sofort gegen sein Gegenstück probieren, bevor das nächste gedruckt wird.

### 7. Verkabeln und Inbetriebnahme
- Siehe `elektrik.md`. Pro Ader eine Zeile: von → nach, Farbe, Klemme. Brücken genau nach Plan.
- Probelauf außerhalb des Gehäuses, mit Live-Monitor und Run-Log, dann einbauen.

### 8. Software
- Läuft früh mit Simulator (Tasten statt Sensoren), damit sie nicht auf Hardware wartet.
- Logging pro Lauf, damit der Agent hinterher auswerten kann. Tests für Erkennung,
  Parser und Performance-Budgets.
- Öffentliche Repos: nur eigene Sounds, Schriften mit freier Lizenz (OFL), keine Spiel-Assets.

### 9. Rückschau
- An Meilensteinen und am Ende: `rueckschau.md` durchgehen und Lehren in diesen Skill tragen.

## Zusammenarbeit mit dem Nutzer

- Anleitungen Schritt für Schritt, nummeriert, mit genauen Dateinamen und Einstellungen.
- Bei Fotos: erst beschreiben, was zu sehen ist, dann die Ursache, dann die kleinste Änderung.
- Nur committen und pushen, wenn der Nutzer es sagt. Drucken, Bestellen, Mails: nur der Nutzer
  bzw. nach Freigabe.
- In öffentlichen Repos: keine KI-Attribution, wenige Kommentare, schlanker Code.
