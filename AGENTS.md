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

## Mennt Tool CRM (MCP only — never code)

**Mennt Tool** is our CRM accessed via **MCP tools** (`crm_list`, `crm_get`, `crm_create`, …). It is **not** this repo and **not** the `mennt-tool` GitHub repo.

For requests like "list leads", "show opportunities", "create lead":

1. Use **Mennt Tool MCP** — call `crm_list` with `entity: leads` (or the right entity).
2. **Do not** write code, open PRs, or explore `mennt-tool` / `AgentToolsService`.
3. **Do not** implement missing features — this is a **read/query** task unless the user explicitly asks for code in **this** repo (`demo-client`).
4. If Mennt Tool MCP tools are **not** in your tool list: reply that MCP is unavailable and ask Mennt to check Dashboard → Integrations & MCP. **Stop** — do not fall back to coding.

**Slack prompt tip:** Avoid the phrase "in Mennt Tool" — Cursor may route to the wrong `mennt-tool` repo. Say `list leads` or `list leads via MCP`.

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
