# REX AI CRM Assistant (Telegram + GHL)

An AI-powered CRM assistant that lets real estate agents query and interact with their GoHighLevel CRM data through Telegram — in natural language.

## What It Does

- Receives messages from agents via **Telegram**
- Routes queries to an **OpenAI GPT-4 AI agent** with persistent memory
- Executes live lookups against **GoHighLevel CRM** via HTTP tool calls
- Returns answers, summaries, and updates back to Telegram — conversationally

## Tech Stack

| Tool | Role |
|---|---|
| n8n | Workflow orchestration |
| Telegram Bot | User interface / trigger |
| OpenAI GPT-4 | AI reasoning & response generation |
| GoHighLevel API | CRM data source (contacts, opportunities, pipelines) |
| LangChain Agent (n8n) | Memory + tool-calling framework |

## How It Works

```
Telegram Message
      ↓
  AI Agent (GPT-4 + memory window)
      ↓
  HTTP Tool → GoHighLevel CRM API
      ↓
  Response → Telegram
```

The agent maintains **conversation memory** across turns, so agents can ask follow-up questions naturally (e.g., "What about their last note?" after asking about a contact).

## Key Features

- Natural language CRM queries — no dashboard needed
- Memory-aware multi-turn conversations
- Live data — always pulls current CRM state
- Deployed and active in production

## Screenshot

> *Add workflow-canvas.png to screenshots/ folder*
