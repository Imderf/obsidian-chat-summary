# 🗂️ Obsidian Chat Summary — Claude Skill

> Turn any Claude conversation into a structured Obsidian note with a single word.

**English** | [Español](#español)

---

A Claude skill that reads your conversation, extracts what matters, and generates a ready-to-paste `.md` file — with proper frontmatter, tags, and vault path — in seconds.

No formatting. No copy-pasting. No thinking about folder structure. Just type `obsidian`.

---

## The Problem

After a productive Claude session, your insights live in a chat window that you'll never find again.

| Without this skill | With this skill |
|---|---|
| Manually copy key points | Type `obsidian` — done |
| Guess the right folder path | Path suggested automatically |
| Remember which tags to use | Tags inferred from context |
| Repeat the process every time | Config saved once, works forever |
| Only works for you | Setup wizard adapts to any vault |

---

## How It Works

```
You: [any conversation]

You: obsidian

Claude: 📝 Here's your note...

---
title: "Topic of the conversation"
date: 2026-05-06
tags:
  - "#world"
  - "#note-type"  
  - "#status"
source: claude-chat
---

## Context
## What was worked on
## Key decisions
## Next steps
## Tools / References

📁 Save to: work/client/2026-05-06-topic.md
⚡ Claude Code command: [optional, ready to paste]
```

---

## Triggers

The skill activates on any of these:

```
obsidian
resumen obsidian
guardar en obsidian
save to obsidian
nota obsidian
haz un resumen para obsidian
```

Or any phrase that mentions Obsidian + summarizing/saving.

---

## Install

**1.** Download [`obsidian-chat-summary.skill`](./obsidian-chat-summary.skill)

**2.** Open [claude.ai](https://claude.ai) → profile icon → **Customize**

**3.** Go to **Skills** → click **+** → upload the file

**4.** Done. Active immediately across all your chats.

> ⚠️ Skills work in regular claude.ai chats only — not inside Projects, not in Claude Code.

---

## First-Time Setup

The first time you type `obsidian`, the skill asks about your vault. Three ways to share it:

### Option 1 — Describe it yourself
Tell Claude your main folders, what tags you use, and your note language. Doesn't have to be perfect.

### Option 2 — Send a screenshot
Take a screenshot of your Obsidian file panel and upload it. Claude reads the folder tree and builds your config automatically.

```
[screenshot of your vault]
→ Claude reads it
→ Confirms: "Found this structure — correct?"
→ Saves your config
```

### Option 3 — I'm new to Obsidian
Tell Claude what you use it for. It proposes a clean starter structure from scratch.

---

## Saving Your Config

After setup, Claude gives you a config block. Paste it in **Settings → Preferences** on claude.ai:

```yaml
obsidian-vault-config
worlds:
  - path: work/
    tag: "#work"
  - path: personal/
    tag: "#personal"
note_types: ["#meeting", "#research", "#idea", "#project", "#content"]
operative_tags: ["#type/invoice", "#type/email"]
client_tags: ["#client/acme", "#client/globex"]
status_tags: ["#status/active", "#status/done", "#status/exploring"]
language: english
date_format: YYYY-MM-DD
```

Once saved, Claude never asks again — every conversation gets a note tailored to your vault.

---

## Output Structure

Every generated note:

```markdown
---
title: "Exact topic of the conversation"
date: YYYY-MM-DD
tags:
  - "#world-folder"
  - "#note-type"
  - "#client-or-project"   ← omitted if none
  - "#operative-tag"       ← omitted if none
  - "#status"
source: claude-chat
---

## Context
1-2 sentences about what this conversation was and why it matters.

## What was worked on
- Bullet list of topics, decisions, outputs

## Key decisions
- Omitted if none

## Next steps
1. Omitted if none

## Tools / References
- Omitted if none

## Additional notes
- Omitted if nothing
```

Empty sections are **never** included.

---

## Vault Path Logic

The skill suggests where to save the note based on your config:

| Conversation about | Suggested path |
|---|---|
| Work project for a client | `work/client/2026-05-06-topic.md` |
| Personal idea | `personal/2026-05-06-idea.md` |
| Stream content concept | `content/ideas/2026-05-06-stream-concept.md` |
| No clear match | `inbox/2026-05-06-topic.md` ← reclassify later |

**New paths** are proposed automatically with a one-line justification:
> ⚠️ New path — created because this is the first note for this client.

---

## Claude Code Integration (Optional)

If you use Claude Code connected to your vault — locally or on a remote VPS — the skill outputs a ready-to-run command at the end of every note:

```
Save the following content to: work/client/2026-05-06-topic.md
Create the folder if it doesn't exist.

[paste the markdown block here]
```

Copy it. Paste it in your Claude Code session. Done.

Works with any setup — local vault, VPS, or any filesystem Claude Code can access.

---

## Language

The skill detects your language automatically from your messages.

- Write in English → note and setup come in English
- Write in Spanish → note and setup come in Spanish
- No configuration needed

---

## Reset Config

To redo the setup wizard:

1. Go to **Settings → Preferences** on claude.ai
2. Delete the `obsidian-vault-config` block
3. Type `obsidian` in a new chat

---

## Key Insight

The skill is designed around one principle: **your context is already in the conversation**. Claude reads what you discussed, infers the structure, and maps it to your vault — you just trigger it.

The vault path suggestion follows your conventions, not generic ones. If your vault has `work/client-name/`, new notes go there. If it doesn't exist yet, the skill proposes the closest logical path and tells you why.

---

## License

MIT — free to use, modify, and share.

---

Made with Claude · [claude.ai](https://claude.ai)

---

## Español

> Convierte cualquier conversación de Claude en una nota estructurada de Obsidian con una sola palabra.

Una skill de Claude que lee tu conversación, extrae lo importante y genera un archivo `.md` listo para pegar — con frontmatter, tags y ruta de vault — en segundos.

### Instalación

1. Descarga [`obsidian-chat-summary.skill`](./obsidian-chat-summary.skill)
2. Abre [claude.ai](https://claude.ai) → ícono de perfil → **Personalizar**
3. Ve a **Habilidades** → clic en **+** → sube el archivo
4. Listo. Activa de inmediato en todos tus chats.

### Uso

Al final de cualquier conversación escribe:

```
obsidian
```

La skill se activa automáticamente y genera tu nota.

### Primera vez

Te preguntará sobre tu vault con 3 opciones: describírselo, mandar un pantallazo, o empezar desde cero si eres nuevo. Después te da un bloque de config para pegar en **Settings → Preferences** — y nunca vuelve a preguntar.

> ⚠️ Las skills funcionan solo en chats normales de claude.ai. No funcionan dentro de Proyectos ni en Claude Code.
