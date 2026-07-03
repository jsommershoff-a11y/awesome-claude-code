# Vorlage für neue Skills

Diese Vorlage 1:1 kopieren nach `.claude/skills/<skill-name>/SKILL.md` und alle `<...>`-Platzhalter ersetzen. Abschnitte, die nicht gebraucht werden, ersatzlos streichen.

```markdown
---
name: <skill-name-klein-mit-bindestrichen>
description: <WAS der Skill tut, 1 Satz>. Verwenden, wenn <WANN/Situation>. Trigger: "<Formulierung 1>", "<Formulierung 2>", "<Formulierung 3>".
---

# <Skill-Titel>

<1–2 Sätze: Rolle und Ziel des Skills. Was ist am Ende fertig?>

## Voraussetzungen

<Was muss vorhanden sein: Dateien, Zugänge, Kontext. Was tun, wenn etwas fehlt — z.B. "frage den Nutzer nach X". Abschnitt streichen, wenn keine.>

## Ablauf

### Schritt 1: <Verb + Objekt>

<Konkrete Anweisung. Bei Shell-Arbeit: der exakte Befehl. Bei Entscheidungen: die Kriterien.>

### Schritt 2: <Verb + Objekt>

<...>

### Schritt 3: Ergebnis prüfen und übergeben

<Wie sieht das fertige Ergebnis aus? In welcher Form wird es übergeben (Datei, Chat-Antwort, PR)?>

## Grenzen

- Dieser Skill macht NICHT: <...>
- Dafür stattdessen: <anderer Skill / manueller Weg>

## Abschluss-Checkliste

- [ ] <Prüfpunkt 1>
- [ ] <Prüfpunkt 2>
- [ ] Registry-Eintrag in `.claude/skills/SKILLS_REGISTRY.md` aktuell
```

## Hinweise zum Ausfüllen

- **description**: Wichtigste Zeile des Skills — siehe `best-practices.md` Abschnitt 1. Im Zweifel mehr Trigger-Formulierungen aufnehmen.
- **Schritte**: So schreiben, dass jemand ohne Vorwissen sie ausführen könnte. Jeder Schritt beginnt mit einem Verb.
- **Referenzen**: Wird ein Abschnitt länger als ~30 Zeilen, in `referenzen/<thema>.md` auslagern und im Ablauf verweisen: "Lies zuerst `referenzen/<thema>.md`."
- **Skripte**: Wiederholbare, deterministische Arbeit in `skripte/` ablegen und im Ablauf per Befehl aufrufen.
