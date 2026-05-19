# 🤖 Agente AI con N8N — Client Management Bot

> Automazione intelligente no-code per la gestione clienti via Telegram.

---

## 📋 Project Overview

This project is a **fully functional AI agent** built with **N8N** (no-code). It receives commands in natural language via a Telegram bot — text or voice — and autonomously executes real operations: it looks up the client database on Airtable, sends emails via Gmail, and creates events on Google Calendar, all without opening a single app.

---

## 📁 Repository Structure

```
agent-ai-n8n/
│
├── workflow/
│   └── n8n_workflow.json        # Exportable N8N workflow
├── AgentAI_N8N_LucaFrittitta.pptx   # Project presentation
└── README.md
```

---

## 🛠️ Tech Stack

| Layer | Tool |
|-------|------|
| **Platform** | N8N (no-code workflow automation) |
| **I/O Channel** | Telegram Bot |
| **AI Model** | OpenAI GPT |
| **Transcription** | OpenAI Whisper |
| **Memory** | N8N Simple Memory (Window Buffer — 10 messages) |
| **Database** | Airtable (client address book) |
| **Email** | Gmail |
| **Calendar** | Google Calendar |

---

## ⚙️ How It Works

The agent follows a structured 8-step flow:

```
1. TRIGGER      → User sends text or voice message to Telegram bot
2. SWITCH       → Routing: text → AI Agent / audio → Transcription
3. WHISPER      → Converts audio to text and merges it into the flow
4. AI AGENT     → Processes the prompt, queries memory, selects the right tool
5. AIRTABLE     → Retrieves client name and email from the address book
6. GMAIL        → Composes and sends the email automatically
7. GOOGLE CAL   → Creates the event with attendees and time
8. OUTPUT       → Sends confirmation back to the user on Telegram
```

---

## 🧠 System Prompt Design

The system prompt is the core of the agent. Key design decisions:

- **Exact tool names** matching N8N node names (`Rubrica`, `Invio Email`, `Calendario`)
- **Mandatory address book rule** — the agent must query Airtable before any action
- **Dynamic date/time** injection via `{{ $now }}` for temporal references
- **Error handling** — covers missing contacts, duplicate names, incomplete data; the agent always asks for clarification when uncertain
- **Output language** — always Italian, formal tone

---

## ✨ Key Features

**🎙 Multimodal Input** — Accepts both text and voice via OpenAI Whisper, lowering the barrier to use for anyone.

**🧠 Contextual Memory** — Window Buffer Memory with 10 messages enables coherent multi-turn conversations.

**📊 Airtable as Single Source of Truth** — All client data is centralized; the agent is forced to consult it before every action.

**🔧 100% No-Code** — Built entirely on N8N without writing a single line of code.

**🧩 Modular Architecture** — Each tool is independent; new features can be added without touching the existing flow.

**⚡ Real Automation** — The agent doesn't just answer questions — it executes concrete actions with measurable time savings.

---

## 🚀 How to Run

1. Import `n8n_workflow.json` into your N8N instance
2. Configure credentials for: Telegram, OpenAI, Airtable, Gmail, Google Calendar
3. Set your Airtable Base ID and Table ID in the Airtable node
4. Activate the workflow
5. Start chatting with your Telegram bot

---

## 👤 Author

**Luca Frittitta**
*AI Agent with N8N — No-Code Automation Project*

---

> *"The agent doesn't just answer questions — it executes real actions: sends emails, books meetings, retrieves data. All from a simple Telegram chat."*

---

Watch the demostration video here: https://www.loom.com/share/e08389ea7b88458fbd6ce35c34da1f72
