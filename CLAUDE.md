# king west commons app — CODE ONLY (no project context here)

This folder is the **Netlify/iOS Lounge app** — deployable code only. It holds NO project
knowledge, agents, or tasks.

🔴 **The project brain lives at:** `~/Documents/KWC main project`
Open Claude **there**, not here — it has the shared `CLAUDE.md`, the 3 agents, `TASKS.md`, and
`PROJECT-SNAPSHOT.md`. From that session the engineer edits the files in this folder directly.

## What's here
- `king-west-commons-v3.html` — source of truth for the Lounge.
- `kwc-deploy/index.html`, `kwc-ios/www/index.html` — deploy copies (differ from the source ONLY in
  manifest delivery; keep in sync otherwise).

## Shipping
- Re-drag `kwc-deploy/` onto Netlify — **only with Disha's explicit OK.**
- Version control is automatic (LaunchAgent `com.kwc.autosave`) — never run git by hand.
- `gh` CLI is logged in as `dsareen02`.
