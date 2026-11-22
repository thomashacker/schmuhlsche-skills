# Rückschau

An jedem Meilenstein (Prüfdruck fertig, Gehäuse steht, Inbetriebnahme, Projektende) kurz
durchgehen. Am Projektende gründlich.

## Fragen

1. Welche Annahme war falsch? Wann hätten wir es merken können?
2. Was mussten wir doppelt drucken, kaufen oder machen?
3. Welche Prüfung im Build hätte den Fehler gefunden?
4. Was hat überraschend gut funktioniert und sollte Standard werden?
5. Was sah gut aus, was nicht? (für `stil.md`)
6. Wo hat der Nutzer nachfragen oder korrigieren müssen?

Als Checkliste kopieren:

```
Rückschau:
- [ ] Fragen 1–6 beantwortet
- [ ] Neue Lehren in lehren.md (was, Regel, warum, Herkunft)
- [ ] Stabile Lehren nach SKILL.md oder in die passende Nebendatei befördert
- [ ] Code-Audit aus software.md am Projekt-Repo durchgeführt
- [ ] Keine privaten Daten im Skill
- [ ] Commit und Push des Skill-Repos
```

## Einarbeiten

- Neue Lehre in `lehren.md`: was passiert ist, Regel, warum, Herkunft.
- Wird eine Lehre zur festen Arbeitsweise: in `SKILL.md` (Grundsätze oder Phase) aufnehmen und
  in `lehren.md` kürzen.
- Wiederverwendbarer Code (Funktionen, Prüfungen) wandert nach `geruest.md` bzw. später in eine
  eigene Bibliothek.
- `SKILL.md` kurz halten (unter 500 Zeilen): Details gehören in die Nebendateien, jede direkt von
  `SKILL.md` verlinkt, nie Datei → Datei → Datei. Nebendateien über 100 Zeilen bekommen oben ein
  Inhaltsverzeichnis.
- Nur aufschreiben, was Claude nicht ohnehin weiß. Ein Begriff pro Sache, keine Datumsbedingungen.
- Beschreibung im Frontmatter: was der Skill tut und wann er greift, mit den Wörtern, die der
  Nutzer benutzt (max. 1024 Zeichen).
- Keine privaten Daten (Adressen, Bestellnummern, IPs, Mails).
- Commit pro Rückschau: `rueckschau <projekt>: <kurz>`.
