# Automation Portfolio

A collection of production-grade automation systems and workflows built with **n8n**, **OpenAI**, **VAPI**, **Node.js**, and **GoHighLevel CRM** — designed for real estate operations, AI voice automation, and CRM intelligence.

All projects are sanitized (credentials removed) and documented for review.

---

## Projects

### 1. [REX AI CRM Assistant](./rex-ai-crm-assistant/)
> **Telegram + OpenAI GPT-4 + GoHighLevel CRM**

AI-powered assistant that lets agents query and interact with their CRM through natural language on Telegram. Maintains conversation memory and executes live CRM lookups via tool-calling.

**Stack:** n8n · Telegram · OpenAI · GoHighLevel API · LangChain Agent

---

### 2. [Personal AI Assistant](./personal-ai-assistant/)
> **Telegram + Gmail + Google Calendar + OpenAI**

Multi-tool AI assistant that reads/sends emails and manages calendar events through Telegram. Uses OpenRouter for LLM fallback and maintains window-based memory.

**Stack:** n8n · Telegram · OpenAI · OpenRouter · Gmail · Google Calendar

---

### 3. [AI Lease Generator](./ai-lease-generator/)
> **Telegram + OpenAI + GoHighLevel CRM**

Generates real estate lease agreements on demand via Telegram. AI agent gathers info conversationally, fetches live CRM data, and produces formatted documents.

**Stack:** n8n · Telegram · OpenAI GPT-4 · GoHighLevel API · LangChain Agent

---

### 4. [Cold Outreach System](./cold-outreach-system/)
> **GoHighLevel Webhook + Gmail + Google Sheets**

End-to-end outreach pipeline: GHL triggers the workflow when a contact enters a stage, logs to Sheets, sends a personalized Gmail, and tags the contact back in GHL.

**Stack:** n8n · GoHighLevel · Gmail · Google Sheets

---

### 5. [Email Warmup System](./email-warmup/)
> **DeepSeek AI + Multi-Sender SMTP + Scheduler**

Rotates across 8 sender accounts and 16 topic prompts, uses DeepSeek to generate unique emails every 3 hours, and distributes to a pool of receiver addresses to improve inbox deliverability.

**Stack:** n8n · DeepSeek API · SMTP (multi-account)

---

### 6. [Reply Tracker](./reply-tracker/)
> **Gmail + GoHighLevel CRM + Google Sheets**

Polls Gmail every minute for replies, matches senders to GHL contacts, tags them as replied, and automatically moves their opportunity to the correct pipeline stage.

**Stack:** n8n · Gmail · GoHighLevel API · Google Sheets

---

### 7. [GHL Live Dashboard](./ghl-dashboard/)
> **GoHighLevel API + n8n Webhooks + JavaScript Charts**

Custom real-time CRM dashboard served via n8n webhooks. Pulls pipeline and contact data from GHL on a schedule and renders interactive charts in the browser — no external BI tool needed.

**Stack:** n8n · GoHighLevel API · JavaScript · Webhook nodes

---

### 8. [Purple Cow AI Receptionist](./purple-cow-ai-receptionist/)
> **VAPI.ai + Node.js + Rex CRM + Railway**

Production AI voice receptionist that answers every inbound call to a real estate office 24/7 — no human operator needed. Greets callers, looks up live property listings from Rex CRM, matches agent names using fuzzy + phonetic search, transfers calls to the right agent's mobile, and automatically writes call notes and creates leads in Rex after every call.

**Stack:** VAPI.ai · Node.js · Express · Rex CRM API · Railway · Resend · GitHub

**Full codebase:** [verdeflors/purple-cow-receptionist](https://github.com/verdeflors/purple-cow-receptionist)

---

## About

Built and deployed by **Marc** — automation engineer focused on AI voice systems, CRM integrations, and real estate operations.

- All workflows run on a self-hosted n8n instance
- Production-tested and actively maintained
- Contact: vmarcelne@gmail.com
