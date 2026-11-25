# Bauen und Montieren

Regeln für Teile, die verschraubt, eingehängt oder an ein Gehäuse gesetzt werden. Zusammengetragen
aus Design-for-Assembly-Leitfäden, Herstellerangaben für Schrauben in Kunststoff und Holz und
eigenen Funden. Zahlen sind Startwerte: per Prüfstück auf dem eigenen Drucker bestätigen.

## Inhalt
- Montage zuerst denken
- Schrauben in Druckteile
- Schrauben in Holz
- Druckgerechte Form
- Prüfungen im Build
- Checkliste

## Montage zuerst denken

- **Reihenfolge vor Geometrie.** Für jedes Teil aufschreiben: wer setzt es wann ein, von wo wird
  geschraubt, womit (Schraubendreher-Länge, Bit). Erst dann Löcher und Dome setzen.
- **Zugang prüfen.** Ein Schraubenkopf braucht Platz für Kopf und Schrauber (Radius ca. 10 mm,
  gerade Linie nach hinten frei). Eine offene Rückseite, die an eine Wand kommt, ist nach der
  Montage zu: Einbauteile vorher einsetzen.
- **Wenige Teile.** Jedes Teil muss sich begründen (bewegt sich, anderes Material, muss zum
  Service ab). Eine Zwischenplatte ohne eigene Aufgabe streichen.
- **Normteile, wenige Sorten.** Möglichst eine Schraubengröße pro Ebene (z. B. M2,5 im Gerät,
  4 × 30 ins Holz). Nur Teile aus dem Baumarkt oder Elektronikhandel.
- **Fehlmontage unmöglich machen.** Stifte, Nasen oder asymmetrische Lochbilder zentrieren und
  geben die Lage vor. Teile, die gleich aussehen, aber verschieden sind, vermeiden.
- **Servicezugang.** Was getauscht oder verkabelt wird (Rechner, Netzteil, Stecker), muss ohne
  Zerlegen des Rests erreichbar sein.
- **Transport und Menschen.** Das Gerät wird getragen, gerüttelt und angefasst: Stecker sichern,
  keine Steckbretter, erreichbare Kanten rund oder gepolstert, Schütteltest vor dem Einsatz.
- **Last tragen, nicht nur halten.** Lange Hebel (Kästchen, das weit absteht) brauchen Auflage
  oder Abstützung, Schrauben allein auf einer Seite reichen nicht.

## Schrauben in Druckteile

| Was | Startwert |
|---|---|
| Dom-Außendurchmesser | 2–2,5 × Schrauben-Ø (4er Schraube: Dom 10 mm) |
| Vorbohrung selbstschneidend | 0,7–0,85 × Schrauben-Ø; bewährt: 2,5er Schraube in 2,2 mm, 4er in 3,2 mm |
| Einschraubtiefe | mindestens 2–2,5 × Schrauben-Ø |
| Dom zur Außenwand | nicht direkt an eine dünne Wand setzen, sonst reißt die Wand |
| Löcher | gedruckt leicht zu eng; bei Bedarf nachbohren |

- Selbstschneidende Schrauben für Verbindungen, die selten gelöst werden. Häufiges Lösen →
  Einschmelzmuttern.
- **Einschmelzmuttern:** Loch nach dem Datenblatt der Mutter, nicht nach Schraubengröße; Loch
  0,5–1,5 mm tiefer als die Mutter. Bei PLA nur ohne Wärmelast; zuletzt einsetzen.
- Gedruckte Gewinde nur bei großen Größen, sie halten deutlich weniger.

## Schrauben in Holz

- Durchgangsloch im angeschraubten Teil etwas größer als die Schraube (4er Schraube: 4,5 mm),
  damit es sich anzieht.
- Vorbohren im Nadelholz mit ca. 2,5 mm (4er Schraube), Hartholz 3 mm. Nah an Kanten immer
  vorbohren.
- **Länge:** Schraube darf nicht durchs Brett kommen. Länge ≤ Bauteil + Brettdicke − 3 mm, oder
  von innen durchs Brett ins Druckteil (Länge ≤ Brett + Domtiefe).
- Das Druckteil kann selbst die Bohrschablone sein: anhalten, durch das Domloch anbohren,
  dann auf Durchgangsmaß aufbohren.

## Druckgerechte Form

- Wände ab 3 Umfangslinien (ca. 1,35 mm bei 0,4-mm-Düse), tragende Teile 3 mm.
- Bewegliche Teile mindestens 0,3 mm Spiel, Schiebesitz ca. 0,1 mm (siehe `druck.md`).
- Sichtseite aufs Bett; unten 0,5 mm Fase gegen den Elefantenfuß.
- Dome, Stifte und Rippen wachsen senkrecht aus der Bettseite, dann brauchen sie keine Stützen.

## Prüfungen im Build

- **Schraubstellen automatisch suchen, nicht von Hand setzen.** Für jede Schraube prüfen: frei im
  Bauteil (kein Display, Rechner oder Kabelloch im Dom) und frei auf der Schrauberseite
  (Pfosten, Polster, Platten mit Kopf-Radius 10 mm). Größtes freies Rechteck nehmen, sonst `!!`.
- **Werkzeugweg:** pro Schraube den Halter (Ø 13 mm) bzw. einen langen Bit (Ø 7 mm) als Körper
  bis zum Kopf legen; was nur mit Spezialwerkzeug geht, kommt auf die Einkaufsliste.
- **Druckbarkeit:** jede STL in Drucklage auf Auflagefläche und Überhang (> 45°) prüfen.
- **Bewegung:** Gleit- und Rastwege durchspielen, nur vorgesehene Federteile dürfen schneiden.
- Bauraum (Druckbett) für jedes Teil prüfen.
- Gewicht und Schwerpunkt grob schätzen, wenn das Gerät getragen oder auf ein Stativ gesetzt wird.

## Checkliste

```
Montage:
- [ ] Reihenfolge und Schraubrichtung für jedes Teil aufgeschrieben
- [ ] Schrauber kommt an jede Schraube (Prüfung im Build)
- [ ] Schraube kommt nirgends durch (Länge gegen Brett + Dom)
- [ ] Dome: Ø, Vorbohrung, Einschraubtiefe nach Tabelle
- [ ] Teile zentrieren sich selbst (Stifte, Nasen)
- [ ] Servicezugang zu Rechner, Netzteil, Steckern
- [ ] Jedes Teil passt aufs Druckbett und druckt ohne Stützen (Prüfung im Build)
- [ ] Bewegliche Teile im Schnitt geprüft
- [ ] Erreichbare Kanten rund oder gepolstert, Stecker gesichert
```

Quellen (für Nachschlagen): Prusa Knowledge Base „Modeling with 3D printing in mind“; Hersteller-
Leitfäden zu Domen für selbstschneidende Schrauben und Einschmelzmuttern (Celo, Sovol, Formlabs);
Holzschrauben-Vorbohrtabellen (Fabory); DFA-Checklisten (Fictiv, Autodesk).
