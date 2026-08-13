# The Gate

A friction layer for iPhone Screen Time. Instead of a code you can just type in, unlocking your
short-form video apps means making your case in a chat first — and the further into the day you
go, the harder that gets.

**This only works on iPhone**, and only alongside the free app [Foqos](https://www.foqos.app)
(open source: [github.com/awaseem/foqos](https://github.com/awaseem/foqos)), which does the actual
Screen Time blocking/unblocking. The Gate doesn't touch Screen Time itself — it's the conversation
you have before Foqos will let you back in.

Everything runs entirely in your own browser. There's no backend, no account, and no data leaves
your phone except the messages you send to the AI model you choose (via your own [OpenRouter](https://openrouter.ai)
key, which also never leaves your browser).

---

## Setup

### 1. Install and configure Foqos
Get it from the App Store: **[Foqos on the App Store](https://apps.apple.com/app/foqos/id6736793117)**
(or search "Foqos"). Then set up one blocking profile for your short-form apps (TikTok, Instagram
Reels, YouTube Shorts, etc.) like this:

- **Blocking strategy:** `QR Code` — Foqos will scan a code to start/stop the block. The Gate
  doesn't actually use the QR scan itself day-to-day (that's what the Shortcuts below are for),
  but QR Code is the strategy that also unlocks Foqos's **Breaks** feature, which is what you want.
- **Breaks:** turn this **on**, and set the break duration to unlimited/no-limit (an "infinite"
  break, i.e. one that doesn't auto-expire on its own). A break pauses the block without ending
  the whole session — with no fixed length on Foqos's side, it stays paused until something
  actively re-locks it, and that's the Shortcuts' job, not a timer inside Foqos.
- **"Only allow unblocking from the Foqos app" — turn this off.** This is usually phrased as
  something like *Disable Background Stops* or a *Strict Mode* restriction, and when it's on, it
  blocks anything outside the Foqos app itself — including a Shortcut — from ending a block or
  break. Since The Gate works entirely through Shortcuts running in the background, this has to
  be off, or tapping the unlock link in The Gate will do nothing.

Foqos updates fairly often and does relabel settings between versions, so if none of these are
worded exactly like this in your version, look for the nearest equivalent — the important part is
QR Code strategy, breaks enabled with no auto-expiry, and background/Shortcut stops allowed.

### 2. Install the two Shortcuts
These are what The Gate actually triggers to start/end a break once it grants you access — the
10-minute one starts a break and lets it run, the 1-minute one is the quick-unlock fast path.
Open both links on your iPhone and tap **Add Shortcut**:

- **Pause 10 min** (a normal gate opening): https://www.icloud.com/shortcuts/134b3f49e7384faf816cc950cc245c9e
- **Pause 1 min** (the "quick unlock" fast path, for things like replying to one text): https://www.icloud.com/shortcuts/b40ceadb114e41f781b73629f1f654ca

**Important:** The Gate opens these by exact name, not by picking whichever shortcut looks right.
After adding them, open the **Shortcuts** app and confirm they're named exactly:
- `Pause Focus` — for the 10-minute one
- `Pause Focus One Min` — for the 1-minute one

If either imported under a different name, rename it (long-press → Rename) to match exactly —
otherwise tapping the link in The Gate will silently fail to find the shortcut.

### 3. Get an OpenRouter API key
The Gate needs an AI model to actually negotiate with you — that comes from
[OpenRouter](https://openrouter.ai), which gives you one key that works across many providers'
models, billed as you go.

1. Go to **[openrouter.ai](https://openrouter.ai)** and sign up (Google/GitHub login works).
2. Go to **[openrouter.ai/credits](https://openrouter.ai/credits)** and add a small amount of
   credit — a few dollars covers a very long time at this app's usage level, since it uses cheap,
   fast models.
3. Go to **[openrouter.ai/keys](https://openrouter.ai/keys)**, click **Create Key**, name it
   whatever you like, and copy it. It starts with `sk-or-v1-...`.
4. Keep this tab open or save the key somewhere for a moment — you'll paste it into The Gate in
   step 5.

You're never charged a subscription; it's pay-as-you-go against the credit you add.

### 4. Open The Gate and save it to your Home Screen
Open this page on your iPhone in **Safari**:

**[→ Launch The Gate](https://guyboy1.github.io/The-Gate/)**

Then tap the **Share** button → **Add to Home Screen**. This makes it behave like a real app —
full screen, its own icon, no browser bar.

### 5. Add your API key
Open The Gate from your Home Screen icon, tap the **gear icon** (top right), and paste your
OpenRouter key into the **OpenRouter API key** field at the top of Settings. It's saved only in
your phone's local browser storage — it isn't sent anywhere except directly to OpenRouter when
you chat with the gate.

That's it — you're set up. The gate opens 10-minute windows for the first few times you ask each
day; past that, it starts asking more of you before it lets you through.

---

## Notes

- If you ever want a different AI model behind the gate, or a fresh key, everything's in Settings.
- Clearing your browser data will reset your key, your theme preferences, and today's log — it
  won't affect Foqos or your Shortcuts, those are separate iOS-level things.
- This is a personal project, shared as-is. There's no support channel — if something breaks,
  you're welcome to fork it and fix it yourself.
