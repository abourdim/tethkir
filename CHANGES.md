# 📝 Tethkir — Changelog

All notable changes to this project will be documented in this file.

---

## v1.4.0 — 2026-02-21 — Firebase Cloud Sync ☁️🔥

### ✨ New Features
- **☁️ Full Firebase Integration** — Google Sign-In and Firestore cloud sync now fully working
- **Dynamic SDK Loading** — Firebase SDK loaded on demand from CDN (no performance hit in local mode)
- **Auto-Sync** — Every change (tasks, notes, profiles, stars, theme, language) auto-syncs to cloud when signed in
- **Bidirectional Sync** — Pull from cloud on sign-in, push on every save
- **Auth State Persistence** — Stay signed in across page reloads
- **Sync Status UI** — Green dot + user name when connected, red dot when offline
- **Error Handling** — Clear toast messages for unauthorized domain, popup closed, invalid config, etc.

### 📖 Documentation
- **In-App Firebase Guide** — Full 7-step setup guide with collapsible sections added to Help tab
- **Styled Steps** — Numbered step indicators with accent colors and code blocks
- **Updated README** — Removed old "Developer Step 8", added Troubleshooting table
- **Updated FAQ** — "How do I sync across devices?" now references in-app guide

### 🔧 Improvements
- `saveState()` now auto-syncs to cloud when signed in
- `init()` auto-loads Firebase SDK on page load if config was previously saved
- `toggleAuth()` performs actual Google sign-in/sign-out instead of placeholder toast
- `saveFirebaseConfig()` loads SDK immediately after saving config
- `clearFirebaseConfig()` signs out and cleans up Firebase state

---

## v1.3.2 — 2026-02-19 — Standard Copy/Paste 📋📌

### 🔧 Improvements
- **📌 Paste now works normally** — Pastes FROM clipboard INTO preview bar (standard behavior)
- **📋 Copy** — Copies preview text TO clipboard (unchanged)
- **Standard workflow** — Type/compose in preview → 📋 Copy → click your field → Ctrl+V
- **No more "send to field" magic** — Removed confusing behavior, everything works as expected
- **Enter key** — No longer triggers any action (was confusing)
- **Clipboard fallback** — Shows "Use Ctrl+V" if browser blocks clipboard access

---

## v1.3.1 — 2026-02-19 — Simplify Keyboard 🧹

### 🔧 Improvements
- **Removed Direct mode entirely** — Simpler UX: always type in preview bar, then Copy or Paste
- **Only 3 action buttons** — 📋 Copy, 📌 Paste, ✖ Clear (+ 🤲 Phrases next to input)
- **↵ Enter key = Paste** — Quick shortcut to paste preview text into last focused field
- **Removed ~50 lines of dead code** — No more kbIsDirect variable, toggle function, or dual-path logic
- **Updated help section** — Removed Direct mode documentation

---

## v1.3 — 2026-02-19 — Bug Fixes & Islamic Emoji Redesign 🌙

### 🐛 Bug Fixes
- **Copy button now works** — Fixed clipboard API with proper fallback for local files, visual feedback (selects text)
- **Paste button now works** — Removed duplicate code block causing early return; clear error messages for empty preview or no focused field
- **Direct mode now works** — Fixed critical naming conflict (`kbDirectMode` was both variable and function name); renamed variable to `kbIsDirect`
- **Preview bar is editable** — Click to type directly, cursor-aware insert from virtual keys

### 🎨 Islamic Emoji Redesign
Removed all animal and human emojis, replaced with Islamic-themed alternatives:
- **عـ / غـ for Show/Hide password** — عين (Ain) = "eye" in Arabic; غين (Ghain) = Ain with dot = "veiled eye". Deeply meaningful, elegant, and unique
- **⭐ replaces 🧸 for Kids Mode** — Stars are already the reward system, consistent and joyful
- **Toggle buttons styled** in Amiri font with accent color

### 🔧 Improvements
- **Better error toasts** — "Nothing to copy", "Nothing to paste", "Click a field first"
- **Flat toolbar layout** — Row 1: [editable input] + [🤲], Row 2: [📋 Copy] [📌 Paste] [✖ Clear] [🎯 Direct]
- **Gentle close button** — Moved to left, subtle card style (no red)

---

## v1.2.5 — 2026-02-19 — Editable Preview & Flat Buttons ⌨️

### 🔧 Improvements
- **Preview bar is now an editable input** — Click it, type, select, edit, cursor position works
- **Flat buttons restored** — 🤲 Phrases next to preview, Copy/Paste/Clear/Direct in a centered row below
- **Layout**: Row 1 = [editable input] + [🤲], Row 2 = [📋 Copy] [📌 Paste] [✖ Clear] [🎯 Direct]
- **Cursor-aware typing** — Virtual keyboard inserts at cursor position in the preview
- **Cursor-aware backspace** — Deletes at cursor position, not just end
- **Preview excluded from "last focused"** — Paste sends to your real input field, not back to preview
- Removed hidden popup menu — everything visible and flat

---

## v1.2.4 — 2026-02-19 — UI Polish 🎨

### 🔧 Improvements
- **Close button moved to left** — ⌨️ opens on the right, closes on the left (less confusing)
- **No more red X** — Close buttons now use subtle card-style (border + muted color), highlights on hover
- **Help button too** — Same gentle style when active, no more red
- **Gentler close labels** — Shows `⌨️ ▾` and `❓ ▾` instead of aggressive `✕`
- **RTL aware** — Positions flip correctly for Arabic layout

---

## v1.2.3 — 2026-02-19 — Toolbar Popup Menu ⚡

### 🔧 Improvements
- **Single ⚡ menu button** replaces the row of buttons — cleaner, no overlap
- **Popup menu** appears above the button with all actions: 🤲 Phrases, 📋 Copy, 📌 Paste, ✖ Clear, 🎯 Direct mode
- **Preview bar gets maximum width** — no more cramped layout
- **Auto-closes** when clicking outside or after an action
- **Smart arrow** pointing to the button for clarity
- **RTL aware** — popup and arrow flip for Arabic layout

---

## v1.2.2 — 2026-02-19 — Keyboard Toolbar Redesign 🔧

### 🐛 Bug Fixes
- **Two-row toolbar layout** — Preview bar on top, buttons centered below (no more overlap)
- **Labels restored** — Buttons show emoji + short text (🤲 Phrases, 📋 Copy, 📌 Paste, ✖ Clear, 🎯 Direct)
- **Bigger touch targets** — Buttons are wider and easier to tap on mobile
- **Mobile adaptive** — Buttons shrink gracefully on small screens

---

## v1.2.1 — 2026-02-19 — Keyboard Toolbar Fix 🔧

### 🐛 Bug Fixes
- **Toolbar overflow fixed** — Buttons are now icon-only (🤲📋📌✖🎯) to prevent overlapping with the preview bar
- **Space between phrases** — Inserting multiple Islamic phrases now automatically adds a space separator
- **Preview bar scrollable** — Long text in keyboard preview now scrolls horizontally instead of being cut off
- **Responsive toolbar** — Buttons shrink properly on mobile screens

---

## v1.2 — 2026-02-19 — Islamic Shortcuts Drawer 🤲⌨️

### ✨ New Features

#### 🤲 Islamic Phrases Shortcuts
- **Side drawer** slides from the right edge (left in RTL) via 🤲 button on keyboard toolbar
- **14 built-in phrases** with full harakat:
  - بِسْمِ ٱللَّهِ ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ (Bismillah)
  - الحمد لله (Alhamdulillah)
  - سبحان الله (SubhanAllah)
  - الله أكبر (Allahu Akbar)
  - إن شاء الله (In Shaa Allah)
  - ما شاء الله (Ma Shaa Allah)
  - جزاك الله خيراً (JazakAllahu Khairan)
  - السلام عليكم (Assalamu Alaikum)
  - وعليكم السلام (Wa Alaikum Assalam)
  - صلى الله عليه وسلم (Sallallahu Alaihi Wasallam)
  - أستغفر الله (Astaghfirullah)
  - لا إله إلا الله (La ilaha illAllah)
  - بارك الله فيك (Barakallahu Fik)
  - حسبنا الله ونعم الوكيل (Hasbunallah)
- **Each card shows all three**: Arabic (large calligraphic), transliteration (italic), meaning (in current language)
- **Tap to preview** — phrase goes to keyboard preview bar, then Copy or Paste to any field
- **Custom phrases** — "+" button opens form to add your own (Arabic + transliteration + meaning)
- **Delete custom** — 🗑️ button on hover for custom phrases
- **Custom phrases saved** in localStorage, persist across sessions
- **Meanings translated** per phrase in EN/FR/AR
- **All UI translated** in EN 🇬🇧 / FR 🇫🇷 / AR 🇸🇦

---

## v1.1 — 2026-02-19 — Help System & Password Management 🆘🔑

### ✨ New Features

#### ❓ Floating Help Widget
- **Floating ❓ button** (bottom-left) opens a sliding help panel
- **Quick Start cards** — 4 visual tips: Add Task, Complete Task, Change Theme, Switch Language
- **Feature Guide** — 9 accordion sections covering all features in detail:
  - Tasks, Secure Notes, Arabic Keyboard, Themes, Kids Mode, Profiles, Import/Export, Firebase, PIN Lock
- **FAQ section** — 6 common questions with detailed answers
- **Search filter** — Search help content by keyword in real-time
- **Fully translated** in EN 🇬🇧 / FR 🇫🇷 / AR 🇸🇦

#### 🏷️ Contextual Tooltips
- **?** icons next to key UI elements (Priority, Tags, PIN Lock, Kids Mode)
- Hover or tap to see a helpful tooltip bubble
- Positioned smartly, responsive on mobile

#### 🔑 Change Passphrase
- **Button** appears next to 🔒 Lock when notes are unlocked
- **Modal** with current/new/confirm passphrase fields (all with 👁️ show/hide)
- **Validates**: wrong current passphrase, mismatch, too short, same as old
- **Re-encrypts all notes** with the new passphrase

#### 🔑 Change PIN
- **Button** appears in Settings when PIN is set
- **Modal** with current/new/confirm PIN fields (all with 👁️ show/hide)
- **Validates**: wrong current PIN, mismatch, same as old

### 🔧 Improvements
- Version bumped to v1.1
- Version display in Settings page
- Changelog link in Settings page

---

## v1.0 — 2026-02-19 — Initial Release 🚀

بِسْمِ ٱللَّهِ ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ

### ✨ Features
- **Task Management** — Add, edit, delete, mark as done with priority levels (High/Medium/Low), due dates, categories, tags, search, filter, and drag-and-drop reorder
- **7 Islamic Themes** — Alhambra/Andalusian, Ottoman/Turkish, Moroccan Zellige, Calligraphy/Minimal, Ramadan Night, Desert Oasis, Kids/Playground
- **3 Languages** — English 🇬🇧, French 🇫🇷, Arabic 🇸🇦 with full RTL layout support
- **Dual Storage** — Local (localStorage) for offline use + Firebase-ready cloud sync with Google Sign-In
- **Import/Export** — Download/upload all data as JSON backup file
- **PIN Lock** — 4-digit PIN protection with SHA-256 hashing
- **Encrypted Secure Notes** — AES-256 client-side encryption via CryptoJS
- **Kids Mode** — Toggle switch, separate profiles, star rewards ⭐, confetti celebrations 🎉, encouraging Islamic messages
- **Multiple Profiles** — Default, Kids, and custom profiles with independent task lists
- **Beautiful Bismillah Header** — بِسْمِ ٱللَّهِ ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ in calligraphic Arabic font, adapts to each theme
- **Responsive Design** — Works on mobile and desktop

### 🔐 Security
- **Show/Hide password toggle** (👁️/🙈) on all password fields
- **Passphrase confirmation** — Required when creating first secure note
- **Passphrase verification** — Validates against existing notes on unlock, shows error if wrong
- **Change Passphrase** — Modal with current/new/confirm fields, re-encrypts all notes
- **Change PIN** — Modal with current/new/confirm fields, validates old PIN

### ⌨️ Arabic Virtual Keyboard
- **Floating bottom panel** — Toggle with ⌨️ button (bottom-right corner)
- **Full Arabic alphabet** — Standard layout with all letters
- **Harakat / Diacritics** — فتحة، ضمة، كسرة، تنوين، شدّة، سكون
- **Arabic numbers** — ٠١٢٣٤٥٦٧٨٩
- **Two modes** — Preview mode (type then paste) and Direct mode (type into focused field)
- **Toolbar** — Copy 📋, Paste 📌, Clear ✖ buttons
- **Responsive** — Adapts to mobile screens

### 🔧 UX Improvements
- **Secure Notes UX** — Notes list shown first after unlock, collapsible "Write New Note" form, clear "🔐 Encrypt & Save" button
- **Note count hint** — Shows "🔒 You have X encrypted notes saved" on reload
- **Enter key support** — Press Enter to submit in task form, passphrase field, and confirm field
- **Version display** — Version shown in Settings page with link to changelog

### 📄 Documentation
- **README.md** — Full feature overview, GitHub Pages deployment guide, 8-step Firebase setup tutorial
- **README.html** — Styled documentation page with Alhambra theme and "Open App" button
- **CHANGES.md** — This changelog
- **CHANGES.html** — Styled changelog page

---

*Built with love and Tawakkul. بارك الله فيكم* 🌙✨
