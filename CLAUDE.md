# King West Commons — working rules for EVERY Claude session

This folder is the **King West Commons** app, under git (private GitHub: `dsareen02/king-west-commons`).
Many Claude sessions edit this app. To stop sessions from overwriting each other, **every session that edits app files MUST use the branch workflow via the `./kwc` helper. Never edit `main` directly.**

## App files
- `king-west-commons-v3.html` — source of truth
- `kwc-deploy/index.html`, `kwc-ios/www/index.html` — deploy copies (keep in sync; they differ ONLY in manifest delivery: deploy/ios use static `<link rel="manifest">` + apple-touch-icon, source uses the injected-blob-manifest IIFE)

## Required workflow — use `./kwc` (it wraps git + GitHub)
1. **Before editing anything:** `./kwc start <short-name>`  (e.g. `./kwc start build-004`)
   - Puts you on your OWN branch off the latest `main`. If it refuses due to unsaved changes, another session is mid-edit → STOP and tell Disha.
2. **After a verified-good change:** `./kwc save "what you changed"`
   - Commits, pushes, and opens a pull request automatically.
3. **When Disha approves shipping it:** `./kwc ship`
   - Merges your branch into `main`. GitHub checks for conflicts; nothing is silently overwritten.

If any step reports a **MERGE CONFLICT**, do NOT force anything — report it to Disha. Nothing is lost; a conflict just needs a human decision.

## Hard rules
- NEVER commit straight to `main` — it is protected on GitHub (direct pushes are rejected).
- Plan-only / strategy / docs sessions that don't touch app files: do nothing with git.
- NEVER deploy to Netlify (drag of `kwc-deploy/`) without Disha's explicit OK.
- Disha is new to git — never ask her for credentials; the `gh` CLI is already logged in on this Mac as `dsareen02`.
- Only ONE session should edit the app at a time unless each is in its own git worktree.
