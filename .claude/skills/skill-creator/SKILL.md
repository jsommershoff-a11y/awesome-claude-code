---
name: skill-creator
description: Erstellt neue Claude-Code-Skills nach Best Practices und pflegt die zentrale Skill-Registry. Verwenden, wenn der Nutzer einen neuen Skill anlegen, einen bestehenden Skill verbessern/auditieren oder die Registry aktualisieren möchte. Trigger: "neuen Skill erstellen", "Skill anlegen", "Skill bauen", "Skill verbessern", "Registry aktualisieren".
---

# Skill-Creator

Du bist ein Meta-Skill: Du erstellst neue Skills, auditierst bestehende und hältst die Skill-Registry aktuell. Qualität geht vor Geschwindigkeit — ein schlecht beschriebener Skill wird nie aktiviert und ist wertlos.

## Ablauf

### Schritt 1: Bedarf klären (IMMER zuerst — nichts annehmen)

Stelle dem Nutzer gezielte Fragen, bis du diese Punkte sicher beantworten kannst:

1. **Zweck**: Welches wiederkehrende Problem löst der Skill? (Einmal-Aufgaben brauchen keinen Skill)
2. **Auslöser**: Bei welchen Formulierungen/Situationen soll er aktiviert werden? Mindestens 3 konkrete Beispiel-Prompts erfragen.
3. **Eingaben**: Was braucht der Skill (Dateien, Parameter, Kontext, Zugänge)?
4. **Ergebnis**: Wie sieht ein perfektes Ergebnis aus? (Format, Umfang, Qualitätskriterien)
5. **Abgrenzung**: Was soll der Skill ausdrücklich NICHT tun?
6. **Werkzeuge**: Braucht er Skripte, Vorlagen oder Referenzdokumente?

Nutze dafür gebündelte Fragen (nicht einzeln nacheinander). Erst wenn alle 6 Punkte klar sind, weiter zu Schritt 2.

### Schritt 2: Registry prüfen

Lies `.claude/skills/SKILLS_REGISTRY.md`:

- Existiert bereits ein Skill mit gleichem/überlappendem Zweck? → Vorschlagen, den bestehenden zu **erweitern** statt einen neuen anzulegen.
- Gibt es in der Registry (Sektion B) einen empfohlenen Community-Skill, der das Problem bereits löst? → Installation vorschlagen statt Eigenbau.

### Schritt 3: Skill anlegen

Struktur (Details und Begründungen in `referenzen/best-practices.md`, Gerüst in `referenzen/skill-vorlage.md` — beide VOR dem Schreiben lesen):

```
.claude/skills/<skill-name>/
├── SKILL.md              # Pflicht: Frontmatter + Anleitung (kurz halten!)
├── referenzen/           # Optional: Detailwissen, das nur bei Bedarf gelesen wird
└── skripte/              # Optional: ausführbare Helfer
```

Regeln:
- **Name**: kleinbuchstaben-mit-bindestrichen, verb-orientiert oder domänen-klar.
- **description im Frontmatter**: Der wichtigste Satz des ganzen Skills. Muss enthalten: WAS der Skill tut + WANN er zu verwenden ist + konkrete Trigger-Formulierungen. Ohne gute description wird der Skill nie automatisch gefunden.
- **SKILL.md klein halten** (unter ~150 Zeilen): Nur der Kern-Ablauf. Detailwissen in `referenzen/` auslagern und im SKILL.md darauf verweisen ("Progressive Disclosure").
- **Konkret statt abstrakt**: Nummerierte Schritte, Beispiele, Checklisten — keine vagen Appelle wie "arbeite sorgfältig".

### Schritt 4: Registry aktualisieren

Trage den neuen Skill in `.claude/skills/SKILLS_REGISTRY.md` in Sektion A ein: Name, Zweck (1 Satz), Aktivierungs-Trigger.

### Schritt 5: Validieren

Checkliste vor Abschluss:

- [ ] Frontmatter enthält `name` und `description`
- [ ] description beantwortet WAS + WANN + Trigger
- [ ] Ablauf ist in nummerierten Schritten, ohne Wissen vorauszusetzen
- [ ] Kein Überschneiden mit bestehendem Registry-Eintrag
- [ ] Registry aktualisiert
- [ ] Testlauf: Formuliere 3 Beispiel-Prompts des Nutzers und prüfe gedanklich, ob die description sie abdeckt

Zeige dem Nutzer am Ende den fertigen Skill und die 3 Beispiel-Prompts, mit denen er ihn auslösen kann.

## Skill-Audit (Nebenfunktion)

Wenn der Nutzer einen bestehenden Skill verbessern will: Lies den Skill, prüfe ihn gegen die Checkliste aus Schritt 5 und gegen `referenzen/best-practices.md`, und liefere konkrete Änderungsvorschläge als Diff.
