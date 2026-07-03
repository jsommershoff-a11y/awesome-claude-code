---
name: perfect-prompt
description: Baut vor dem Start einer Aufgabe einen präzisen, vollständigen Arbeitsauftrag - klärt fehlende Informationen durch gezielte Fragen, wählt passende Skills aus der Registry aus und formuliert daraus den perfekten Prompt. Verwenden am Anfang jeder größeren oder unklaren Aufgabe. Trigger: "perfekter Prompt", "Prompt bauen", "Aufgabe vorbereiten", "prime", vage/unterspezifizierte Aufträge.
---

# Perfect-Prompt

Du verwandelst einen groben Auftrag in einen präzisen Arbeitsauftrag, BEVOR die eigentliche Arbeit beginnt. Ergebnis: ein strukturierter Prompt-Block plus die Liste der zu aktivierenden Skills. Das kostet 2 Minuten am Anfang und spart Korrekturschleifen am Ende.

## Ablauf

### Schritt 1: Auftrag einordnen

Lies den Auftrag des Nutzers und stufe ihn ein:

- **Trivial** (eindeutig, klein, ein Schritt): Diesen Skill NICHT durchziehen — direkt arbeiten. Sag dem Nutzer kurz, dass keine Klärung nötig war.
- **Substanziell** (mehrdeutig, mehrere Schritte, unklares Zielbild): Weiter mit Schritt 2.

### Schritt 2: Lücken identifizieren und gezielt nachfragen

Prüfe, welche dieser 7 Bausteine fehlen oder unklar sind, und frage NUR die fehlenden ab (gebündelt, max. 4 Fragen auf einmal):

1. **Ziel**: Was ist am Ende fertig? Woran wird Erfolg gemessen?
2. **Kontext**: Welches Projekt/System/Umfeld? Welche Vorarbeit existiert?
3. **Eingaben**: Welche Dateien, Daten, Zugänge stehen zur Verfügung?
4. **Einschränkungen**: Was darf NICHT passieren (öffentlich machen, löschen, Kosten, Deadlines)?
5. **Ausgabeformat**: Datei? Bericht? Code + Tests? PR? Sprache? Umfang?
6. **Qualitätskriterien**: Was unterscheidet "okay" von "exzellent"? Gibt es ein Vorbild/Beispiel?
7. **Entscheidungsspielraum**: Was darf eigenständig entschieden werden, was ist Rückfrage-pflichtig?

Faustregel: Lieber eine Runde präziser Fragen als drei Runden Nacharbeit. Aber nicht abfragen, was aus dem Kontext bereits klar ist — das nervt.

### Schritt 3: Passende Skills auswählen

Lies die Skill-Registry (lokal `.claude/skills/SKILLS_REGISTRY.md`, bei globaler Installation `~/.claude/skills/SKILLS_REGISTRY.md`) und wähle die Skills, deren Trigger zum Auftrag passen:

- 0 Treffer → notieren "keine Spezial-Skills nötig"; wenn die Aufgabe wiederkehrend ist, `/skill-creator` als Follow-up vorschlagen.
- 1–3 Treffer → diese Skills im Prompt-Block als "zu aktivieren" aufführen.
- Treffer in Sektion B (empfohlen, aber nicht installiert) → dem Nutzer die Installation vorschlagen, bevor die Arbeit beginnt.

### Schritt 4: Den perfekten Prompt bauen

Fasse alles in diesem Block zusammen und zeige ihn dem Nutzer zur Bestätigung:

```
## Arbeitsauftrag

**Ziel**: <messbares Endergebnis>
**Kontext**: <Projekt, Umfeld, Vorarbeit>
**Eingaben**: <Dateien, Daten, Zugänge>
**Einschränkungen**: <harte Grenzen, No-Gos>
**Ausgabeformat**: <Form, Sprache, Umfang des Ergebnisses>
**Qualitätskriterien**: <woran "exzellent" erkannt wird>
**Entscheidungsspielraum**: <eigenständig vs. rückfragepflichtig>

**Aktivierte Skills**: <Liste aus Schritt 3, mit je 1 Satz warum>

**Vorgehen**: <3–7 nummerierte Schritte, letzter Schritt = Prüfung gegen die Qualitätskriterien>
```

### Schritt 5: Bestätigen und starten

Frage: "Passt der Auftrag so, oder soll ich etwas ändern?" Nach Bestätigung: Skills aktivieren und den Arbeitsauftrag abarbeiten. Der letzte Arbeitsschritt ist IMMER die Selbstprüfung gegen die Qualitätskriterien aus dem Block.

## Grenzen

- Dieser Skill führt die Aufgabe nicht selbst aus — er bereitet sie vor.
- Bei trivialen Aufgaben wird er übersprungen (siehe Schritt 1); er ist ein Werkzeug, kein Bürokratie-Ritual.
