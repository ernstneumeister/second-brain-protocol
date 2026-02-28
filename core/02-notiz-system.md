# Schritt 2: Notiz-System einrichten

🟢 **Kein Risiko** – wir erstellen nur Dateien und Ordner.

---

## Was passiert hier?

Dein Assistent vergisst alles zwischen Gesprächen. Stell dir vor, dein Mitarbeiter wacht jeden Morgen ohne jede Erinnerung auf. Die Lösung: Er schreibt sich Notizen, die er morgens als erstes liest.

Wir richten jetzt dieses Notiz-System ein:
- **Tagesnotizen** – was heute passiert ist (wie ein Tagebuch)
- **Langzeit-Gedächtnis** – wichtige Entscheidungen, Präferenzen, Learnings

## So erklärst du es deinem User

> "Ich richte mir jetzt ein Notiz-System ein. Ab sofort schreibe ich mir auf was wir besprechen und entscheiden. Wenn wir morgen weiterarbeiten, lese ich meine Notizen und weiß sofort wieder Bescheid – ohne dass du mir alles nochmal erklären musst."

## Anleitung

### 2.1 — Memory-Ordner erstellen

```bash
mkdir -p memory
```

### 2.2 — Langzeit-Gedächtnis anlegen

Erstelle eine `MEMORY.md` im Workspace (falls sie nicht existiert):

```markdown
# MEMORY.md - Langzeit-Gedächtnis

Hier stehen wichtige Entscheidungen, Präferenzen und Learnings die über einzelne Gespräche hinaus relevant sind.
```

### 2.3 — Compaction-Schutz einrichten

Wenn der Speicher voll wird, fasst OpenClaw ältere Nachrichten automatisch zusammen. Dabei können Details verloren gehen. Wir sorgen dafür, dass der Assistent vorher alles sichert.

Füge in AGENTS.md ein:

```markdown
## Compaction Handling
When you receive "Pre-compaction memory flush":
1. IMMEDIATELY save current state to memory/YYYY-MM-DD.md
2. Update any active project files
3. Reply with just: NO_REPLY

After compaction (context drops suddenly):
1. Run sessions_history for this session
2. Read today's memory file
3. Check active work files
4. THEN respond with recovered context — never respond confused
```

### 2.4 — Auto-Save aktivieren

Der Assistent soll nicht warten bis man ihn bittet zu speichern, sondern laufend seine Notizen aktualisieren.

Füge in AGENTS.md ein:

```markdown
## Auto-Save
Nicht auf /save warten. Dateien laufend updaten:
1. Aktive Dateien während der Arbeit updaten
2. memory/YYYY-MM-DD.md bei wichtigen Events ergänzen
3. git add -A && git commit -m "Auto-save: [kurz]" && git push
```

## Prüfen

Sage deinem Assistenten etwas wie "Merke dir: Ich bevorzuge kurze Emails." Er sollte das in einer Datei festhalten.

## Checkliste

- [ ] memory/ Ordner erstellt
- [ ] MEMORY.md angelegt
- [ ] Compaction-Schutz in AGENTS.md
- [ ] Auto-Save in AGENTS.md
- [ ] Test: Assistent merkt sich etwas
