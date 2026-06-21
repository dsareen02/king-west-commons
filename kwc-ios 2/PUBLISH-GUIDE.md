# King West Commons — App Store Publishing Guide

You have: an Apple Developer account ✅ and the app live on Netlify ✅.
This guide takes the same app and ships it to the App Store.

---

## Part 0 — One-time setup on your Mac (~30 min, mostly downloads)

1. **Xcode** — install free from the Mac App Store (it's big, start it first).
   Open it once and accept the license / let it install components.
2. **Node.js** — install the LTS from https://nodejs.org if you don't have it
   (check: open Terminal, type `node -v`).
3. **CocoaPods** — in Terminal: `sudo gem install cocoapods`
   (if that fights you, `brew install cocoapods` works too).

## Part 1 — Build the native project (~5 min)

Open Terminal, `cd` into this `kwc-ios` folder, then:

```
npm install
npx cap add ios
npx cap open ios
```

That creates the iOS app around the `www/` folder (your exact app) and opens it in Xcode.

## Part 2 — Sign it in Xcode (~5 min)

In Xcode, click **App** in the left sidebar → **Signing & Capabilities** tab:

1. Check **"Automatically manage signing"**.
2. **Team**: pick your Apple Developer team.
3. **Bundle Identifier**: `ca.kingwestcommons.app` (already set — change only if Apple says it's taken).

Plug in your iPhone (or pick a Simulator) and press ▶ to run it — this is your first real native build. Test everything.

## Part 3 — Create the app record in App Store Connect (~10 min)

1. Go to https://appstoreconnect.apple.com → **My Apps** → **+** → **New App**.
2. Platform: iOS · Name: **King West Commons** · Language: English (Canada)
   · Bundle ID: select `ca.kingwestcommons.app` · SKU: `kwcommons1`.
3. Fill the required metadata:
   - **Privacy Policy URL** (required): a page on kingwestcommons.ca describing what you collect (name/alias, chat messages). Bettermode can host this page.
   - **Description, keywords, support URL** (kingwestcommons.ca works).
   - **Screenshots**: run the app in Xcode's iPhone 15 Pro Max simulator, ⌘S saves screenshots; you need the 6.7" set (and 5.5" can reuse scaled). Take: lounge, a conversation card, the chat circle, The Commons tab.
   - **App Privacy** questionnaire: you collect "Name" + "Other user content" (chat), linked to user, not used for tracking.
4. Age rating questionnaire: the chat means "Unrestricted Web Access"? — answer NO (embedded pages are your own community); social features → 12+ typically.

## Part 4 — Upload (~10 min)

In Xcode:

1. Top bar device selector → **Any iOS Device (arm64)**.
2. Menu **Product → Archive**.
3. When the Organizer window opens → **Distribute App** → **App Store Connect** → **Upload** → accept defaults.
4. Back in App Store Connect, the build appears under **TestFlight** in ~15 min.

## Part 5 — TestFlight first (recommended), then review

- **TestFlight**: add yourself + friends as internal testers — instant install on phones, no review. Run the beta here for a week.
- **Submit for review**: in App Store Connect → your app → select the build → **Submit for Review**. Typical wait: 1–3 days.

### Review notes to include (avoids the common rejection)
In "App Review Information" notes, write:
> The core experience is an interactive social lounge (canvas game: walk, chat, join conversations) built natively into the app. Community pages (The Commons, Pass Along, Directory) are first-party pages from our own community platform at kingwestcommons.ca, not third-party web content. No account is required to try the lounge.

### Honest risk flags
- **Guideline 4.2 (minimal functionality)**: webview-heavy apps get flagged. The lounge being the home tab is your defence — keep it that way.
- **Demo bots**: if reviewers see "DEMO ROOM · regulars are bots", that's fine (it's honest), but wiring Supabase before submission makes the app real — strongly recommended.
- **Sign in**: Bettermode pages will ask reviewers to log in. Provide a **demo account** (email+password) in App Review Information.

## Updating the app later
Web (Netlify) updates are instant. For the App Store version: replace files in `www/`, then `npx cap sync ios`, Archive, Upload, submit. (Later we can add live-update tooling so the store app pulls web updates automatically.)
