# CLAUDE.md

## Skill-System: Aktivierung vor jeder Aufgabe

Dieses Repo enthält unter `.claude/skills/` ein Meta-Skill-System (Registry, `skill-creator`, `perfect-prompt`). Es gilt folgende Arbeitsregel:

1. **Vor jeder substanziellen Aufgabe** (mehrschrittig, mehrdeutig oder mit unklarem Zielbild): Lies `.claude/skills/SKILLS_REGISTRY.md` und aktiviere die Skills, deren Trigger zum Auftrag passen. Nenne dem Nutzer kurz, welche Skills du aktivierst und warum.
2. **Bei vagen oder unterspezifizierten Aufträgen**: Wende zuerst den Skill `perfect-prompt` an — kläre fehlende Informationen durch gebündelte Fragen und lege den Arbeitsauftrag fest, bevor die Arbeit beginnt.
3. **Bei trivialen Aufgaben** (eindeutig, ein Schritt): Direkt arbeiten, kein Registry-Ritual.
4. **Wenn ein Bedarf wiederkehrt** und kein Skill ihn abdeckt: Schlage `/skill-creator` vor, um einen neuen Skill anzulegen. Neue Skills werden immer in die Registry eingetragen.
5. **Qualitätsschluss**: Jede substanzielle Aufgabe endet mit einer Selbstprüfung gegen die vereinbarten Qualitätskriterien (bei `perfect-prompt`-Aufträgen: gegen den Arbeitsauftrags-Block).

## Repo-Kontext

Dies ist ein Fork von awesome-claude-code — einer kuratierten Ressourcen-Liste für Claude Code. Die Liste selbst wird über `THE_RESOURCES_TABLE.csv` + `make generate` gepflegt (Details: `docs/HOW_IT_WORKS.md`). README-Dateien nicht von Hand editieren, sie werden generiert.
