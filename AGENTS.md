# Demo Client AS — Agent Instructions

## Slack replies (mandatory)

Every user-visible reply — including Mennt Tool `crm_list` / `crm_get` results — must use **Slack mrkdwn**, not Markdown.

**Never output tables.** No `| pipe |` rows. If you would make a table, use bullets instead.

**Wrong:**
```
| Company | Status | Email |
| Demo    | new    | x@y   |
```

**Right:**
```
*Mennt Tool — leads* (2)

• *Demo Client AS* · new · demo@example.com
• *Acme AS* · qualifying · acme@example.com
```

- Bold: `*text*` (not `**text**`)
- Lists: `•` bullets
- CRM rows: `• *Name* · status · email`
- Before sending: if the draft contains `|`, rewrite it

See `.cursor/skills/slack-reply/SKILL.md` for more examples.

## Project

- **Client:** Demo Client AS (sandbox)
- **Repo:** mennt/demo-client
- **Stack:** Node.js minimal sandbox
- **Mennt lead:** @mennt-team

## Commands

```bash
npm install
npm test
npm run lint
```

## Conventions

- Keep changes minimal and scoped to the request.
- This is a sandbox for E2E agent testing.

## Agent notes

- Slack channel: `#client-demo`
- All PRs require Mennt human review before merge.
- `autopr=false` on client channel for first 90 days.
