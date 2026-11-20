# schmuhlsche skills

Claude-Code-Skills aus eigenen Projekten. Jeder Skill wächst mit jedem Projekt.

| Skill | Wofür |
|---|---|
| [hardware-projekt](hardware-projekt/SKILL.md) | Maker-Projekte mit 3D-Druck, build123d-CAD, Elektronik und Einkauf |

## Einbinden

Ordner nach `~/.claude/skills/` verlinken, z. B. unter Windows:

```powershell
New-Item -ItemType Junction -Path "$env:USERPROFILE\.claude\skills\hardware-projekt" -Target "$PWD\hardware-projekt"
```

## Pflege

Nach jedem Projekt eine Rückschau nach [hardware-projekt/rueckschau.md](hardware-projekt/rueckschau.md).
