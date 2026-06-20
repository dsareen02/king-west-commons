# King West Commons — app folder

This folder is the **King West Commons** app, backed up to a private GitHub repo (`dsareen02/king-west-commons`).

## App files
- `king-west-commons-v3.html` — source of truth
- `kwc-deploy/index.html`, `kwc-ios/www/index.html` — deploy copies (keep in sync; they differ ONLY in manifest delivery: deploy/ios use static `<link rel="manifest">` + apple-touch-icon, source uses the injected-blob-manifest IIFE)

## Version control is AUTOMATIC — you do nothing
A background auto-save (macOS LaunchAgent `com.kwc.autosave`) commits and pushes every change in this folder to GitHub roughly every 90 seconds. **You do NOT need to run any git commands.** Just edit the files normally; every saved state is captured and recoverable on GitHub. Do not set up branches or ask Disha to manage folders.

If you want to mark a meaningful milestone with a clear message you MAY run `git commit -am "message"` — but it's optional; the auto-save already protects everything.

## Hard rules
- NEVER deploy to Netlify (drag of `kwc-deploy/`) without Disha's explicit OK.
- Disha is new to git/GitHub and must not be given any manual git/folder steps — keep all version-control work invisible to her.
- `gh` CLI is already logged in on this Mac as `dsareen02`; git push/pull work without prompts.

## 🔴 ALWAYS UPDATE THE GOOGLE SHEET (Drive) — mandatory for every task
- Canonical tracker = the Google Sheet "King West Commons — Task Tracker"
  (id `1nH08RJJDxaq2PSh-_UZrWPKvuAiyNhl92yZ0lFknXLM`, tab gid `1284780150`). `TASKS.md` in the
  **docs repo** (`dsareen02/king-west-commons-docs`) is the working mirror.
- Every task add/change/complete must end up in BOTH that Sheet and `TASKS.md` — the Sheet must
  never drift behind. If you have a Sheets write path, write directly; if not (the Drive connector
  is READ-ONLY today), output a copy-paste-ready row block labelled "🔴 PASTE INTO DRIVE SHEET"
  for Disha to paste. Keep IDs identical across the Sheet and `TASKS.md`.
- Full engineer conventions live in the docs repo's `CLAUDE.md`.
