# 📝 Tethkir — تذكير

**Islamic Task Manager & Secure Notes**

بِسْمِ ٱللَّهِ ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ

A single-file web app for managing tasks and encrypted notes with Islamic themes, Arabic keyboard, voice features, and optional Firebase cloud sync.

---

## Features

**Tasks** — Full task management with priorities, due dates, categories, tags, search, filter, and drag-and-drop reorder.

**Secure Notes** — AES-256 encrypted notes with master passphrase. 🔊 Listen to notes read aloud.

**6 Islamic Themes** — Alhambra, Ottoman, Moroccan, Calligraphy, Ramadan, Desert.

**3 Languages** — English, French, Arabic with full RTL support.

**Arabic Keyboard** — Virtual keyboard with full alphabet, harakat, Arabic numerals, and 🤲 Islamic phrases drawer.

**Voice** — 🎤 Speech-to-text on task/note inputs. 🔊 Text-to-speech on saved notes.

**Cloud Sync** — Optional Firebase integration with Google Sign-In. Auto-syncs tasks, notes, profiles, theme, and language.

**Profiles** — Multiple independent task lists (Default + custom).

**Security** — PIN lock (SHA-256), encrypted notes (AES-256), change passphrase/PIN support.

**Data** — Import/Export JSON backups. Clear All Data option. Works offline with localStorage.

---

## Deploy on GitHub Pages

1. Create a GitHub repository (e.g. `tethkir`)
2. Upload all files: `index.html`, `README.html`, `CHANGES.html`, `CHANGES.md`, `README.md`
3. Go to Settings → Pages → Source: main branch → Save
4. Your app is live at `https://yourusername.github.io/tethkir/`

---

## Firebase Setup (Optional)

The app includes a built-in Firebase setup guide. Open the app → tap ❓ Help → scroll to **Firebase Cloud Sync Setup**.

**Quick summary:**
1. Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)
2. Register a web app and copy the config JSON
3. Enable Google sign-in in Authentication
4. Create a Firestore database
5. Add your GitHub Pages domain as an authorized domain
6. Paste the config JSON in Settings → Firebase Cloud Sync

**Firestore Security Rules:**
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
| "Unauthorized domain" on sign-in | Add your domain in Firebase Console → Authentication → Settings → Authorized domains |
| Popup blocked | Allow popups for your site in browser settings |
| "Invalid config" | Check JSON format — must have apiKey, authDomain, projectId, storageBucket, messagingSenderId, appId |
| Notes won't decrypt | Wrong passphrase — there is no recovery |
| Old data after rename | Clear browser localStorage (Settings → Clear All) |

---

## Tech Stack

- **Single HTML file** — No build tools, no dependencies to install
- **CryptoJS** — AES-256 encryption for secure notes
- **Firebase 10.8** — Auth + Firestore (loaded on demand)
- **Web Speech API** — Speech-to-text and text-to-speech
- **localStorage** — Offline data persistence

---

*v1.0 — Built with love and Tawakkul. بارك الله فيكم* 🌙✨
