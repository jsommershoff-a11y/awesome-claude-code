# Skill-System lokal übernehmen (z.B. ins Donna-System)

Das komplette Skill-System liegt in diesem Ordner (`.claude/`). Zwei Varianten der Übernahme:

## Variante 1: Global für alle Projekte (empfohlen)

Auf deinem Rechner im Terminal:

```bash
# Repo holen (falls noch nicht vorhanden)
git clone https://github.com/jsommershoff-a11y/awesome-claude-code.git
cd awesome-claude-code
git checkout claude/skills-review-gaps-n29raq

# Skills global installieren
mkdir -p ~/.claude/skills
cp -r .claude/skills/* ~/.claude/skills/

# Aktivierungs-Regel global übernehmen:
# Inhalt von CLAUDE.md (Abschnitt "Skill-System") an ~/.claude/CLAUDE.md anhängen
cat CLAUDE.md >> ~/.claude/CLAUDE.md
```

Danach stehen `/skill-creator` und `/perfect-prompt` in **jeder** Claude-Code-Sitzung auf deinem Rechner zur Verfügung.

## Variante 2: Nur in einem Projekt (z.B. Donna)

```bash
cp -r .claude/skills <dein-projekt>/.claude/
cat CLAUDE.md >> <dein-projekt>/CLAUDE.md   # Abschnitt "Repo-Kontext" danach entfernen
```

## Nach der Installation: Donna-Skills eintragen

Die Registry (`skills/SKILLS_REGISTRY.md`) hat in **Sektion C** einen Platzhalter für deine internen Skills. Zum Befüllen in einer lokalen Claude-Code-Sitzung (im Donna-Ordner) sagen:

> "Nutze /skill-creator und trage alle Skills aus diesem Projekt in die Registry ein."

**Wichtig (intern bleiben!)**: Die ausgefüllte Sektion C mit Donna-Interna nur in der lokalen Kopie pflegen — nicht zurück in ein öffentliches Repo pushen. Am einfachsten: Registry-Änderungen lokal in `~/.claude/skills/SKILLS_REGISTRY.md` machen, das liegt außerhalb jedes Git-Repos.

## Erste Schritte danach

1. `claude` in einem beliebigen Projekt starten
2. `/perfect-prompt` mit einer echten Aufgabe testen — er fragt fehlende Infos ab und baut den Arbeitsauftrag
3. Ersten eigenen Skill anlegen: "Nutze /skill-creator, ich möchte einen Skill für <wiederkehrende Aufgabe>"
