# Skill-Registry

Zentrale Liste aller Skills. Wird von `perfect-prompt` (Skill-Auswahl vor Aufgabenstart) und `skill-creator` (Duplikat-Prüfung, Neueinträge) gelesen.

**Pflege-Regel**: Jeder neue Skill bekommt hier einen Eintrag (macht `/skill-creator` automatisch). Jeder Eintrag: Name, Zweck in 1 Satz, Aktivierungs-Trigger.

---

## Sektion A — Installierte Skills

### Eigene Skills (dieses Repo, `.claude/skills/`)

| Skill | Zweck | Aktivieren wenn |
|---|---|---|
| `skill-creator` | Erstellt neue Skills nach Best Practices und pflegt diese Registry | Neuer Skill gewünscht, Skill verbessern/auditieren, Registry aktualisieren |
| `perfect-prompt` | Klärt Aufgaben durch gezielte Fragen, wählt Skills, baut den Arbeitsauftrag | Start jeder größeren/unklaren Aufgabe; vage Aufträge |

### Umgebungs-Skills (in Claude-Code-Sitzungen typischerweise verfügbar)

Verfügbarkeit je Umgebung prüfen — diese Liste entspricht dem Stand der Sitzung, in der sie erstellt wurde.

| Skill | Zweck | Aktivieren wenn |
|---|---|---|
| `/code-review` | Prüft den aktuellen Diff auf Korrektheits-Bugs und Vereinfachungen | Vor Commit/PR; "review meine Änderungen" |
| `/review` | Reviewt einen GitHub-Pull-Request | PR-Link/Nummer soll begutachtet werden |
| `/security-review` | Sicherheits-Review der anstehenden Änderungen im Branch | Sicherheitsrelevante Änderungen (Auth, Input, Secrets, Netzwerk) |
| `/verify` | Verifiziert eine Änderung durch echtes Ausführen der App | "Funktioniert das wirklich?"; vor dem Push; Fix bestätigen |
| `/simplify` | Vereinfacht geänderten Code (Wiederverwendung, Effizienz) und wendet Fixes an | Nach größeren Implementierungen; Code fühlt sich umständlich an |
| `/run` | Startet die App des Projekts, um eine Änderung live zu sehen | "Starte die App", Screenshot gewünscht, manueller Funktionstest |
| `/deep-research` | Mehrquellen-Recherche mit Verifikation und zitiertem Bericht | Tiefe Recherche-Fragen; "recherchiere gründlich zu X" |
| `/init` | Erstellt ein CLAUDE.md mit Codebase-Dokumentation | Neues Projekt aufsetzen; Claude kennt das Projekt noch nicht |
| `/loop` | Führt einen Prompt/Command wiederkehrend im Intervall aus | "Prüfe alle 5 Minuten X"; Deploy/CI beobachten |
| `/update-config` | Konfiguriert settings.json (Hooks, Permissions, Env-Variablen) | "Erlaube X", "immer wenn Y, dann Z", Hook-Probleme |
| `/fewer-permission-prompts` | Erstellt Allowlist häufiger read-only Befehle | Zu viele Berechtigungs-Nachfragen |
| `/claude-api` | Referenz für Claude-API/SDK (Modelle, Preise, Tool-Use) | Fragen zu Claude-Modellen, API-Nutzung, LLM-Integration |
| `/session-start-hook` | Richtet SessionStart-Hooks für Web-Sessions ein | Repo für Claude Code Web vorbereiten (Tests/Linter beim Start) |

## Sektion B — Empfohlen zu installieren (aus awesome-claude-code)

Kuratierte Top-Auswahl aus der Liste. Bei passendem Bedarf zuerst Installation prüfen statt Eigenbau (`/skill-creator` Schritt 2).

| Ressource | Stärke | Wann installieren | Link |
|---|---|---|---|
| Superpowers | Engineering-Grundkompetenzen: Planen, Testen, Debuggen, Reviewen | Als solide Basis für Software-Arbeit | https://github.com/obra/superpowers |
| Trail of Bits Security Skills | Professionelles Security-Auditing (CodeQL, Semgrep, Variant Analysis) | Bei sicherheitskritischem Code | https://github.com/trailofbits/skills |
| Compound Engineering Plugin | Fehler in Lektionen/Checklisten verwandeln — lernende Workflows | Wenn Team-Wissen wachsen soll | https://github.com/EveryInc/compound-engineering-plugin |
| Context Engineering Kit | Kontext-Techniken mit minimalem Token-Footprint | Bei langen Sessions / Kontext-Problemen | https://github.com/NeoLabHQ/context-engineering-kit |
| TÂCHES CC Resources | Meta-Skills: skill-auditor, Hook-Erstellung | Zum Auditieren/Verbessern eigener Skills | https://github.com/glittercowboy/taches-cc-resources |
| Everything Claude Code | Beispielhafte Patterns für jedes Claude-Code-Feature | Als Nachschlagewerk/Vorlagensammlung | https://github.com/affaan-m/everything-claude-code |
| cc-devops-skills | IaC/DevOps-Generatoren mit Validierung für alle großen Plattformen | Bei Infrastruktur-/Deploy-Arbeit | https://github.com/akin-ozer/cc-devops-skills |
| Claude Scientific Skills | Forschung, Analyse, Finance, Writing | Bei wissenschaftlich-analytischer Arbeit | https://github.com/K-Dense-AI/claude-scientific-skills |
| Fullstack Dev Skills | 65 Framework-Skills + `/common-ground` (deckt Claudes Annahmen auf) | Bei Fullstack-Projektarbeit | https://github.com/jeffallan/claude-skills |
| claude-code-tools | Session-Kontinuität, Session-Suche, tmux-Integration, Safety-Hooks | Gegen Kontextverlust zwischen Sessions | https://github.com/pchalasani/claude-code-tools |

Installation je nach Ressource: als Plugin (`/plugin install …`), via `npx skills add <owner/repo>` oder manuell nach `~/.claude/skills/` kopieren — README der Ressource beachten.

## Sektion C — Eigene lokale Skills (Donna-System)

> **AUSFÜLLEN**: Diese Sektion ist ein Platzhalter. Lokal ausfüllen (nicht in ein öffentliches Repo pushen, falls die Inhalte intern sind):
>
> 1. Lokal ausführen: `find ~/donna -name "SKILL.md" | sort` (Pfad anpassen)
> 2. Pro Skill eine Zeile in die Tabelle: Name, Zweck (1 Satz), Trigger
> 3. Alternativ `/skill-creator` bitten: "Trage meine Donna-Skills in die Registry ein" — er liest die SKILL.md-Dateien und füllt die Tabelle.

| Skill | Zweck | Aktivieren wenn |
|---|---|---|
| _(eintragen)_ | | |
