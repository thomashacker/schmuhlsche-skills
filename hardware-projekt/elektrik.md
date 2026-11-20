# Elektrik

## Stromversorgung

- Steuerrechner (Pico) über USB versorgen; VBUS/VSYS nicht mit dem Netzteil verbinden.
- Verbraucher (Sensoren, LEDs) am eigenen 5-V-Netzteil.
- **Gemeinsame Masse:** GND des Pico an die GND-Schiene des Netzteils. Ohne das gibt es keine
  gültigen Signale.
- Elko (z. B. 1000 µF / 16 V) am Netzteil-Eingang, Polung beachten (Streifen = −).
- LED-Streifen: 330 Ω in die Datenleitung, Helligkeit in der Firmware begrenzen und den Strom
  gegen das Netzteil rechnen. Pegelwandler (74AHCT125) nur bei Flackern.
- Open-Collector-Empfänger brauchen einen Pull-up; der interne des Pico reicht.

## Klemmen

- Wago 221: Hebel auf, Ader 11 mm abisolieren, rein, Hebel zu.
- Mehrere Wagos zu einer Schiene: Brücken aus kurzen Aderstücken, jede kostet 2 Einlässe.
- Einlässe pro Schiene im Build zählen, Reserve von mind. 1 pro Schiene einplanen.

## Testen

1. Simulation (Wokwi) mit derselben Pinbelegung.
2. Polung und Spannung am Netzteil mit dem Multimeter prüfen (5 V Netzteil zeigte 5,15 V: ok).
3. Ein Sensor, dann eine Linie, dann alles, jeweils mit Live-Monitor.
4. Gesamte Schaltung außerhalb des Gehäuses, Run-Log mitschreiben.
5. Erst dann einbauen.

## Anleitungen für den Nutzer

- Pro Ader: von → nach, Farbe, Klemme. Brücken explizit.
- Draufsicht als SVG mit allen Adern im Maßstab, gleiche Wege wie im 3D-Modell.
- Begriffe kurz erklären (VBUS, GND, Elko), wenn sie zum ersten Mal vorkommen.
