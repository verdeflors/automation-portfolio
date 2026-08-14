# GHL Live Dashboard (CRM Data Visualization)

A custom real-time dashboard that pulls live data from GoHighLevel CRM and renders charts and metrics on a web page — built entirely with n8n webhooks and vanilla JavaScript.

## What It Does

- Serves a **live HTML dashboard page** via n8n webhook
- Pulls contacts, opportunities, and pipeline data from **GoHighLevel API**
- Syncs CRM data on a schedule and caches it in n8n
- Renders **interactive charts** (pipeline stages, conversion rates, activity)
- No external dashboard tool needed — fully self-hosted

## Tech Stack

| Tool | Role |
|---|---|
| n8n | API orchestration + webhook server |
| GoHighLevel API | CRM data source |
| JavaScript (Code node) | Data transformation + chart rendering logic |
| HTTP Request nodes | GHL API calls |
| Webhook nodes | Serve dashboard HTML + chart data endpoints |

## Workflows

This folder covers 3 connected workflows:

| Workflow | Role |
|---|---|
| `Rex → GHL Dashboard Sync` | Scheduled pull of CRM data into n8n |
| `Rex → GHL Dashboard Page` | Webhook that serves the HTML dashboard |
| `Rex → GHL Dashboard Charts` | Webhook that returns JSON chart data |

## How It Works

```
Schedule Trigger
      ↓
  GHL API → Fetch contacts + opportunities
      ↓
  Transform + store in n8n

Browser hits dashboard URL
      ↓
  Webhook → Serve HTML page
      ↓
  Page JS fetches /charts endpoint
      ↓
  Charts webhook → returns JSON data
      ↓
  Render charts in browser
```

## Key Features

- Zero external dashboard tools — n8n serves everything
- Modular: sync, page, and charts are separate workflows for maintainability
- Live data — syncs on schedule, always current
- Active in production

## Screenshot

> *Add workflow-canvas.png to screenshots/ folder*
