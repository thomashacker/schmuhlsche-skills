# Software, Firmware und Wartung

Für App, Mikrocontroller-Firmware und Sensor-Logik. Ziel: Was der Nutzer am Gerät erlebt, lässt
sich aus Logs exakt nachspielen, und jeder Fehler wird ein Test.

## Daten zuerst

- **Rohdaten mit Ankunftszeit loggen**, nicht nur Ergebnisse: jede Zeile vom Mikrocontroller
  (`raw.log`), dazu Zusammenfassung, Ereignisse, Gesundheitswerte (Spannung, Temperatur,
  Scanrate). Ein Ordner pro Lauf.
- **Replay-Werkzeug**: spielt `raw.log` durch exakt dieselbe Logik, mit denselben Frame-Ticks wie
  live. Live und Replay müssen dasselbe Ergebnis liefern, sonst ist das Replay wertlos.
- **Unabhängige Kontrolle**: eine zweite, einfache Zählung aus den Rohdaten (z. B. Eintritte in
  die hintere Ebene) zeigt, ob die Hauptlogik zu viel oder zu wenig zählt.
- **Wahrheit vom Menschen**: ein Aufnahme-Modus, in dem der Nutzer selbst mitzählt und das
  Ergebnis ins Log schreibt. Ohne diese Grundwahrheit nur gegen die Kontrolle optimieren.
- Bei „ich glaube, der zählt falsch“: erst den Lauf holen und beziffern (alt / neu / Kontrolle),
  dann ändern.

## Sensor-Logik

- Physikalisch denken: Was kann ein Körper zwischen zwei Abtastungen tun? Benachbarte Sensoren
  gehören meist zum selben Objekt; ein Arm kann seitlich rutschen, ohne neu anzufangen.
- **Plausibilitätsgrenzen** für jede Messgröße (Faust ≤ 40 km/h auf 20 cm). Lieber kein Wert als
  ein falscher; das Ereignis zählt trotzdem.
- Ergebnisfelder, die fehlen dürfen (`None`), in **jedem** Verbraucher abfangen: Anzeige, Log,
  Statistik, Highscore. Ein einziger ungeschützter Verbraucher hat die App abstürzen lassen.
- Jede Regeländerung gegen **alle** gespeicherten echten Läufe prüfen: Zählung, Anteil mit
  Messwert, Median, Ausreißer. Eine Regel, die 40 % der Messwerte wegwirft, ist zu grob.

## Kommunikation mit dem Mikrocontroller

- `readline()` mit Timeout liefert halbe Zeilen: puffern, bis `\n` da ist.
- Zeilenprotokoll mit Kennbuchstaben (`E`, `S`, `H`, `I`), kaputte Zeilen zählen statt abstürzen.
- Watchdog und Wiederverbindung: Port neu öffnen, stillen Controller anstoßen.
- Firmware fällt ohne Befehle nach ein paar Sekunden in einen sicheren Eigenmodus zurück
  (z. B. LEDs auf Automatik), damit ein App-Absturz das Gerät nicht einfriert.

## Robustheit am Einsatzort

- Dauerhafte Dateien (Einstellungen, Highscores) **atomar** schreiben: erst `.tmp`, dann
  `os.replace`. Ein Stromausfall darf nie eine halbe Datei hinterlassen.
- Zustand sichtbar machen: Version, Verbindung zum Controller, WLAN/Internet auf dem Startbildschirm.
- Rückmeldung pro Phase (LED-Farbe und Ton je Zustand) hilft Nutzer und Entwickler beim Testen.
- **Dauertest**: das Gerät eine Stunde laufen lassen, danach prüfen: Dienst ohne Neustart,
  Datenlücken, kaputte Zeilen, Spannungsbereich, Temperatur, Speicher, Plattenplatz.

## Tests

- Den **niedrigsten** Test behalten, der den Fehler noch fängt (Logik-Test vor App-Test).
- Jeder Fehler aus echten Daten wird ein Replay-Test mit dem echten (kleinen) `raw.log` und
  Grenzen (z. B. 104–112 Treffer, Höchstwert ≤ 40 km/h).
- Ein neuer Test muss **ohne den Fix fehlschlagen**. Einmal gegenprüfen.
- Gleiche Fälle parametrisieren oder in einer Schleife bündeln; triviale Ein-Zeilen-Prüfungen an
  bestehende Tests hängen. Löschen nur, wenn ein anderer Test dasselbe Verhalten abdeckt.
- Langsame Tests messen (`pytest --durations=12`) und die Ursache beheben, statt Tests zu streichen.
  Beispiel: `pygame.SCALED` unter dem Dummy-Videotreiber kostete 0,5 s pro Test.
- Performance-Budgets als Tests (Durchsatz des Parsers, Frame-Zeit).

## Code-Audit

Bei Meilensteinen und vor dem Einsatz durchgehen, als Checkliste kopieren:

```
Audit:
- [ ] Design: Gibt es Code, der mehr kann als nötig, oder Doppeltes?
- [ ] Robustheit: Eingaben vom Controller, Dateien, Netz; was passiert bei Müll, Abbruch, Stromausfall?
- [ ] Optionale Werte: Wird jedes None überall abgefangen?
- [ ] Threads: Gemeinsamer Zustand nur unter Lock oder über threadsichere Queues?
- [ ] Performance: Frame-Zeit und CPU auf dem Zielgerät, langsamste Tests
- [ ] Tests: redundante zusammenlegen, Lücken mit dem niedrigsten Test schließen
- [ ] Jede Änderung: Tests grün, Replay aller echten Läufe unverändert oder besser
```

## Release

- Ein kleiner PR pro Änderung: `VERSION` und `CHANGELOG.md` mitziehen, mergen, aufs Gerät deployen.
- Nach dem Deploy auf dem Gerät prüfen: Dienst aktiv, Version, neuer Lauf schreibt Logs, Daten
  (Highscores, Einstellungen) noch da.
- Unter Windows mit CRLF-Dateien: Ersetzungen per `sed`/Heredoc schlagen leise fehl oder
  zerstören `\n`. Gezielte Edits mit dem Edit-Werkzeug, danach `git diff` ansehen.
