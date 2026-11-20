# Lehren

Jede Lehre: was passiert ist, die Regel, warum. Neue Einträge oben in ihrer Gruppe.
Herkunft in Klammern.

## Messen und Annahmen

- **Datenblatt-Maße sind Annahmen.** Sensorgehäuse laut Datenblatt 8 mm hoch, gemessen 9 mm;
  die Sensoren standen 1 mm über. Regel: Jedes Kaufteil, in das etwas passen muss, vor dem
  Prüfdruck messen und in `parameter.py` als gemessen markieren. (DragonFist)
- **Einheit und Bezugspunkt erfragen.** „4,1 inches“ meinte cm, „0,8 cm Durchmesser“ war der
  Kragen, nicht die LED. Regel: Bei jedem Wert, der vom Modell um mehr als 10 % abweicht,
  nachfragen, was genau gemessen wurde. (DragonFist)
- **Rohre und Profile haben Toleranz.** Alu-Vierkant „10 mm“ war 9,9 mm. Regel: Passungen für
  Halbzeuge immer mit gemessenem Wert plus 0,05–0,1 mm Spiel. (DragonFist)
- **Gehäuse nach dem Bau neu messen.** Die Holzkiste wich in Höhe und Innenmaß leicht ab. Regel:
  Nach dem Zusammenbau Innenmaße messen und ins Modell übernehmen, bevor Einbauteile gedruckt
  werden. (DragonFist)

## Einkauf

- **Versand und Zoll mitrechnen.** Sensoren aus den USA: 80 $ Ware, aber 156 $ mit Express und
  Einfuhrumsatzsteuer. Regel: Gesamtpreis bis zur Haustür nennen, bevor bestellt wird. (DragonFist)
- **Gelieferte Artikelnummer prüfen.** Wago 221-412 kam statt 221-415. Regel: Beim Auspacken
  Nummer gegen Bestellung abgleichen, Modell bei Bedarf anpassen. (DragonFist)
- **Passungen zwischen Kaufteilen vorab prüfen.** Flansch passte nicht aufs Stativ (Ø 40 gegen
  Ø 35), musste aufgesägt werden. Regel: Bei zusammengehörenden Kaufteilen beide Maße aus den
  Datenblättern vergleichen. (DragonFist)
- **Speicherkarten zuerst prüfen.** Zwei alte microSD-Karten waren defekt und kosteten einen
  Abend Fehlersuche am Jetson. Regel: Bei Einplatinenrechnern neue A2-Karte verwenden oder die
  alte vorher mit einem Lese-/Schreibtest prüfen. (DragonFist)

## 3D-Druck

- **Runde Löcher in einer frei überbrückten Decke werden zu Gewölle.** Die Taschendecke über
  den Sensoren hatte runde Lochwände in der Luft; das Schraubloch war zu. Regel: Gestufte Löcher
  (1. Schicht Schlitz quer, 2. Schicht Quadrat, darüber rund) und Deckenhöhe auf das
  Schichtraster legen. (DragonFist)
- **Lichtlöcher nicht unter ~3 mm.** 2,9 mm war das Maximum wegen des Übersprechwinkels; kleiner
  wird unsauber. Regel: Optische Kanäle früh mit Prüfstück testen und gegen die Geometrie-Grenze
  rechnen. (DragonFist)
- **Gramm-Schätzung war zu niedrig.** Volumen × 20 % Füllung unterschätzt, weil die Außenhaut
  voll gedruckt wird. Regel: Außenhaut (Fläche × 0,9 mm) voll, Inneres mit Füllgrad, gegen den
  Slicer eichen, 25 % Reserve. (DragonFist)
- **Vor dem Druck die Platte im Slicer ansehen.** Zwei Prüfteile lagen versehentlich mit auf der
  Platte (40 mm statt 33 mm Höhe). Regel: Teileliste und Gesamthöhe vor „Drucken“ kontrollieren.
  (DragonFist)
- **Prüfstück so klein wie die Frage.** Ein ganzer Testblock mit drei Taschen, wo eine reicht,
  kostet Zeit und Filament. (DragonFist)
- **Veraltete Dateien umbenennen.** Zwei gleichnamige Prüfdateien verwirrten. Regel: Alte Stände
  mit Präfix `ALT_` und Datum, Ausgabeordner vor jedem Build leeren. (DragonFist)

## CAD und Modell

- **Kabel nicht als Dekoration.** Erste Kabel liefen durch den Schlagbereich und ineinander.
  Regel: Adern mit echten Wegen routen, Kollisionen prüfen lassen, Kabellängen prüfen.
  (DragonFist)
- **Klemmen-Einlässe zählen inklusive Brücken.** Eine Wago 221-415 hat 5 Einlässe, aber jede
  Brücke zur nächsten Wago kostet 2. Regel: Einlässe pro Schiene im Build zählen. (DragonFist)

## Elektrik

- **Breadboards brauchen eine gemeinsame Masse.** Linie B lief nicht, bis GND zwischen beiden
  Breadboards verbunden war. Regel: Jede Teilschaltung bekommt GND zur gemeinsamen Schiene, auch
  wenn sie eigenen Strom hat. (DragonFist)
- **Wackelkontakte zuerst verdächtigen.** Ein Sensor zeigte dauerhaft Signal; nach Umstecken lief
  er. Regel: Bei Einzelausfällen erst Stecker prüfen, dann Code. (DragonFist)

## Zusammenarbeit

- **Backup vor Experimenten.** Der Nutzer wollte Änderungen ausprobieren, ohne die gute Version
  zu verlieren. Regel: Vor größeren Umbauten committen. (DragonFist)
- **Optik früh zeigen.** Der Nutzer entscheidet viel über Bilder (Blender, Viewer, 2D-Pläne).
  Regel: Nach jeder größeren Änderung ein Bild oder eine Ansicht schicken. (DragonFist)
- **Zuständigkeit klären, bevor man etwas behauptet.** „Ich habe Blender geschlossen“ war falsch,
  der Nutzer hatte es geschlossen. Regel: Nur berichten, was man selbst getan oder geprüft hat.
  (DragonFist)
