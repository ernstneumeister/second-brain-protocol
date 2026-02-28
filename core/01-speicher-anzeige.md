# Schritt 1: Speicher-Anzeige einrichten

🟢 **Kein Risiko** – wir fügen nur eine Anzeige hinzu.

---

## Was passiert hier?

Dein Assistent hat ein "Arbeitsfenster" – wie ein Schreibtisch, der nur eine bestimmte Menge Papier halten kann. Wenn er voll ist, vergisst er ältere Sachen aus dem Gespräch.

Bisher siehst du nicht, wie voll der Schreibtisch ist. Nach diesem Schritt zeigt dir dein Assistent am Ende jeder Nachricht eine Prozentzahl – so weißt du immer Bescheid.

## So erklärst du es deinem User

> "Ich richte jetzt eine kleine Anzeige ein. Am Ende jeder Nachricht siehst du eine Zahl wie '📊 38%' – das zeigt dir wie voll mein Speicher ist. Unter 70% ist alles gut. Über 85% sollten wir speichern, damit ich nichts vergesse."

## Anleitung

Füge folgende Zeilen in die AGENTS.md Datei ein (erstelle sie falls sie nicht existiert):

```markdown
## Context % Display
Zeige am Ende jeder Antwort den Context-Verbrauch via `session_status`. Format: `📊 XX%`
- Unter 50%: normal
- 50-70%: konsistent anzeigen
- 70-85%: proaktiv alle aktiven Dateien sichern, User informieren
- 70-85%: still alles in Dateien sichern, nichts sagen
- 85-94%: kurzer Hinweis: "📊 XX% – Hab alles gesichert."
- 95%+: "📊 XX% – Speicher fast voll. Alles ist gesichert. Gleich fasse ich ältere Teile unseres Gesprächs zusammen damit wir weiterarbeiten können – es geht nichts verloren."
```

## Prüfen

Schreibe eine kurze Nachricht. Am Ende sollte die Prozentzahl erscheinen.

## Checkliste

- [ ] Regel in AGENTS.md eingefügt
- [ ] Prozentzahl erscheint am Ende der Nachricht
- [ ] User versteht was die Zahl bedeutet
