# 📝 Tethkir — Changelog

---

## v4.0 — 2026-02-27 — Multi-Pass Notes, Images & Smart Views 🖼️

### ✨ New Features
- **Multi-Passphrase Notes** — Any passphrase unlocks the notes section. Each note decrypts individually based on its own passphrase. Create new notes with a different passphrase without losing old ones.
- **Image Notes** — 📷 Camera/Gallery button on both Simple and Encrypted notes. Images are compressed (800px max, JPEG 70%) and stored inline. Tap any image to view fullscreen.
- **Notes Search** — 🔍 Real-time search bar filters notes by title or content
- **View Selector** — Toggle between 📄 List (collapsible cards) and 📐 Grid (2-column thumbnails) views. Preference is saved.
- **Pagination** — Notes load 10 at a time with "Load more" button for better performance
- **Collapsible Notes** — In list view, notes show title + date only. Tap to expand and see full content, image, and actions.

### 🔧 Fixes & Improvements
- **Mode Label Bug Fixed** — Settings now correctly shows "Simple Mode" or "Advanced Mode" with matching descriptions in all 3 languages
- **Locked Notes with Dates** — Notes encrypted with a different passphrase show their creation date/time instead of just a lock icon
- **🔑 Recover Old Notes** — "Unlock with another passphrase" button re-encrypts locked notes with your current passphrase
- Notes toolbar (search + view toggle) appears in both Simple and Advanced modes

---

## v1.1 — 2026-02-22 — Android PWA & Offline 📱

### ✨ New Features
- **Progressive Web App (PWA)** — Install on Android/iOS home screen, runs fullscreen like a native app
- **Service Worker** — Caches all assets for true offline use. App works without internet
- **App Icons** — 192px and 512px icons for home screen and splash screen
- **Theme Color** — Android status bar matches the Alhambra dark theme

### 🔧 Improvements
- `manifest.json` with app name, icons, standalone display mode
- `sw.js` caches core assets on install, cache-first strategy, old cache cleanup
- Firebase/Google auth requests bypass the cache
- Offline navigation falls back to cached index.html
- Apple mobile web app meta tags for iOS home screen

---

## v1.0 — 2026-02-22 — Initial Release 🚀

بِسْمِ ٱللَّهِ ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ

### ✨ Core Features
- **Simple Mode** (default) — Clean, minimal interface: just tasks and plain notes with voice input
- **Advanced Mode** — Toggle in Settings to unlock profiles, priorities, categories, tags, filters, encrypted notes, Arabic keyboard, and help system
- **Task Management** — Add, complete, delete, drag-and-drop reorder. Advanced: priority, due date, category, tags, search, filter
- **Notes** — Simple mode: plain text with 📋 copy, 🔊 read aloud, 🗑️ delete. Advanced mode: AES-256 encrypted with master passphrase
- **Firebase Cloud Sync** — Google Sign-In, auto-sync, bidirectional sync, manual ☁️ Sync Now button
- **Multiple Profiles** — Default + custom profiles with independent task lists (Advanced)
- **PIN Lock** — 4-digit protection with SHA-256 hashing

### 🎤 Voice Features
- **Speech-to-Text** — 🎤 mic button on task title, note title, note content
- **Text-to-Speech** — 🔊 button on each note reads it aloud
- Auto-detects app language (EN/FR/AR)

### 🎨 Design
- **6 Islamic Themes** — Alhambra, Ottoman, Moroccan, Calligraphy, Ramadan, Desert
- **3 Languages** — English, French, Arabic with full RTL support and SVG flags
- **Settings Sidebar** — Slides from right (left in RTL), collapsible accordion sections
- **Discrete Bismillah** — بِسْمِ ٱللَّهِ ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ in the header bar
- **Status Indicator** — 🟢 Synced / 🟠 Online / 🔴 Offline
- **Mobile-first** — 16px inputs, 44px touch targets, responsive layout

### ⌨️ Arabic Virtual Keyboard (Advanced)
- Full alphabet, harakat/diacritics, Arabic numerals
- Preview bar with copy/paste toolbar
- 🤲 Islamic phrases drawer with 14 built-in + custom phrases

### ❓ Help System (Advanced)
- Floating help panel with quick tips, feature guide, FAQ
- In-app Firebase setup guide
- Contextual ? tooltips

### 📦 Data Management
- ☁️ Sync Now — manual push/pull to Firebase
- 📥 Export / 📤 Import JSON backups
- 🗑️ Clear Cache — wipe local data (cloud data unaffected)

### 📱 iOS Support
- Redirect-based Google Sign-In for iOS Safari
- No-zoom inputs (16px), large touch targets

---

*Built with love and Tawakkul. بارك الله فيكم* 🌙✨
