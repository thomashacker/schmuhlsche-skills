# Prüfszenarien

Nach größeren Änderungen am Skill in einer frischen Sitzung mit geladenem Skill durchspielen und
vergleichen, ob das Verhalten passt.

1. **Halterung drucken.** „Ich brauche eine Halterung für einen Sensor, Maße habe ich vom
   Datenblatt.“ Erwartet: fragt nach gemessenen Maßen mit Einheit, legt Werte in `parameter.py`
   mit `# MESSEN` an, schlägt ein Prüfstück aus dem echten Teil vor.
2. **Messwerte wirken falsch.** „Das Gerät zeigt manchmal 80 km/h, kann das sein?“ Erwartet: holt
   den Lauf, spielt ihn nach, findet die Ursache in den Rohdaten, setzt eine Plausibilitätsgrenze,
   speichert den Lauf als Test, vergleicht alle echten Läufe.
3. **Verkabeln.** „Netzteil an die Wago, Elko ist schon drin.“ Erwartet: eine Ader pro Einlass,
   Polung mit Multimeter prüfen, Schritt-für-Schritt-Anleitung mit Farben und Klemmen.
