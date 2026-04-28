# تذكير — Tethkir v5.2

**Islamic Task Manager & Secure Notes**

بِسْمِ ٱللَّهِ ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ

A single-file web app for managing tasks and notes with Islamic themes, voice input, and optional cloud sync. Installable as a PWA on Android and iOS.

---

## What's New in v5.2

**Safer Sync** — Sync is now timestamp-guarded: cloud can no longer overwrite newer local data, and an empty cloud doc can no longer wipe your tasks. `simpleNotes` is now included in the cloud payload (was silently missing).

**Multi-Layer Backups** — Rolling local snapshots (last 20, throttled to one per 5 min), daily cloud snapshots (last 14 days, auto-pruned), and a weekly reminder to download a JSON export. All restorable from Settings → Data Management.

**Critical Fix** — Resolved the data-loss bug where signing in could overwrite local tasks with stale or empty cloud state.

---

## Install

**Android** — Open in Chrome → tap ⋮ menu → "Add to Home Screen" or "Install App"

**iOS** — Open in Safari → tap Share → "Add to Home Screen"

The app runs fullscreen without a browser bar and works offline.

---

## Two Modes

**Simple Mode** (default) — Open the app, type a task or note, done. Voice input with 🎤, read notes aloud with 🔊, copy with 📋. Nothing else in the way.

**Advanced Mode** — Toggle in ⚙️ Settings. Unlocks: multiple profiles, task priorities/dates/categories/tags, search & filters, AES-256 encrypted notes, Arabic virtual keyboard, and the help system.

---

## Features

**Header** — Bismillah always visible and centered at the top. Arabic calligraphy title تذكير with theme-adaptive gradient. Sync status, language picker, sign-in, and settings on the controls row.

**Tasks** — Add, complete, delete, reorder. In Advanced mode: priority, due date, category, tags, search, filter, drag-and-drop.

**Notes** — Simple mode: plain text, just type and save. 📋 Copy, 🔊 Read aloud, 🗑️ Delete. Advanced mode: AES-256 encrypted with master passphrase.

**Voice** — 🎤 Speech-to-text on task/note inputs. 🔊 Text-to-speech on saved notes. Detects app language (EN/FR/AR).

**6 Islamic Themes** — Alhambra, Ottoman, Moroccan, Calligraphy, Ramadan, Desert.

**3 Languages** — English, French, Arabic with full RTL support.

**Cloud Sync** — Optional Firebase with Google Sign-In. ☁️ Sync Now button for manual sync.

**Offline** — Service worker caches the app. Works without internet.

**Profiles** — Multiple independent task lists (Advanced mode).

**Security** — PIN lock (SHA-256), encrypted notes (AES-256), change passphrase/PIN (Advanced mode).

**Data** — Export/Import JSON backups. 🗑️ Clear Cache. Works offline with localStorage.

**Mobile-first** — 16px inputs (no iOS zoom), 44px touch targets, responsive layout. PWA installable.

---

## Deploy on GitHub Pages

1. Create a GitHub repository (e.g. `tethkir`)
2. Upload: `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`, `README.html`, `CHANGES.html`, `CHANGES.md`, `README.md`
3. Settings → Pages → Source: main branch → Save
4. Live at `https://yourusername.github.io/tethkir/`

---

## Firebase Setup (Optional)

Open the app → ❓ Help → **Firebase Cloud Sync Setup** (in Advanced mode).

**Quick steps:**
1. Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)
2. Register a web app, copy the config JSON
3. Enable Google sign-in in Authentication
4. Create a Firestore database
5. Add your GitHub Pages domain as authorized
6. Paste config in ⚙️ Settings → Firebase Cloud Sync

**Firestore Rules:**
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| "Unauthorized domain" | Add domain in Firebase → Authentication → Authorized domains |
| Sign-in fails on iOS | Uses redirect auth — wait for page to reload |
| Popup blocked | Allow popups for your site |
| Notes won't decrypt | Wrong passphrase — no recovery |
| Old data showing | ⚙️ Settings → 🗑️ Clear Cache |
| App not updating | Clear browser cache or unregister service worker in DevTools |

---

## Tech Stack

Single HTML file. No build tools. PWA installable.

- **CryptoJS** — AES-256 encryption
- **Firebase 10.8** — Auth + Firestore (loaded on demand)
- **Reem Kufi** — Arabic calligraphy display font
- **Web Speech API** — STT and TTS
- **Service Worker** — Offline caching
- **localStorage** — Data persistence

---

*v5.1 — Built with love and Tawakkul. بارك الله فيكم* 🌙✨
