# Schritt 4: Ordnerstruktur anlegen

🟢 **Kein Risiko** – wir erstellen nur Ordner und leere Dateien.

---

## Was passiert hier?

Damit dein Assistent Projekte, Meetings und Wissen sauber organisieren kann, braucht er eine feste Ordnerstruktur. Wie Schubladen in einem Büro – jedes Ding hat seinen Platz.

## So erklärst du es deinem User

> "Ich lege jetzt ein paar Ordner an – wie Schubladen für verschiedene Sachen. Projekte kommen in einen Ordner, abgeschlossene Projekte ins Archiv, Meeting-Notizen in einen eigenen Ordner. So finde ich alles wieder und nichts geht verloren."

## Anleitung

### 4.1 — Ordner erstellen

```bash
mkdir -p projects/_template/{docs,conversations}
mkdir -p projects_archived
mkdir -p meetings
mkdir -p knowledge/people
```

### 4.2 — Projekt-Vorlage erstellen

Datei `projects/_template/AGENT.md`:
```markdown
# Projekt: [NAME]

## Überblick
[Was ist das Projekt? Was soll erreicht werden?]

## Kontext
[Hintergrund, Motivation, Links]
```

Datei `projects/_template/ROADMAP.md`:
```markdown
# Roadmap: [NAME]

**Status:** 🟡 Active
**Created:** YYYY-MM-DD

## Phases

### Phase 1: [Name]
- [ ] Task 1
- [ ] Task 2

## Log
- YYYY-MM-DD: Projekt erstellt
```

### 4.3 — Weitere Dateien erstellen

Datei `meetings/INDEX.md`:
```markdown
# Meetings Index

| Datum | Thema | Teilnehmer | Projekt |
|-------|-------|------------|---------|
```

Datei `IDEAS.md`:
```markdown
# IDEAS.md - Ideensammlung

*Schnell festgehaltene Ideen via /idea.*
```

Datei `TASKS.md`:
```markdown
# TASKS.md - Aufgaben-Backlog

*Schnell festgehaltene Tasks via /task.*
```

## Prüfen

Tippe `/create test-projekt Das ist ein Test`. Der Assistent sollte ein neues Projekt mit der Vorlage anlegen. Danach `/close test-projekt` um es wieder zu archivieren.

## Checkliste

- [ ] Alle Ordner erstellt
- [ ] Projekt-Vorlage vorhanden
- [ ] meetings/INDEX.md angelegt
- [ ] IDEAS.md angelegt
- [ ] TASKS.md angelegt
- [ ] Test-Projekt erstellt und geschlossen
