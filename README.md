# void_messenger
Official APK releases for VOID Messenger — end-to-end encrypted, zero knowledge messaging for Android.
# VOID Releases

Official APK releases for **VOID Messenger** — a privacy-first encrypted messaging app for Android.

> Source code is maintained in a private repository. This repo exists solely for distributing signed release builds.

---

## Download

**Latest:** [v2.1.3](https://github.com/toutakun04/void-releases/releases/latest)

Or visit **[void.toutakun04.qzz.io](https://void.toutakun04.qzz.io)** to download directly.

---

## Installation

1. Download the APK from the [Releases](https://github.com/toutakun04/void-releases/releases) page
2. On your Android device, enable **Install from unknown sources**
   - Settings → Apps → Special app access → Install unknown apps
3. Open the downloaded APK and install
4. Launch VOID and sign in with Google or email

> Minimum Android version: **Android 8.0 (API 26)**

---

## Verifying the APK

All releases are signed with the VOID release keystore. You can verify the signature using `apksigner`:

```bash
apksigner verify --print-certs void-2.1.3.apk
```

The certificate SHA-1 should match the one published on the official site.

---

## What is VOID?

VOID is an end-to-end encrypted messaging app built around one principle — your conversations belong to no one.

- **E2EE** — EC P-256 + AES-256-GCM, encrypted on device via AndroidKeyStore
- **No phone number required** — sign up with Google or email
- **Zero data collection** — no analytics, no tracking, no metadata
- **Server-side queue only** — messages deleted from server immediately on delivery
- **Open architecture** — Cloudflare Workers + Supabase + Backblaze B2

---

## Release Cadence

| Channel | Description |
|--------|-------------|
| `beta` | Active development builds, may have rough edges |
| `stable` | Production-ready signed releases |

Current channel: **Beta**

---

## Links

- Website: [void.toutakun04.qzz.io](https://void.toutakun04.qzz.io)
- Privacy Policy: [void.toutakun04.qzz.io/privacy](https://void.toutakun04.qzz.io/privacy)
- Terms of Service: [void.toutakun04.qzz.io/terms](https://void.toutakun04.qzz.io/terms)

---

## Reporting Issues

Found a bug or security issue? 

- **Security vulnerabilities** — contact privately via the website
- **General bugs** — open an [Issue](https://github.com/toutakun04/void-releases/issues) on this repo

---

<div align="center">
  <sub>© 2026 VOID · Built for privacy · Nothing leaves</sub>
</div>
