<p align="center">
  <img src="docs/img/keepmark.png" width="112" height="112" alt="Keepmark" />
</p>

<h1 align="center">Keepmark</h1>

<p align="center">
  <b>Your bookmarks on every browser and your phone, synced and end-to-end encrypted.</b><br />
  No account needed. Compatible with xBrowserSync.
</p>

<p align="center">
  <a href="https://github.com/Keepmark/KeepmarkApp"><img src="https://img.shields.io/badge/Browser-Firefox%20%C2%B7%20Chrome%20%C2%B7%20Edge%20%C2%B7%20Brave-243878?style=for-the-badge" alt="Browser extension" /></a>
  <a href="https://github.com/Keepmark/KeepmarkMobile"><img src="https://img.shields.io/badge/Android-10%2B-1f6f5c?style=for-the-badge" alt="Android app" /></a>
  <a href="https://github.com/Keepmark/KeepmarkApi"><img src="https://img.shields.io/badge/Server-.NET%2010%20%C2%B7%20Docker-512bd4?style=for-the-badge" alt="Sync server" /></a>
</p>

<p align="center">
  <img src="docs/img/ecosystem.png" alt="Keepmark in a browser and on Android: the same encrypted bookmarks everywhere" />
</p>

---

## How it works

Your bookmarks are encrypted **on your device**, with a password that never
leaves it. The sync service stores only ciphertext and a random sync ID: no
email, no account, no way to read your data.

```mermaid
flowchart LR
    B["🧩 Browser<br/>Firefox · Chrome · Edge · Brave"]
    P["📱 Android"]
    S[("🗄️ Sync service<br/>ciphertext only")]
    B <-- "AES-GCM encrypted" --> S
    P <-- "AES-GCM encrypted" --> S
```

1. **Create a sync** in any Keepmark app: you get a sync ID and choose a password.
2. **Link your other devices** with the same sync ID and password.
3. **Done.** Changes flow everywhere; conflicts are never resolved behind your back.

It works with **any xBrowserSync service** (the official one, a community
host or your own) and with the official xBrowserSync apps. A sync created in
Keepmark opens there, and the other way round. Nothing to migrate.

---

## 🧩 Keepmark for browsers

<p align="center">
  <a href="https://github.com/Keepmark/KeepmarkApp"><img src="docs/img/browser/marquee.png" alt="Keepmark browser extension" /></a>
</p>

Firefox (MV2) and Chrome, Edge, Brave (MV3). Toolbar, menu and other
bookmarks sync automatically; the toolbar icon tells you at a glance whether
you are in sync.

- **Honest conflicts:** keep server, keep local or merge, with a preview first.
- **Safety backups** before every destructive step, plus encrypted export and import.
- **Duplicate cleanup**, service migration, change password, activity log.

<p align="center">
  <img src="docs/img/browser/02-conflict.png" width="49%" alt="Conflict preview" />
  <img src="docs/img/browser/03-duplicates.png" width="49%" alt="Duplicate cleanup" />
</p>
<p align="center">
  <img src="docs/img/browser/04-dark.png" width="49%" alt="Dark theme" />
  <img src="docs/img/browser/05-private.png" width="49%" alt="Connect a browser" />
</p>

<p align="center"><a href="https://github.com/Keepmark/KeepmarkApp"><b>→ Keepmark/KeepmarkApp</b></a></p>

---

## 📱 Keepmark for Android

<p align="center">
  <a href="https://github.com/Keepmark/KeepmarkMobile"><img src="docs/img/android/feature.png" alt="Keepmark for Android" /></a>
</p>

The same bookmarks in your pocket. Encrypted local database (SQLCipher),
credentials in the Android KeyStore, app lock with fingerprint or PIN.

- **Made for the phone:** full-text search, pinned bookmarks, breadcrumb, swipe for details.
- **Share to Keepmark** from any app: the add form opens already filled in.
- **Backups** compatible with the browser extension, safety snapshots, undo.

<p align="center">
  <img src="docs/img/android/01-browse.png" width="24%" alt="Browse folders" />
  <img src="docs/img/android/03-connect.png" width="24%" alt="Connect a sync" />
  <img src="docs/img/android/05-backup.png" width="24%" alt="Encrypted backups" />
  <img src="docs/img/android/07-pinned.png" width="24%" alt="Pinned bookmarks" />
</p>

<p align="center"><a href="https://github.com/Keepmark/KeepmarkMobile"><b>→ Keepmark/KeepmarkMobile</b></a></p>

---

## 🗄️ Keepmark Server

A drop-in xBrowserSync sync service: same contract, safer writes, easier to
run. Official xBrowserSync apps and Keepmark apps work unchanged.

- **No silent overwrites:** every conditional write is an atomic compare-and-swap.
- **Opt-in v1.2 API:** revisions, conflict detection, cheap `HEAD` / `304` checks, sync deletion.
- **Built to be public:** per-IP throttling, daily new-sync quota, origin allow-list, redacted logs.
- **Easy to operate:** Docker Compose with MongoDB, healthchecks and rolling backups.

```sh
git clone https://github.com/Keepmark/KeepmarkApi.git && cd KeepmarkApi
cp .env.example .env          # set real passwords
docker compose up --build -d
curl localhost:8080/info
```

<p align="center"><a href="https://github.com/Keepmark/KeepmarkApi"><b>→ Keepmark/KeepmarkApi</b></a></p>

---

## At a glance

| | [Browser](https://github.com/Keepmark/KeepmarkApp) | [Android](https://github.com/Keepmark/KeepmarkMobile) | [Server](https://github.com/Keepmark/KeepmarkApi) |
|---|:---:|:---:|:---:|
| End-to-end encryption | ✅ | ✅ | stores ciphertext only |
| Works with any xBrowserSync service | ✅ | ✅ | serves any xBrowserSync client |
| Conflict preview, safety backups | ✅ | ✅ | revision-based CAS (v1.2) |
| Encrypted backup export / import | ✅ | ✅ | — |
| Languages | 9 | 9 | — |

Languages: English, Italiano, Français, Español, Deutsch, 日本語, Português
(Brasil), Русский, 简体中文.

## Contact

Questions, bug reports or feedback: open an issue in the relevant repository
or write to [keepmark@proton.me](mailto:keepmark@proton.me).

<sub>Keepmark is an independent project built on the xBrowserSync protocol. Not affiliated with or endorsed by xBrowserSync.</sub>
