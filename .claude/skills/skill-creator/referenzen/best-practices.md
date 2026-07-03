# Best Practices für Skill-Design

Destilliert aus den besten Skill-Sammlungen der awesome-claude-code-Liste (Superpowers, TÂCHES skill-auditor, Context Engineering Kit, Compound Engineering, Claude Code Infrastructure Showcase) und den offiziellen Anthropic-Konventionen.

## 1. Die description entscheidet über Leben und Tod

Claude wählt Skills anhand der Frontmatter-description aus — nicht anhand des Inhalts. Eine description muss drei Fragen beantworten:

| Frage | Beispiel |
|---|---|
| WAS tut der Skill? | "Erstellt Release-Notes aus Git-Historie" |
| WANN verwenden? | "Verwenden vor jedem Release oder wenn ein Changelog gebraucht wird" |
| Welche TRIGGER? | "Trigger: 'Release Notes', 'Changelog', 'was hat sich geändert'" |

**Anti-Pattern**: `description: Hilft bei Releases.` — zu vage, wird nie zuverlässig aktiviert.

## 2. Progressive Disclosure — Kontext ist teuer

Das SKILL.md wird bei Aktivierung komplett in den Kontext geladen. Deshalb:

- SKILL.md = nur der Ablauf (Ziel: < 150 Zeilen)
- Detailwissen, Tabellen, lange Beispiele → `referenzen/*.md`, mit explizitem Verweis "lies X bevor du Y tust"
- Deterministische Arbeit (Parsen, Formatieren, Validieren) → `skripte/` als ausführbare Dateien, statt sie vom Modell erledigen zu lassen

Faustregel aus dem Context Engineering Kit: Jede Zeile, die nicht in JEDEM Durchlauf gebraucht wird, gehört ausgelagert.

## 3. Ablauf statt Absichtserklärung

Gut (Superpowers-Stil):
```
1. Führe `git log --oneline -20` aus
2. Gruppiere Commits nach: Features, Fixes, Breaking Changes
3. Frage den Nutzer, welche Version (major/minor/patch)
```

Schlecht:
```
Analysiere die Git-Historie sorgfältig und erstelle hochwertige Release-Notes.
```

Konkrete Befehle, nummerierte Schritte, explizite Entscheidungspunkte. Wenn ein Schritt eine Nutzer-Entscheidung braucht, steht da "frage den Nutzer" — nicht "berücksichtige die Präferenzen".

## 4. Abgrenzung explizit machen

Jeder Skill sollte benennen, was er NICHT tut, und wohin stattdessen verwiesen wird. Das verhindert, dass sich Skills gegenseitig kannibalisieren (Muster aus TÂCHES skill-auditor).

## 5. Checklisten für Qualitätssicherung

Skills, die etwas produzieren (Code, Dokumente, Konfiguration), enden mit einer Abschluss-Checkliste. Das erzwingt Selbstprüfung statt "fertig und weg" (Muster aus Compound Engineering: Fehler von heute = Checklisten-Eintrag von morgen).

## 6. Ein Skill = ein Problem

Wenn die Beschreibung ein "und" braucht ("erstellt Releases UND managt Issues"), sind es zwei Skills. Große Workflows werden als Skill-Familie gebaut, bei der ein Orchestrator-Skill auf Teil-Skills verweist (Muster: Book Factory, Fullstack Dev Skills).

## 7. Namenskonventionen

- Kleinbuchstaben, Bindestriche: `release-notes`, `db-migration-check`
- Verb-orientiert wenn Aktion: `create-`, `check-`, `sync-`
- Domänen-klar wenn Wissensgebiet: `postgres-tuning`, `gdpr-basics`
- Keine generischen Namen (`helper`, `utils`, `tools`) — sie sagen der Auswahl-Logik nichts

## 8. Testen wie Software

Vor dem Abschluss: 3–5 realistische Nutzer-Prompts formulieren und prüfen:
1. Würde die description bei diesem Prompt matchen?
2. Führt der Ablauf ohne Rückfragen ins richtige Ergebnis — oder fragt er an den richtigen Stellen nach?
3. Was passiert bei fehlenden Eingaben? (Der Skill muss den Fall benennen)
