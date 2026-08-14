# Reply Tracker (Gmail → GHL CRM Pipeline Automation)

Automatically detects email replies from leads, matches them to contacts in GoHighLevel CRM, tags them, and moves their opportunity to the correct pipeline stage — closing the loop on outreach without any manual work.

## What It Does

- Polls **Gmail every minute** for unread emails
- Parses sender email to identify the replying lead
- Looks up the contact in **GoHighLevel CRM**
- Adds a `replied` tag to the contact
- Finds the associated opportunity
- Moves the opportunity to the **"Replied"** pipeline stage
- Logs all activity to **Google Sheets**

## Tech Stack

| Tool | Role |
|---|---|
| n8n | Workflow orchestration |
| Gmail | Email polling (unread detection) |
| GoHighLevel API | Contact lookup + tagging + opportunity update |
| Google Sheets | Activity log |
| Schedule Trigger | Polls every 1 minute |

## How It Works

```
Schedule Trigger (every 1 min)
      ↓
  Gmail → Get unread emails
      ↓
  Parse sender email address
      ↓
  GHL API → Lookup contact by email
      ↓
  Add "replied" tag to contact
      ↓
  Find opportunity → Move to "Replied" stage
      ↓
  Log to Google Sheets
```

## Key Features

- Near real-time reply detection (1-minute polling)
- Automatically updates CRM stage — no manual pipeline management
- Paired with `reply-tracker-emailsender` for full send→reply→update loop
- Closes the outreach loop: send → track open → detect reply → update CRM
- Active in production

## Screenshot

> *Add workflow-canvas.png to screenshots/ folder*
