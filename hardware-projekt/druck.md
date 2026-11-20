# 3D-Druck (FDM, Bambu Lab A1)

## Drucker

- Bauraum 256 × 256 × 256 mm. Größere Teile teilen (Schwalbenschwanz, verkleben).
- Kein AMS: Farbwechsel per Pause. Die Pause greift **vor** der gewählten Schicht; für eine
  Gravur von 0,8 mm Tiefe also bei 1,0 mm pausieren.
- Textured PEI Plate. Rechner kann aus, sobald der Druck gestartet ist.
- Zeitraffer erzwingt eine Pause pro Schicht und die Kamera ist schwach: für Produktion aus.

## Standard-Einstellungen

| Was | Wert |
|---|---|
| Profil | 0.20mm Standard @BBL A1 |
| Wandlinien | 3 |
| Füllung | 20 % |
| Stützen | keine (Teile so konstruieren) |
| Material | PLA, 1,75 mm; IR-dichte Teile schwarz |

## Konstruktionsregeln

- **Druckbare Decken:** Überbrückte Decken über Taschen bekommen gestufte Löcher: Schlitz,
  dann Quadrat, dann rund. Deckenhöhe auf ganze Schichten runden.
- **Drucklage zuerst denken:** Sichtfläche aufs Bett (Deckel kopfüber), Türmchen nach oben,
  keine Überhänge über 45°.
- **Passungen:** Schiebesitz ca. +0,1 mm, Halbzeug gemessen +0,05–0,1 mm, Schwalbenschwanz mit
  eigenem Spiel-Parameter. Immer per Prüfstück-Reihe bestätigen.
- **Schrauben ins Druckteil:** Holzschrauben 2,5 mm in 2,2-mm-Löcher schneiden selbst Gewinde.
- **Kleine Löcher** unter 3 mm werden unsauber; optische Kanäle lieber an die Grenze legen.
- **Gravur:** 0,8 mm tief, Teil kopfüber, Farbwechsel per Pause. Ergibt saubere Zweifarbigkeit.
- **Hitze:** PLA wird ab ca. 50–60 °C weich. Wärmequellen (Netzteile, Spannungsregler) prüfen;
  ein Pico bleibt deutlich darunter.

## Ablauf pro Druck

1. Datei laden, Teileliste und Höhe prüfen.
2. Einstellungen wie oben, Pausen setzen.
3. Slicen, Gramm und Zeit notieren, mit der Schätzung vergleichen.
4. Nach dem Druck: sofort gegen Gegenstück probieren, Ergebnis zurückmelden.
