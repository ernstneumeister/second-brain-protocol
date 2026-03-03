# 06 — QMD: Bessere Gedächtnis-Suche (Optional)

> ⚠️ **Nur für lokale Installationen mit GPU empfohlen!**
> 
> - ✅ Mac Mini (M1/M2/M3/M4)
> - ✅ Lokaler PC mit NVIDIA GPU
> - ❌ Cloud-Server ohne GPU (Hetzner, DigitalOcean, etc.)
> - ❌ ARM-Server (Raspberry Pi, Hetzner CAX, etc.)

---

## Was ist QMD?

QMD ist ein **optionales Upgrade** für die Gedächtnis-Suche deines Assistenten.

**Normale Suche (Standard):**
- Dein Assistent sucht nach dem Wort "Pizza"
- Findet nur Stellen wo "Pizza" steht
- Wenn du "Margherita" geschrieben hast → findet er's nicht

**Mit QMD:**
- Dein Assistent sucht nach "Pizza"
- QMD denkt: "Pizza? Ich schau auch nach Margherita, Italienisch, Käse..."
- Findet es, auch wenn du es anders geschrieben hast

---

## Warum nur mit GPU?

QMD nutzt kleine KI-Modelle die lokal auf deinem Computer laufen:

| Modell | Aufgabe |
|--------|---------|
| EmbeddingGemma (300M) | Text in Zahlen umwandeln |
| Qwen3-Reranker (600M) | Ergebnisse sortieren |
| Query-Expansion (1.7B) | Suche erweitern |

Diese Modelle brauchen Rechenpower:
- **Mit GPU (Mac Mini M-Chip):** ~50ms pro Suche ✅
- **Ohne GPU (Cloud-Server):** ~2-5 Sekunden pro Suche ❌
- **ARM ohne GPU:** Build scheitert oft komplett ❌

---

## Brauche ich QMD?

**Nein, wenn:**
- Du weniger als ~200 Memory-Dateien hast
- Die Standard-Suche funktioniert gut für dich
- Dein Server keine GPU hat

**Ja, wenn:**
- Du einen Mac Mini mit M-Chip hast
- Du hunderte Memory-Dateien über Monate gesammelt hast
- Du maximale Such-Qualität willst
- Du keine API-Kosten für Embeddings willst (QMD ist kostenlos)

---

## Installation (nur Mac Mini / GPU)

**Schritt 1: Bun installieren**
```bash
curl -fsSL https://bun.sh/install | bash
source ~/.bashrc
```

**Schritt 2: QMD installieren**
```bash
bun install -g https://github.com/tobi/qmd
```

**Schritt 3: Memory-Ordner hinzufügen**
```bash
qmd collection add memory ~/dein-workspace/memory
qmd update
qmd embed
```

**Schritt 4: OpenClaw konfigurieren**
```bash
openclaw config set memory.backend qmd
openclaw gateway restart
```

---

## Ohne GPU? Standard nutzen!

Die Standard Memory Search von OpenClaw nutzt **Remote Embeddings**:
- Suchtext wird an OpenAI/Gemini geschickt
- Die machen die Rechenarbeit
- Kostet ~0.01 Cent pro Suche
- Funktioniert auf jedem Server

**Das ist völlig ausreichend für 99% der Nutzer.**

---

## Zusammenfassung

| Setup | Empfehlung |
|-------|------------|
| Mac Mini (M1-M4) | ✅ QMD empfohlen |
| PC mit NVIDIA GPU | ✅ QMD möglich |
| Cloud-Server mit GPU | 🟡 QMD möglich, aber teuer |
| Cloud-Server ohne GPU | ❌ Standard nutzen |
| ARM-Server | ❌ Standard nutzen |

**Im Zweifel:** Standard lassen. QMD ist ein Nice-to-have, kein Must-have.
