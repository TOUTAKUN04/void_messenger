# VOID Releases

Official APK releases for **VOID Messenger**, a privacy-first, end-to-end encrypted messaging application for Android.

> This repository is dedicated exclusively to distributing official, signed VOID Messenger release builds. The application source code is maintained separately.

**Latest Version:** v3.1.5  
**Last Updated:** 7 November 2026

---

## Download

**Latest Release: [v3.1.5](https://github.com/TOUTAKUN04/void_messenger/releases/latest)**

**APK:** `void_release_v3.1.5.apk`

Download directly from our official website:

**[void.toutakun04.qzz.io](https://void.toutakun04.qzz.io)**

[All Releases](https://github.com/TOUTAKUN04/void_messenger/releases)

---

## Installation

1. Download the latest APK from the [Releases](https://github.com/TOUTAKUN04/void_messenger/releases) page.
2. On your Android device, enable installation from unknown sources:
   - Settings → Apps → Special app access → Install unknown apps.
3. Open the downloaded APK and follow the installation instructions.
4. Launch VOID and sign in using Google or email.

**Minimum Android version:** Android 8.0 (API 26)

---

## Verifying the APK

All official releases are signed using the VOID release keystore.

Verify the APK signature using Android's `apksigner` utility:

```bash
apksigner verify --print-certs void_release_v3.1.5.apk
```

The certificate SHA-1 fingerprint should match the fingerprint published on the official website.

Always download VOID from official distribution channels.

---

## What is VOID?

VOID is an end-to-end encrypted messaging application built around one principle:

**Your conversations belong to no one.**

Messages are encrypted directly on your device before transmission. The server handles delivery without needing access to message content.

### Core Principles

- **End-to-End Encryption** — EC P-256 and AES-256-GCM encryption, with keys protected through Android Keystore.
- **No Phone Number Required** — Sign in using Google or email.
- **Privacy First** — No advertising analytics or tracking.
- **Temporary Message Queuing** — Undelivered encrypted messages are queued for delivery and removed from the server queue after successful delivery.
- **Encrypted Group Messaging** — Group conversations with per-member key delivery.
- **Minimal Infrastructure** — Built using Cloudflare Workers, Supabase and Backblaze B2.

---

## Features

| Feature | Status |
|---|---|
| 1:1 E2EE Messaging | ✅ |
| Group Messaging (E2EE) | ✅ Beta |
| Voice Messages | ✅ |
| File Attachments | ✅ |
| Media Sharing | ✅ |
| Message Reactions | ✅ |
| Reply to Messages | ✅ |
| Chat Wallpapers | ✅ |
| Read Receipts | ⚠️ Temporarily disabled in v3.1.5 |
| Voice & Video Calls | ✅ Beta |
| Contacts Page | ✅ |
| In-App Bug Reporting | ✅ |
| Change Display Name | ✅ |
| Account Deletion | ✅ |
| Google & Email Sign-in | ✅ |
| No Phone Number Required | ✅ |
| AXIOM AI Chat | ✅ |
| AXIOM Voice Transcription | ✅ |
| Online Presence | ✅ |

---

## Release Channels

VOID maintains two release channels:

| Channel | Description |
|---|---|
| `beta` | Active development builds. Features may be experimental and occasional bugs are expected. |
| `stable` | Production-ready releases intended for general use. |

**Latest documented version:** v3.1.5

---

## Changelog

### v3.1.5 Reliability, Delivery & AXIOM Uptime

**✨ Highlights**

- **Resilient Push Notifications** — FCM tokens now synchronize through the API worker using a mutex and exponential-backoff retry. Tokens are persisted and retried automatically after timeouts or cold starts, preventing notifications from silently stopping.
- **Deleted Chat Recovery** — New messages in deleted 1:1 chats now restore the conversation. Re-invited groups also clear their tombstones immediately.
- **Realtime Delivery Hardening** — Added WebSocket ping/pong auto-responses for hibernated connections, instant-delivery checks, and conflict-safe message insertion with client UUID deduplication.

**🤖 AXIOM AI**

- Added multi-provider fallback:
  - Gemini
  - Groq (3 free models)
  - Cloudflare Workers AI
  - Graceful fallback
- AXIOM can continue responding when an individual provider reaches its daily usage limit.
- Improved web search resilience — failed searches no longer block responses.
- Added Supabase server-side timeouts:
  - 20 seconds
  - 45 seconds
  - 60 seconds, depending on request size.
- Requests now return clean errors instead of hanging indefinitely.

**🛠 Bug Fixes**

- Restored generic friend-request notifications without requester names.
- Fixed group member lookups including deleted groups.
- Standardized notification handling for archived chats.
- Removed an unnecessary archived-chat check from the notification pipeline.

**🔒 Privacy**

- Message notifications never include message content.

**⚠️ Changes**

- Read receipts are temporarily disabled in this build.
- Local read state continues to update normally.

**⚙️ Under the Hood**

- FCM token synchronization mutex with exponential retry (30 seconds to a 5-minute cap).
- WebSocket hibernation keepalive and signaling delivery flags.
- Idempotent message insertion and conflict resolution.
- Version updated from `3.0.2` to `3.1.5`.
- Version code: `11`.

**APK:** `void_release_v3.1.5.apk`  
**Minimum Android:** 8.0 (API 26)

**Full Changelog:** [Compare v3.0.2...v3.1.5](https://github.com/TOUTAKUN04/void_messenger/compare/v3.0.2...v3.1.5)

---

### v3.0.2

**New Features**

- **AXIOM Voice Transcription** — Voice notes in AXIOM chat can now be transcribed server-side using Groq Whisper. Works across Android versions without depending on Google's Android 13+ speech recognition service.
- **Online Presence** — Users remain online for up to 10 minutes after leaving the application. Active users refresh their presence window through heartbeats.

**Bug Fixes**

- Fixed media re-download loops that caused received images to download repeatedly, sometimes up to seven times.
- Fixed read receipts being dropped when the sender was offline during message synchronization.
- Fixed call history displaying raw UUIDs instead of user display names.
- Fixed AXIOM voice notes occasionally sending stray "." messages after silent or short recordings.
- Fixed missing `message_id` values in direct-message FCM payloads.
- Fixed FCM push notifications being rejected due to the reserved `message_type` data key.
- Fixed delivery and read states not updating correctly for messages sent while offline.

**AXIOM Worker**

- Upgraded to Gemini 2.5 Flash.
- Added Tier-2 search digest.
- Improved question-word gating and confusion/fallback escalation.
- Introduced the authenticated `/transcribe` endpoint using Groq Whisper.

**Under the Hood**

- Improved toast error handling and navigation error callbacks.
- Improved splash screen behaviour.
- Extended online presence from 90 seconds to 10 minutes.
- Removed the need for periodic presence cleanup jobs by calculating expiry at read time.

---

### v3.0.1

**New Features**

- Contacts page for managing VOID connections.
- In-app bug reporting.
- Display name editing through account settings.
- Full account deletion.
- File attachments with filename, size and download information.
- Individual call history deletion.

**Bug Fixes**

- Fixed message loading animations looping indefinitely.
- Fixed long-press context menu dismissal.
- Fixed self-chat read receipt edge cases.
- Fixed stale avatar cache caused by a database trigger issue.
- Improved orphaned Backblaze B2 media cleanup.
- Fixed avatar refresh after profile updates.
- Improved group messaging stability.
- Improved call functionality and stability.

**Privacy & Security**

- Enforced delete-for-everyone restrictions server-side.
- Connected Backblaze B2 media deletion to delete-for-everyone events.
- Added automatic hard deletion of undelivered messages after seven days.
- Added delivery failure notifications.
- Improved profile synchronization across devices using server-side timestamps.

**Under the Hood**

- Database migration v13 → v14.
- Improved message and media state tracking.
- Reduced unnecessary recomposition in message lists.
- Improved media loading performance.

---

### v2.2.0

- Introduced end-to-end encrypted group messaging.
- Added message reactions with floating picker UI.
- Added per-chat and global chat wallpapers.
- Overhauled voice message UI.
- Improved reply bubbles and media thumbnails.
- Introduced privacy-first presence without last-seen tracking.
- Hardened notification lock-screen privacy.
- Overhauled retry logic with intelligent 20-second timeouts.

### v2.1.3

Previous stable release.

---

## Important Links

| Resource | Link |
|---|---|
| Official Website | [void.toutakun04.qzz.io](https://void.toutakun04.qzz.io) |
| Latest Release | [Download](https://github.com/TOUTAKUN04/void_messenger/releases/latest) |
| All Releases | [GitHub Releases](https://github.com/TOUTAKUN04/void_messenger/releases) |
| Privacy Policy | [Read Policy](https://void.toutakun04.qzz.io/privacy) |
| Terms of Service | [Read Terms](https://void.toutakun04.qzz.io/terms) |
| Full v3.1.5 Changelog | [Compare Changes](https://github.com/TOUTAKUN04/void_messenger/compare/v3.0.2...v3.1.5) |

---

## Reporting Issues

Found a bug or potential security vulnerability?

- **Security Vulnerabilities:** Report them privately through the official website. Please avoid publicly disclosing exploitable vulnerabilities.
- **General Bugs:** Open an [Issue](https://github.com/toutakun04/void-releases/issues) in this repository or use VOID's built-in bug reporter.

Bug reports and feedback help improve VOID for everyone.

---

<div align="center">

**VOID**

*Built for privacy. Designed for freedom.*

**Nothing Leaves.**

© 2026 VOID

</div>
