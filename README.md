# VOID Releases
Official APK releases for **VOID Messenger** — a privacy-first encrypted messaging app for Android.

> Source code is maintained in a private repository. This repo exists solely for distributing signed release builds.

---

## Download

**Latest:** [v3.0.1](https://github.com/TOUTAKUN04/void_messenger/releases/latest)

Or visit **[void.toutakun04.qzz.io](https://void.toutakun04.qzz.io)** to download directly.

---

## Installation

1. Download the APK from the [Releases](https://github.com/TOUTAKUN04/void_messenger/releases) page
2. On your Android device, enable **Install from unknown sources**
   - Settings → Apps → Special app access → Install unknown apps
3. Open the downloaded APK and install
4. Launch VOID and sign in with Google or email

> Minimum Android version: **Android 8.0 (API 26)**

---

## Verifying the APK

All releases are signed with the VOID release keystore. You can verify the signature using `apksigner`:

```bash
apksigner verify --print-certs void-3.0.1.apk
```

The certificate SHA-1 should match the one published on the official site.

---

## What is VOID?

VOID is an end-to-end encrypted messaging app built around one principle — your conversations belong to no one.

- **E2EE** — EC P-256 + AES-256-GCM, encrypted on device via AndroidKeyStore
- **No phone number required** — sign up with Google or email
- **Zero data collection** — no analytics, no tracking, no metadata
- **Server-side queue only** — messages deleted from server immediately on delivery
- **Group messaging** — fully E2EE group chats with per-member key delivery
- **Open architecture** — Cloudflare Workers + Supabase + Backblaze B2

---

## Features

| Feature | Status |
|--------|--------|
| 1:1 E2EE messaging | ✅ |
| Group messaging (E2EE) | ✅ Beta |
| Voice messages | ✅ |
| File attachments | ✅ |
| Media sharing | ✅ |
| Message reactions | ✅ |
| Reply to messages | ✅ |
| Chat wallpapers | ✅ |
| Read receipts | ✅ |
| Calls | ✅ Beta |
| Contacts page | ✅ |
| In-app bug reporting | ✅ |
| Change display name | ✅ |
| Delete account | ✅ |
| Google & email sign-in | ✅ |
| No phone number required | ✅ |

---

## Release Cadence

| Channel | Description |
|--------|-------------|
| `beta` | Active development builds, may have rough edges |
| `stable` | Production-ready signed releases |

Current channel: **Beta**

---

## Changelog

### v3.0.1

**New Features**
- Contacts page — view and manage your VOID connections in one place
- In-app bug reporting — report issues directly without leaving VOID
- Change display name from account settings
- Full account deletion — removes your data from VOID servers permanently
- File attachments — send documents in chat with inline filename, size, and download action
- Call log management — delete individual entries from call history

**Bug Fixes**
- Fixed message loading animation looping indefinitely
- Fixed long-press context menu not dismissing correctly
- Fixed self-chat edge cases causing incorrect read receipt states
- Fixed `moddatetime` trigger not firing on profile updates — stale avatar cache resolved
- Fixed orphaned B2 media on delete failure — `media_status` only removed if B2 DELETE succeeds
- Fixed avatar not refreshing after profile update
- Groups stability fixes — groups now workable in beta
- Calls stability fixes — calls functional in alpha

**Privacy & Security**
- Delete-for-Everyone window now enforced server-side — late attempts rejected cleanly
- B2 media deletion wired to delete-for-everyone signal — file removed from Backblaze immediately
- Undelivered messages hard-deleted after 7 days — sender receives delivery failure notification
- Profile sync overhauled — display name and avatar consistent across devices via server-side timestamps

**Under the Hood**
- Database migration v13 → v14 with improved message and media state tracking
- Reduced unnecessary recomposition in message list
- Minor performance improvements to media loading pipeline

---

### v2.2.0
- Group messaging with full E2EE
- Message reactions with floating picker UI
- Chat wallpapers (per-chat and global)
- Voice message UI overhaul
- Reply bubble and thumbnail improvements
- Privacy-first presence — no last_seen tracking
- Notification lock screen privacy hardened
- Retry logic overhaul with 20s intelligent timeout

### v2.1.3
- Previous stable release

---

## Links

- Website: [void.toutakun04.qzz.io](https://void.toutakun04.qzz.io)
- Privacy Policy: [void.toutakun04.qzz.io/privacy](https://void.toutakun04.qzz.io/privacy)
- Terms of Service: [void.toutakun04.qzz.io/terms](https://void.toutakun04.qzz.io/terms)

---

## Reporting Issues

Found a bug or security issue?

- **Security vulnerabilities** — contact privately via the website
- **General bugs** — open an [Issue](https://github.com/toutakun04/void-releases/issues) on this repo or use the in-app bug reporter

---

<div align="center">
  <sub>© 2026 VOID · Built for privacy · Nothing leaves</sub>
</div>
