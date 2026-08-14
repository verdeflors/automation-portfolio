# Email Warmup System (AI-Generated Multi-Sender)

An automated email warmup system that rotates across 8 sender accounts, generates unique AI-written emails, and sends them to a pool of receiver addresses on a schedule — improving deliverability and inbox placement.

## What It Does

- Runs on a **schedule every 3 hours**
- Randomly selects 1 of **8 sender accounts** and 1 of **16 topic prompts**
- Uses **DeepSeek AI** to generate a unique, natural-sounding 10–60 word email
- Routes to the correct **SMTP server** for the selected sender
- Sends to **3–6 randomly selected receiver addresses** per run

## Tech Stack

| Tool | Role |
|---|---|
| n8n | Workflow orchestration + scheduling |
| DeepSeek API | AI email content generation |
| SMTP (multi-account) | Email delivery per sender |
| Schedule Trigger | Runs every 3 hours automatically |
| Switch node | Routes to correct SMTP per sender |

## How It Works

```
Schedule Trigger (every 3h)
      ↓
  Pick random sender (1 of 8) + topic (1 of 16)
      ↓
  DeepSeek → generate unique email body
      ↓
  Switch → route to correct SMTP
      ↓
  Send to 3-6 random receivers
```

## Key Features

- 8 rotating senders × 16 topics = high variation, avoids spam pattern detection
- AI-generated content — never the same email twice
- Lightweight per-run (3–6 emails) mimics real human sending behavior
- Fully autonomous — runs 24/7 without intervention
- Active in production

## Screenshot

> *Add workflow-canvas.png to screenshots/ folder*
