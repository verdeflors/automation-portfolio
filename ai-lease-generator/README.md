# AI Lease Generator (Real Estate Document Automation)

An AI agent that generates real estate lease agreements on demand via Telegram, pulling property and tenant data from GoHighLevel CRM.

## What It Does

- Accepts lease generation requests through **Telegram**
- AI agent gathers required info (property, tenant, terms) conversationally
- Fetches live data from **GoHighLevel CRM** via HTTP tool calls
- Generates a complete, formatted lease document
- Delivers the document back through Telegram

## Tech Stack

| Tool | Role |
|---|---|
| n8n | Workflow orchestration |
| Telegram Bot | User interface / trigger |
| OpenAI GPT-4 | Document generation + conversation |
| GoHighLevel API | Contact & property data source |
| LangChain Agent | Tool-calling + memory framework |

## How It Works

```
Telegram: "Generate lease for [tenant name]"
      ↓
  AI Agent (GPT-4 + memory)
      ↓
  HTTP Tool → GHL CRM (fetch contact/property details)
      ↓
  Generate lease document
      ↓
  Send document → Telegram
```

## Key Features

- Conversational document generation — agent asks clarifying questions if info is missing
- Pulls live CRM data — no copy-pasting needed
- Domain-specific prompt engineering for real estate lease format
- Saves hours of manual document preparation per deal

## Screenshot

> *Add workflow-canvas.png to screenshots/ folder*
