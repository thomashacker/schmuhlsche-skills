# Lehren

Jede Lehre: was passiert ist, die Regel, warum. Neue Einträge oben in ihrer Gruppe.
Herkunft in Klammern.

## Inhalt
Messen und Annahmen · Einkauf · 3D-Druck · CAD und Modell · Elektrik · Software · Zusammenarbeit

## Messen und Annahmen

- **Selbstgebautes erst sehen, dann modellieren.** Eine Klemmen-Baugruppe wurde zweimal falsch
  verstanden (liegend statt stehend), ein Kabel mit 13 statt 4 mm angenommen. Regel: Für alles,
  was der Nutzer zusammengesteckt hat, zuerst ein Foto mit Maßstab; Lage, Öffnungsrichtung und
  Kabelwege daraus ablesen. Passmaße nie schätzen. (DragonFist)
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

- **Druckbarkeit rechnen, nicht ansehen.** Zwei Teile hätten auf der offenen Seite gestanden bzw.
  ein freies Dach gehabt. Regel: Für jede STL in Drucklage Auflagefläche und Überhang (> 45°)
  berechnen; Überhang über wenige cm² heißt Lage oder Form ändern. (DragonFist)
- **Bewegliche Teile im Schnitt prüfen.** Eine Schubladen-Rastung hätte geklemmt; sichtbar wurde
  es erst im Schnittbild. Regel: Für alles, was gleitet, rastet oder klappt, den Weg durchspielen
  und einen Schnitt zeigen. Federn muss das Teil, über das der Gegenpart gleitet. (DragonFist)
- **Verbrauchsmaterial mitdenken.** Ein Refill ohne passende Spule blockierte den Druck.
  Regel: Vor einer Druckserie Filamentmenge, Spule und Ersatzteile des Druckers prüfen. (DragonFist)
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

- **Werkzeug ist Teil der Geometrie.** Schraubenköpfe saßen tief in engen Rohren; der Bithalter
  passte nicht hinein. Regel: Pro Schraubstelle den Werkzeugweg (Halter-Ø, Bitlänge) als Körper
  prüfen; nötiges Spezialwerkzeug früh auf die Einkaufsliste. (DragonFist)
- **Erreichbare Kanten entschärfen.** Spitze Teile im Bewegungsbereich verletzten mehrere
  Spieler. Regel: Jede Kante, an die Hände kommen, rund (≥ 2 mm) oder gepolstert; Polster
  austauschbar (Kaufteil auf gedrucktem Halter). (DragonFist)
- **Neue Anbauteile gegen alles Bestehende prüfen.** Die Seitenkonsole ragte 2 cm in den schon
  geplanten Kabelkanal, weil nur gegen den Innenraum geprüft wurde. Regel: Jedes neue Teil im Build
  gegen den ganzen Rahmen schneiden (Volumen > 0 = `!!`). (DragonFist)
- **Schrauben von innen brauchen freien Innenraum.** Die Wandschrauben der Seitenkonsole saßen
  hinter Schwimmnudel, Sensorplatte und Alu-Pfosten, das Display-Kästchen hätte vorne keine
  einzige freie Stelle gehabt. Regel: Schraubstellen im Build automatisch suchen (Inhalt +
  Schrauber-Radius 10 mm), lange Kästchen vorne abstützen (Stifte zum Nachbarteil). (DragonFist)
- **Kabel nicht als Dekoration.** Erste Kabel liefen durch den Schlagbereich und ineinander.
  Regel: Adern mit echten Wegen routen, Kollisionen prüfen lassen, Kabellängen prüfen.
  (DragonFist)
- **Klemmen-Einlässe zählen inklusive Brücken.** Eine Wago 221-415 hat 5 Einlässe, aber jede
  Brücke zur nächsten Wago kostet 2. Regel: Einlässe pro Schiene im Build zählen. (DragonFist)

## Elektrik

- **Transportfest statt tischfest.** Nach einer Fahrt hatten Steckbrett und USB-Stecker
  Wackelkontakt. Regel: Im fertigen Gerät keine Steckbretter; Stecker gegen Herausrutschen
  sichern; nach dem Einbau ein Schütteltest mit Live-Monitor. (DragonFist)
- **Stecker wartbar einbauen.** Ein loser Stecker war nur durch komplettes Zerlegen erreichbar.
  Regel: Jede Steckverbindung von außen oder über eine Klappe erreichbar. (DragonFist)
- **Eine Ader pro Klemmen-Einlass.** Elko-Bein und Kabel steckten zusammen in einem Wago-Einlass;
  das hält nicht sicher. Regel: Jede Ader bekommt ihren eigenen Einlass, notfalls die 5er-Wago.
  (DragonFist)
- **Offene Klemmen schützen.** Die fertige Netzteil-Verbindung lag offen im Kabelweg. Regel: Für
  jede Wago-Verbindung eine kleine, verschraubte Druckdose mit Zugentlastung einplanen. (DragonFist)
- **Vor dem Anschließen messen.** Multimeter auf Gleichspannung, rot an +, schwarz an −: positive
  5 V heißen richtige Polung. Erst dann Verbraucher anstecken. (DragonFist)

- **Breadboards brauchen eine gemeinsame Masse.** Linie B lief nicht, bis GND zwischen beiden
  Breadboards verbunden war. Regel: Jede Teilschaltung bekommt GND zur gemeinsamen Schiene, auch
  wenn sie eigenen Strom hat. (DragonFist)
- **Wackelkontakte zuerst verdächtigen.** Ein Sensor zeigte dauerhaft Signal; nach Umstecken lief
  er. Regel: Bei Einzelausfällen erst Stecker prüfen, dann Code. (DragonFist)

## Software

- **Jeder angezeigte Wert braucht eine Gültigkeitsbedingung.** Die Höchstgeschwindigkeit war ein
  Artefakt überlappender Bewegungen. Regel: Für jede berechnete Größe festlegen, wann sie
  messbar ist; sonst „–“ statt Zahl. Mit echten Läufen belegen (Anteil gültig, Verteilung,
  Ausreißer) und als Test festschreiben. Ranglisten nur aus robusten Werten (nicht Einzelmaximum).
  (DragonFist)
- **Nur Gleiches vergleichen.** Läufe mit verschiedenen Einstellungen standen in einer Liste.
  Regel: Ranglisten je Einstellung, pro Person der beste Eintrag. (DragonFist)
- **Gerät meldet fehlende Hardware selbst.** Ein ausgefallener Lautsprecher fiel erst per SSH
  auf. Regel: Erwartete Geräte als Liste; die App zeigt, was fehlt. (DragonFist)
- **Gefühl „zählt falsch“ war richtig.** 99 statt 93 Schläge, weil ein Schlag durch zwei
  benachbarte hintere Strahlen in zwei Fäuste zerfiel. Regel: Rohdaten nachspielen, gegen eine
  unabhängige Zählung beziffern, den Lauf als Regressionstest speichern. (DragonFist)
- **82 km/h waren ein Messfehler.** Der Arm rutschte in der vorderen Ebene einen Strahl zur
  Seite; das galt als neuer Schlagbeginn kurz vor der hinteren Ebene. Regel: Plausibilitätsgrenze
  für jede Messgröße, im Zweifel ohne Wert zählen. (DragonFist)
- **Ein fehlender Wert ließ die App abstürzen.** Nach der Einführung von „Treffer ohne Tempo“
  rechnete das Run-Log noch mit der Zahl. Regel: Bei optionalen Feldern alle Verbraucher suchen
  (`grep`) und abfangen, ein Test pro Verbraucher. (DragonFist)
- **`readline()` mit Timeout liefert halbe Zeilen.** Regel: seriellen Eingang puffern, bis die
  Zeile komplett ist. (DragonFist)
- **Dateien nie direkt überschreiben.** Highscores und einmal eine Quelldatei (Skriptfehler beim
  Schreiben) gingen fast verloren. Regel: dauerhafte Dateien atomar
  schreiben (`.tmp` + `os.replace`). (DragonFist)
- **Zu grobe Korrektur.** Eine erste Regel gegen falsche Tempi hätte 40 % aller Messwerte
  gelöscht. Regel: Jede Regel gegen alle echten Läufe mit „Anteil mit Messwert“ und Median
  vergleichen, dann eingrenzen. (DragonFist)
- **Testsuite doppelt so schnell durch einen Fund.** Der skalierende Renderer kostete unter dem
  Dummy-Treiber 0,5 s pro Test. Regel: `--durations` ansehen, bevor Tests gestrichen werden.
  (DragonFist)

## Zusammenarbeit

- **Nur geprüfte Links.** Mehrere Kauf-Links führten ins Leere oder lieferten zu spät. Regel:
  Link selbst öffnen, Artikel, Größe, Preis und Lieferdatum bestätigen, dann schicken. (DragonFist)
- **Erklären deckt Fehler auf.** Beim Erklären eines Mechanismus fiel ein Konstruktionsfehler auf.
  Regel: Zu jedem neuen Mechanismus ungefragt Bild und Schnitt mit kurzer Funktionsbeschreibung.
  (DragonFist)
- **Spracheingabe deuten.** Diktierte Fachwörter kommen verfremdet an. Regel: Aus dem Kontext
  deuten und mit dem richtigen Begriff zurückspiegeln. (DragonFist)
- **Backup vor Experimenten.** Der Nutzer wollte Änderungen ausprobieren, ohne die gute Version
  zu verlieren. Regel: Vor größeren Umbauten committen. (DragonFist)
- **Optik früh zeigen.** Der Nutzer entscheidet viel über Bilder (Blender, Viewer, 2D-Pläne).
  Regel: Nach jeder größeren Änderung ein Bild oder eine Ansicht schicken. (DragonFist)
- **Zuständigkeit klären, bevor man etwas behauptet.** „Ich habe Blender geschlossen“ war falsch,
  der Nutzer hatte es geschlossen. Regel: Nur berichten, was man selbst getan oder geprüft hat.
  (DragonFist)
