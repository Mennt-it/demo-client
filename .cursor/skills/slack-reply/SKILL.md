---
name: slack-reply
description: Format agent replies for Slack (mrkdwn). Use whenever responding in Slack via @cursor — triage, CRM results, quotes, client channels. Never use tables or pipe characters.
---

# Slack reply formatting

The Cursor Slack bot posts **plain text with Slack mrkdwn**. It cannot render GitHub Markdown or tables.

## Hard rules (Slack threads)

1. **Never use tables** — no `| col | col |` rows, no ASCII grids, no aligned columns.
2. **Never use `**double asterisks**`** — use `*single asterisks*` for bold.
3. **Never use `#` headings** — use `*Section title*` on its own line.
4. **Use `•` bullets** — not `-` or numbered markdown lists for short replies.
5. **Keep it short** — 5–15 lines; cap CRM lists at 10 records, then offer to filter.

If you would normally make a table, use **one record per block** (see below).

## Format cheatsheet

- Bold: `*text*`
- Italic: `_text_`
- Code: `` `id-or-command` ``
- Link: `<https://github.com/org/repo|repo>` or bare URL
- Blank line between records

## CRM / Mennt Tool — `crm_list` and `crm_get`

**Wrong (shows broken pipes in Slack):**

```
| Company | Status | Email |
|---------|--------|-------|
| Demo    | new    | x@y   |
```

**Right — compact (≤5 records):**

```
*Mennt Tool — leads* (3)

• *Demo Client AS* · new · demo@example.com
• *Acme AS* · qualifying · acme@example.com

_Say which lead to open or convert._
```

**Right — detail (6+ fields or one record):**

```
*Lead: Demo Client AS*

• Status: new
• Email: demo@example.com
• Source: slack
• ID: `a1b2c3d4-…`

_Next:_ convert to opportunity or update status.
```

**Right — many records (truncate):**

```
*Mennt Tool — opportunities* (12 total, showing 5)

• *Demo bakery website* · proposal · 45 000 NOK
• *Acme redesign* · qualifying · —
• *Nordic SaaS* · won · 120 000 NOK
• *Beta pilot* · lost · —
• *Internal tooling* · new · —

_Reply with a filter (status, company) to see more._
```

Use `·` (middle dot) between short fields on one line. Put long text on its own `•` line.

## Triage

```
*Triage*
• Type: bug
• Repo: mennt/demo-client
• Scope: S
• Summary: Fix welcome typo in README
• Next: `@cursor agent fix Welcom→Welcome in demo-client`
• Mennt review required: yes
```

## Quotes (Phase 6)

```
*Estimate*
• Task: Fix login redirect
• Scope: M
• Compute: 2 000–4 000 NOK
• Your price: 4 000–8 000 NOK
Reply *approve* in this thread to proceed.
```

## PR / agent completion summaries

```
*Done*
• Branch: `fix/readme-typo`
• PR: <https://github.com/Mennt-it/demo-client/pull/3|#3>
• Changed: README welcome line

Mennt review required before merge.
```

## End every client-facing reply with

`Mennt review required before merge.` (when code/PR involved)

## When in doubt

Plain sentences beat structured docs. **If your draft contains `|` characters in a row, rewrite it.**
