# Purple Cow AI Receptionist

A production-grade AI voice receptionist that answers inbound calls to a real estate office 24 hours a day, 7 days a week — fully automated, no human operator required.

**Full project repository:** [verdeflors/purple-cow-receptionist](https://github.com/verdeflors/purple-cow-receptionist)

---

## What It Does

The AI, named **Anna**, handles the entire call from greeting to transfer:

- Answers every inbound call instantly, 24/7
- Looks up property listings in real time from Rex CRM
- Identifies which agent a caller needs — by name, property, or enquiry type
- Transfers the call directly to the agent's mobile phone
- Falls back to the next available agent if the first doesn't answer
- Writes a detailed call note to Rex CRM after every call
- Creates a market lead and assigns it to the correct agent in Rex — automatically

Callers speak naturally. Anna handles the rest.

---

## Tech Stack

| Tool | Role |
|------|------|
| VAPI.ai | AI voice platform — speech-to-text, conversation logic, text-to-speech, call transfer |
| Node.js (Express) | Backend server — processes all tool calls from VAPI |
| Railway | Cloud hosting — auto-deploys on every GitHub push, runs 24/7 |
| Rex CRM API | Property listings, contact lookup, lead creation, call notes |
| Resend | Error alert emails when backend exceptions occur |
| GitHub | Source of truth for code and agent configuration |

---

## How It Works

```
CALLER DIALS OFFICE NUMBER
        ↓
VAPI answers — sends assistant-request to Railway backend
  Railway checks Rex CRM for caller's phone number
        ↓
Anna greets the caller
  "Hi, it's Anna from Purple Cow Real Estate..."
        ↓
Caller states their reason for calling
        ↓
Anna calls a tool (Railway processes the request)
  Property enquiry?    → /listing-lookup   → Rex CRM fetches listing + agent
  Asking for agent?    → /connect-agent    → agents.json fuzzy name match
  Appraisal request?   → /listing-lookup   → routes to appraisal specialist
  Wants a real person? → /transfer-human   → Office Reception
        ↓
Anna informs caller and initiates transfer
  VAPI calls /transfer → Railway confirms destination → VAPI dials agent mobile
        ↓
AGENT'S PHONE RINGS
  Answered → caller connected
  No answer → falls back to next agent or voicemail
        ↓
CALL ENDS — end-of-call processing (automatic)
  Rex contact looked up or created
  Call summary fetched from VAPI
  Call note written to Rex contact record
  Market lead created and assigned to agent in Rex
  Call log entry saved
```

---

## Key Features

### Fuzzy + Phonetic Agent Name Matching
When a caller asks for an agent by name, the system matches against the full agent list using:
- Exact and substring matching (normalised)
- Token-level matching (handles word order and partial names)
- Phonetic matching via Metaphone (catches mishearings — "Christian" matches "Kristian", "Waldorf" matches "Waldorff")
- Alias support — common mishearings pre-configured per agent

If multiple agents match (e.g. two Nicoles), Anna asks the caller to clarify. If no match after two attempts, Anna falls back to Office Reception.

### Two Routing Systems Working Together
- **Rex CRM** handles property enquiries — Anna fetches the listing agent live from Rex on every call. No configuration needed.
- **agents.json** handles everything else — direct agent requests, appraisal routing, and fallback. One file, plain JSON, no code knowledge required to update.

### Intelligent Appraisal Routing
- Sales appraisal requests → routed to the designated sales appraisal agent
- Rental appraisal requests → routed to the rental BDM
- Caller has a preferred agent → `select-agent` lets them choose from the available list

### Returning Caller Recognition
The system checks Rex CRM on every call before Anna even speaks. If the caller is already in Rex with an assigned agent, that agent is pre-loaded as the routing destination before the conversation begins.

### Automatic Rex CRM Post-Call Processing
After every call, the backend:
1. Looks up or creates the Rex contact by phone number
2. Fetches the AI-generated call summary from VAPI
3. Writes a structured call note to the Rex contact record (includes call summary, enquiry type, property mentioned, and a direct link to the VAPI call recording)
4. Creates a market lead linked to the enquiry
5. Assigns the contact to the relevant agent in Rex

### Always-On Fallback Chain
If the primary agent is unavailable, the system falls back through a configured chain. Last resort is always Office Reception — no call ever goes unanswered.

---

## Agent Configuration

All agent routing is controlled by a single JSON file — `agents.json` — in the repository root. Non-technical staff can add, remove, or update agents by editing this file directly on GitHub. Changes go live automatically within ~2 minutes via Railway auto-deploy.

No code knowledge required for day-to-day management.

---

## Deployment

- Hosted on **Railway** — auto-deploys on every push to the `main` branch
- Zero-downtime deploys — existing server stays live during rebuild
- Environment variables stored securely in Railway (API keys never in code)
- Startup cache warm-up — pre-loads active listings and agent data from Rex on boot for faster call response times
