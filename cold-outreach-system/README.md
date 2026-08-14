# Cold Outreach System (GHL + Gmail + Google Sheets)

An automated end-to-end cold email outreach pipeline that triggers from GoHighLevel, logs to Google Sheets, sends personalized emails, and tags contacts — all without manual intervention.

## What It Does

- Receives contact data via **GHL webhook** when a contact enters a pipeline stage
- Parses and validates contact info
- Logs each outreach attempt to **Google Sheets** for tracking
- Sends a personalized **Gmail** email to the contact
- Tags the contact back in **GoHighLevel** as "outreach sent"
- Handles routing logic (skip if already contacted, etc.)

## Tech Stack

| Tool | Role |
|---|---|
| n8n | Workflow orchestration |
| GoHighLevel Webhook | Trigger — contact enters stage |
| Google Sheets | Outreach log / CRM tracker |
| Gmail | Email delivery |
| GoHighLevel API | Contact tagging |

## How It Works

```
GHL Webhook (contact enters stage)
      ↓
  Parse contact data
      ↓
  Log to Google Sheets
      ↓
  Send Gmail (personalized)
      ↓
  Tag contact in GHL → "outreach-sent"
      ↓
  Respond to webhook (200 OK)
```

## Key Features

- Fully automated — zero manual steps after setup
- Google Sheets provides a live audit log of all outreach
- Webhook response included — won't leave GHL hanging
- Wait nodes prevent rate-limit issues on bulk triggers
- Active in production

## Screenshot

> *Add workflow-canvas.png to screenshots/ folder*
