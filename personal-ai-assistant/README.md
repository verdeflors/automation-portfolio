# Personal AI Assistant (Telegram + Gmail + Google Calendar)

A fully functional personal AI assistant that manages email and calendar through Telegram, powered by an LLM with tool-calling and memory.

## What It Does

- Listens for commands via **Telegram**
- Uses an **AI agent** (OpenAI + OpenRouter) to understand intent
- Reads and sends **Gmail** emails on command
- Creates, updates, and deletes **Google Calendar** events
- Maintains **conversation memory** so context carries across messages

## Tech Stack

| Tool | Role |
|---|---|
| n8n | Workflow orchestration |
| Telegram Bot | Conversational UI |
| OpenAI / OpenRouter | LLM reasoning layer |
| Gmail (n8n Tool) | Email read/send capability |
| Google Calendar (n8n Tool) | Calendar management |
| LangChain Memory | Window-based conversation memory |

## How It Works

```
Telegram message
      ↓
  AI Agent (LLM + memory)
      ↓
  Route to tool: Gmail OR Google Calendar
      ↓
  Execute action → Reply via Telegram
```

## Example Interactions

- "What emails did I get from John today?" → reads Gmail, summarizes
- "Schedule a call with Sarah tomorrow at 2pm" → creates Calendar event
- "Cancel my 3pm meeting" → deletes the event

## Key Features

- Multi-tool AI agent (not just a chatbot — actually takes actions)
- Dual LLM support via OpenRouter for fallback/cost optimization
- Active in production for daily personal use

## Screenshot

> *Add workflow-canvas.png to screenshots/ folder*
