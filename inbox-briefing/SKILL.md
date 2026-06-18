---
name: inbox-briefing
description: >
  Use when the user wants a daily briefing, inbox triage, email summary, or calendar check.
  Triggers on: "check my email", "what's in my inbox", "triage my email", "what do I have today", 
  "daily briefing", "morning briefing", "what's on my calendar", "what meetings do I have", 
  "inbox zero", "label my emails", "what's coming up", "summarize my inbox", "email digest",
  "what needs my attention", "any important emails", or "check my schedule".
---

# Inbox Briefing Skill

Produce a daily briefing by triaging Gmail from the past 24 hours and surfacing Google Calendar events for the next 48 hours. Output a clean, scannable digest the user can act on immediately.

Requires Gmail and Google Calendar access through the host app, connector, or MCP server.

---

## Step 1 — Fetch Data (run both in the same turn)

**Gmail:** Retrieve all emails from the past 24 hours.
- Use the Gmail MCP `list_emails` or `search_emails` tool with a query like `after:YYYY/MM/DD` (yesterday's date).
- Fetch enough metadata per email to classify: sender, subject, snippet, labels, read/unread status.
- Cap at 50 emails. If there are more, note the overflow.

**Google Calendar:** Retrieve all events from now through 48 hours from now.
- Use the Google Calendar MCP to list events in that window.
- Capture: event title, start time, end time, attendees (if any), location/link, description snippet.

---

## Step 2 — Triage Emails into 4 Buckets

Classify each email into exactly one category. Apply these rules strictly:

| Label | Criteria |
|-------|----------|
| 🔴 **FOCUS** | Requires deep reading or a decision. Direct messages to you, client/contract matters, anything with your name in the body, legal/financial, escalations. |
| ⚡ **ACTION** | Requires a quick response or task. Meeting invites, requests with clear asks, time-sensitive follow-ups, form submissions, calendar changes. |
| 🔇 **NOISE** | No action needed, but not trash. Newsletters, notifications, automated alerts, CC'd threads you don't own, social updates. |
| 🗑️ **DELETE** | Zero value. Pure promotional spam, unsubscribe confirmation, duplicate notifications, mass marketing with no relevance. |

**Triage heuristics:**
- If the sender is a real person (not no-reply/noreply/mailer-daemon), lean toward FOCUS or ACTION.
- If the subject contains "RE:" or "FWD:" and it's from a real person, likely ACTION.
- Newsletters and Substack → NOISE.
- Amazon, promo codes, "Deal of the day" → DELETE.
- Automated CI/CD, build alerts, monitoring pings → NOISE (unless it's a failure, then ACTION).
- Calendar invites from real people → ACTION.

---

## Step 3 — Format the Briefing

Output the briefing in this exact structure. Keep it tight — one line per email max unless FOCUS items need context.

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📬 INBOX BRIEFING — [Day, Date, Time]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📅 CALENDAR — NEXT 48 HOURS
[If no events: "Nothing scheduled."]

  ▸ [Time] — [Event Title] ([Duration])
    [Attendees if >1 person] | [Link/Location if present]

  ▸ [Time] — [Event Title]
  ...

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📧 EMAIL TRIAGE — LAST 24 HOURS
[X emails processed | X FOCUS · X ACTION · X NOISE · X DELETE]

🔴 FOCUS ([count])
  • [Sender Name] — [Subject] | [1-line context if needed]
  ...

⚡ ACTION ([count])
  • [Sender Name] — [Subject] | [Quick note on the ask]
  ...

🔇 NOISE ([count])
  • [Sender/Source] — [Subject]
  ...

🗑️ DELETE ([count])
  • [Sender/Source] — [Subject]
  ...

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
💡 TOP PRIORITY
[1-3 sentence synthesis: What needs attention first, any conflicts between calendar and email, any time-sensitive items.]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## Step 4 — Offer Follow-Up Actions

After the briefing, offer these one-liner options:

```
What do you want to do next?
  → Draft replies for ACTION items
  → Move NOISE to a label/archive
  → Show full email for any FOCUS item
  → Re-triage any email you disagree with
```

Do not execute any of these automatically — wait for the user to pick one.

---

## Notes & Edge Cases

- **No emails in 24hrs:** Say so, then still show calendar.
- **No calendar events:** Say so, still show email triage.
- **Ambiguous emails:** When in doubt between FOCUS and ACTION, use FOCUS. Better to over-flag than under-flag.
- **Thread deduplication:** If multiple emails are from the same thread, group them as one entry under the highest-priority label they collectively earn.
- **Privacy:** Never reproduce full email body text. Snippet + subject + sender is enough.
- **Time zones:** Use the user's local time (infer from calendar event times or default to Pacific).
- **Newsletters the user clearly cares about** (e.g., relevant industry content they subscribe to intentionally): use NOISE, not DELETE.
