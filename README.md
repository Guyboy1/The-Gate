# The Gate

An additional layer of protection for iPhone Screen Time. Instead of simply entering a passcode, you must first explain your reasons in a chat before you can unlock your short-form video apps. And as the day progresses, the process becomes increasingly challenging.

**This works exclusively on the iPhone** and only in conjunction with the free app [Foqos](https://www.foqos.app) (open source: [github.com/awaseem/foqos](https://github.com/awaseem/foqos)), which handles the actual blocking and unblocking via Screen Time. The Gate does not access Screen Time directly—it is the conversation you must have before Foqos lets you back in.

Everything runs entirely within your own browser. There is no server, no user account, and no data leaves your iPhone—with the exception of the messages you send to your chosen AI model (via your own [OpenRouter](https://openrouter.ai) API key, which also never leaves your browser).

AI Warning: AI was used in the creation of this. This does not mean the entire project is AI. All the planning and features where described by me, and either roughly coded or coded in pseudocode before submitted into AI to improve. 

---

## Setup

### 1. Install and configure Foqos

Download the app from the App Store: **[Foqos on the App Store](https://apps.apple.com/app/foqos/id6736793117)** (or search for "Foqos"). Then, set up a blocking profile for your short-form video apps (TikTok, Instagram Reels, YouTube Shorts, etc.) as follows:

- **Blocking strategy:** `QR Code` – Foqos scans a code to start or end the block. The Gate does not use the QR code directly in day-to-day operation (that is handled by the shortcuts described below). However, the QR code strategy enables the **Pause** feature in Foqos, which you will need. - **Pauses:** Enable this feature and set the pause duration to "unlimited" or "no time limit" (an "infinite" pause that does not expire automatically). A pause interrupts the block without ending the entire session. Since no fixed duration is set within Foqos, the block remains paused until it is actively resumed. This is handled by the Shortcuts—not by a timer inside Foqos.
- **"Allow unlocking only via the Foqos app" – disable this option.** Depending on the version, this setting might be labeled *Disable Background Stops* or be part of a *Strict Mode* restriction. If enabled, it prevents anything outside of the Foqos app itself—including a Shortcut—from ending a block or pause. Since The Gate relies entirely on Shortcuts running in the background, this option must be disabled. Otherwise, nothing will happen when you tap the unlock link in The Gate.

Foqos is updated quite frequently, and the names of settings sometimes change between versions. If the labels you see don’t match exactly, look for the equivalent options. The key requirements are the QR code strategy, enabled pauses with no automatic expiration, and permission for background/Shortcut-based actions.

### 2. Installing the two Shortcuts

These Shortcuts are triggered by The Gate to start or end a pause once access is granted to you. The 10-minute Shortcut initiates and maintains a pause, while the 1-minute Shortcut enables the quick-unlock option. Open both links on your iPhone and tap **Add Shortcut**:

- **Pause for 10 min** (a standard release): https://www.icloud.com/shortcuts/134b3f49e7384faf816cc950cc245c9e
- **Pause for 1 min** (a quick-unlock option, for instance, to reply to a single message): https://www.icloud.com/shortcuts/b40ceadb114e41f781b73629f1f654ca

**Important:** The Gate triggers these shortcuts by their exact names; it does not automatically select a matching shortcut.

After adding them, open the **Shortcuts** app and verify that they are named exactly as follows:

- `Pause Focus` – for the 10-minute shortcut
- `Pause Focus One Min` – for the 1-minute shortcut

If any of the shortcuts were imported with a different name, rename them (long-press → Rename) so that the names match exactly. Otherwise, The Gate will be unable to locate the shortcut when you tap the link, resulting in an error.

### 3. Create an OpenRouter API Key

The Gate requires an AI model to negotiate with you. It uses [OpenRouter](https://openrouter.ai) for this purpose. OpenRouter provides a single API key that works with models from many different providers. You are billed based on your usage.

1. Go to **[openrouter.ai](https://openrouter.ai)** and register (you can sign up using Google or GitHub). 2. Go to **[openrouter.ai/credits](https://openrouter.ai/credits)** and add a small amount of credit. Even just a few dollars will go a long way when using this app.
