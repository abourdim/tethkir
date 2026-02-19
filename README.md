# 📝 Tadhkir — Islamic Task Memo App

بِسْمِ ٱللَّهِ ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ

**Tadhkir** (تذكير — "Reminder") is a beautiful, feature-rich task management web app inspired by Islamic art and architecture. It works offline with localStorage and optionally syncs to the cloud via Firebase.

---

## ✨ Features

### 📝 Task Management
- **Add, edit, delete** tasks with a single click
- **Mark as done** with satisfying checkmarks
- **Priority levels** — High (red), Medium (yellow), Low (green) with color-coded indicators
- **Due dates** — Set deadlines for your tasks
- **Categories** — General, Work, Personal, Homework, Chores, Dua/Quran, Activities, Fun
- **Tags** — Add comma-separated tags for organization
- **Search & filter** — Find tasks instantly by title, tag, priority, category, or status
- **Drag-and-drop reorder** — Organize tasks your way

### 🕌 7 Islamic-Inspired Themes
| Theme | Description |
|-------|-------------|
| 🏰 **Alhambra / Andalusian** | Warm gold, terracotta, deep red — inspired by Granada's Alhambra palace |
| 🔵 **Ottoman / Turkish** | Turquoise, cobalt blue, gold accents — Iznik tile inspired |
| 💎 **Moroccan Zellige** | Emerald, saffron, royal blue — vibrant jewel tones |
| ✒️ **Calligraphy / Minimal** | Cream, black ink, gold — manuscript/parchment aesthetic |
| 🌙 **Ramadan Night** | Deep navy, purple, twinkling gold stars — peaceful night sky |
| 🏜️ **Desert Oasis** | Sandy beige, palm green, sky blue — calm and soothing |
| 🧸 **Kids / Playground** | Bright, colorful, rounded — fun for children |

### 🌍 Multi-Language Support
- **English** 🇬🇧
- **French** 🇫🇷
- **Arabic** 🇸🇦 with full **RTL (Right-to-Left)** layout support

### 🔒 Security Features
- **PIN Lock** — 4-digit PIN to protect the app (SHA-256 hashed)
- **Encrypted Secure Notes** — AES-256 client-side encryption using CryptoJS
- Your notes are encrypted *before* being stored — nobody can read them without your passphrase

### 👶 Kids Mode
- **Toggle switch** — Quick flip between Kids and Adult UI
- **Separate profiles** — Each family member gets their own task space
- **Star rewards** ⭐ — Earn stars for completing tasks
- **Confetti celebration** 🎉 — Fun animations when tasks are done
- **Encouraging Islamic messages** — "Ma Shaa Allah! Great job!"
- **Kid-friendly categories** — Homework, Chores, Dua/Quran, Activities, Fun

### 💾 Dual Storage
- **Local mode** (default) — Works immediately, data saved in browser's localStorage
- **Cloud mode** (optional) — Sync across all your devices via Firebase

### 📦 Import / Export
- **Export** all your data as a `.json` backup file
- **Import** data from a `.json` file on any device
- Works in both local and cloud modes

### 👤 Multiple Profiles
- Default and Kids profiles included
- Create custom profiles for family members
- Each profile has its own independent task list

---

## 🚀 Quick Start

### Option 1: Just Open It
Simply download `index.html` and open it in any modern browser. Everything works locally out of the box.

### Option 2: Host on GitHub Pages (Recommended)

1. **Create a GitHub account** (if you don't have one) at [github.com](https://github.com)

2. **Create a new repository:**
   - Click the **+** button → **New repository**
   - Name it something like `tadhkir` or `task-memo`
   - Set it to **Public** (required for free GitHub Pages)
   - Check **"Add a README file"** (optional)
   - Click **Create repository**

3. **Upload the files:**
   - In your new repo, click **Add file** → **Upload files**
   - Drag and drop both `index.html` and `README.md`
   - Click **Commit changes**

4. **Enable GitHub Pages:**
   - Go to **Settings** → **Pages** (in the left sidebar)
   - Under **Source**, select **Deploy from a branch**
   - Select **main** branch, **/ (root)** folder
   - Click **Save**

5. **Access your app:**
   - Wait 1-2 minutes for deployment
   - Your app will be live at: `https://YOUR-USERNAME.github.io/tadhkir/`
   - Bookmark this URL on all your devices!

---

## ☁️ Firebase Cloud Sync Setup (Step-by-Step)

Firebase allows you to sync your tasks across all devices. Here's the complete setup guide:

### Step 1: Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click **"Create a project"** (or "Add project")
3. Enter a project name: `tadhkir` (or anything you like)
4. Disable Google Analytics (not needed) or enable it — your choice
5. Click **Create project**
6. Wait for setup to complete, then click **Continue**

### Step 2: Register a Web App

1. On the project overview page, click the **Web icon** `</>` (looks like `</>`)
2. Enter an app nickname: `Tadhkir Web`
3. ✅ Check **"Also set up Firebase Hosting"** if you want Firebase hosting instead of GitHub Pages (optional)
4. Click **Register app**
5. You'll see a code block with your Firebase config. It looks like this:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyBxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  authDomain: "tadhkir-xxxxx.firebaseapp.com",
  projectId: "tadhkir-xxxxx",
  storageBucket: "tadhkir-xxxxx.appspot.com",
  messagingSenderId: "123456789012",
  appId: "1:123456789012:web:abcdef1234567890"
};
```

6. **Copy this entire config object** — you'll need it later
7. Click **Continue to console**

### Step 3: Enable Authentication (Google Sign-In)

1. In the Firebase Console, click **Build** → **Authentication** in the left sidebar
2. Click **Get started**
3. Go to the **Sign-in method** tab
4. Click **Google**
5. Toggle the **Enable** switch ON
6. Select a **Support email** (your Gmail address)
7. Click **Save**

### Step 4: Set Up Cloud Firestore Database

1. Click **Build** → **Firestore Database** in the left sidebar
2. Click **Create database**
3. Choose a location closest to you:
   - Europe: `europe-west1` (Belgium) or `europe-west6` (Zurich)
   - Middle East: `me-south1` (Doha)
   - US: `us-central1` (Iowa)
   - Asia: `asia-southeast1` (Singapore)
4. Click **Next**
5. Select **Start in test mode** (we'll secure it later)
6. Click **Create**

### Step 5: Set Firestore Security Rules

1. In Firestore, click the **Rules** tab
2. Replace the default rules with:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Users can only read/write their own data
    match /users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

3. Click **Publish**

This ensures only authenticated users can access their own data — nobody else can see your tasks.

### Step 6: Add Authorized Domains

1. Go to **Authentication** → **Settings** tab
2. Scroll to **Authorized domains**
3. Click **Add domain**
4. Add your GitHub Pages domain: `YOUR-USERNAME.github.io`
5. Click **Add**

This allows Google Sign-In to work from your GitHub Pages site.

### Step 7: Paste Config in Tadhkir

1. Open your Tadhkir app
2. Go to **Settings** tab (⚙️)
3. Scroll down to **Firebase Cloud Sync**
4. Paste your Firebase config as JSON in the text area:

```json
{
  "apiKey": "AIzaSyBxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "authDomain": "tadhkir-xxxxx.firebaseapp.com",
  "projectId": "tadhkir-xxxxx",
  "storageBucket": "tadhkir-xxxxx.appspot.com",
  "messagingSenderId": "123456789012",
  "appId": "1:123456789012:web:abcdef1234567890"
}
```

5. Click **Save Config**
6. Click **☁️ Sign In** in the top bar
7. Sign in with your Google account
8. Your tasks will now sync across all devices! 🎉

### Step 8: Enable Firebase on the HTML (Developer Step)

> **Note:** The current version has Firebase config storage ready. To make the actual sync work, you need to add the Firebase SDK scripts to the HTML file. Add these lines before the closing `</body>` tag:

```html
<!-- Firebase SDK -->
<script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-auth-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-firestore-compat.js"></script>

<script>
// Initialize Firebase with saved config
const savedConfig = localStorage.getItem('tadhkir_firebase');
if (savedConfig) {
  const app = firebase.initializeApp(JSON.parse(savedConfig));
  const auth = firebase.auth();
  const db = firebase.firestore();

  // Google Sign-In
  window.firebaseSignIn = async () => {
    try {
      const provider = new firebase.auth.GoogleAuthProvider();
      const result = await auth.signInWithPopup(provider);
      console.log('Signed in:', result.user.displayName);
      syncFromCloud();
      updateSyncUI(true);
    } catch (error) {
      console.error('Sign-in error:', error);
    }
  };

  // Sign Out
  window.firebaseSignOut = async () => {
    await auth.signOut();
    updateSyncUI(false);
  };

  // Sync tasks to cloud
  window.syncToCloud = async () => {
    const user = auth.currentUser;
    if (!user) return;
    try {
      await db.collection('users').doc(user.uid).set({
        tasks: state.tasks,
        profiles: state.profiles,
        notes: state.notes,
        stars: state.stars,
        updatedAt: firebase.firestore.FieldValue.serverTimestamp()
      });
      console.log('Synced to cloud');
    } catch (error) {
      console.error('Sync error:', error);
    }
  };

  // Sync tasks from cloud
  window.syncFromCloud = async () => {
    const user = auth.currentUser;
    if (!user) return;
    try {
      const doc = await db.collection('users').doc(user.uid).get();
      if (doc.exists) {
        const data = doc.data();
        state.tasks = data.tasks || state.tasks;
        state.profiles = data.profiles || state.profiles;
        state.notes = data.notes || state.notes;
        state.stars = data.stars || state.stars;
        saveState();
        renderProfiles();
        renderTasks();
        updateStars();
      }
    } catch (error) {
      console.error('Fetch error:', error);
    }
  };

  // Update UI for sync status
  function updateSyncUI(online) {
    document.getElementById('syncDot').className = 'sync-dot ' + (online ? 'online' : 'offline');
    document.getElementById('syncLabel').textContent = online ? 'Synced' : 'Offline';
    document.getElementById('authBtn').textContent = online ? '☁️ Sign Out' : '☁️ Sign In';
  }

  // Override toggleAuth
  window.toggleAuth = () => {
    if (auth.currentUser) {
      firebaseSignOut();
    } else {
      firebaseSignIn();
    }
  };

  // Auto-sync when tasks change (override saveState)
  const originalSaveState = saveState;
  window.saveState = () => {
    originalSaveState();
    if (auth.currentUser) syncToCloud();
  };

  // Check auth state on load
  auth.onAuthStateChanged(user => {
    if (user) {
      updateSyncUI(true);
      syncFromCloud();
    }
  });
}
</script>
```

---

## 📁 File Structure

```
tadhkir/
├── index.html      ← The complete app (single file)
└── README.md       ← This documentation
```

Everything is contained in a single `index.html` file for maximum simplicity and portability.

---

## 🔐 Security Notes

### PIN Lock
- Your PIN is hashed with SHA-256 before storage
- The PIN prevents casual access to the app UI
- It does NOT encrypt your task data

### Secure Notes (AES Encryption)
- Notes are encrypted using AES-256 via [CryptoJS](https://github.com/brix/crypto-js)
- Encryption happens **client-side** — your passphrase never leaves your browser
- Without the passphrase, notes are unreadable gibberish
- If you forget your passphrase, **notes cannot be recovered**

### Important Warnings
- ⚠️ **Do NOT store critical passwords** in this app — use a proper password manager like [Bitwarden](https://bitwarden.com/) (free) or KeePass
- ⚠️ localStorage can be read by browser extensions and anyone with device access
- ⚠️ Firebase data is stored as plain text unless you use the Secure Notes feature
- ✅ Secure Notes with a strong passphrase are reasonably safe for personal memos

---

## 🌍 Language & RTL Support

| Language | Code | Direction | Font |
|----------|------|-----------|------|
| English | `en` | LTR (Left-to-Right) | Poppins |
| French | `fr` | LTR (Left-to-Right) | Poppins |
| Arabic | `ar` | RTL (Right-to-Left) | Amiri / Aref Ruqaa |

When Arabic is selected, the entire layout flips automatically — text alignment, sidebar, icons, and all UI elements adapt to RTL.

---

## 🧸 Kids Mode Guide

### How It Works
1. **Toggle Kids Mode** in Settings or click the 🧸 button
2. **Switch to Kids profile** in the profile bar
3. Kids see simplified categories: Homework, Chores, Dua/Quran, Activities, Fun
4. Completing tasks earns ⭐ stars with confetti animations
5. Encouraging Islamic messages appear: "Ma Shaa Allah! Great job!"

### For Parents
- Set up tasks for your children
- Track their progress via the star counter
- Use the PIN lock to prevent kids from accessing Secure Notes or Settings
- Create separate profiles for each child

---

## 📦 Import & Export Guide

### Exporting Data
1. Go to **Settings** → **Data Management**
2. Click **📥 Export**
3. A `.json` file will download with all your tasks, notes, profiles, and settings

### Importing Data
1. Go to **Settings** → **Data Management**
2. Click **📤 Import**
3. Select your `.json` backup file
4. All data will be restored instantly

### Use Cases
- **Backup** your data regularly
- **Transfer** tasks between devices without Firebase
- **Share** task templates with others
- **Migrate** from one browser to another

---

## 🛠️ Customization

### Adding New Themes
You can add new themes by adding a CSS `[data-theme="yourtheme"]` block with the following variables:

```css
[data-theme="yourtheme"] {
  --bg-primary: #...;
  --bg-secondary: #...;
  --bg-card: #...;
  --bg-input: #...;
  --text-primary: #...;
  --text-secondary: #...;
  --accent: #...;
  --accent-hover: #...;
  --accent-glow: rgba(...);
  --border: rgba(...);
  --bismillah-color: #...;
  --bismillah-glow: rgba(...);
  --pattern-opacity: 0.06;
}
```

Then add a theme card in the Settings HTML section.

### Adding New Languages
Add a new language object in the `i18n` constant following the existing `en`, `fr`, `ar` pattern, and add the language option in the `langSelect` dropdown.

---

## 🤝 Contributing
Feel free to fork, improve, and share! Some ideas for contributions:
- Additional Islamic themes (Persian, Mughal, Mamluk...)
- More languages (Turkish, Urdu, Malay, Indonesian...)
- Push notifications for due dates
- Recurring tasks
- Calendar view
- Voice input for tasks

---

## 📄 License
This project is open source and free to use. Built with love and Tawakkul.

---

## 🤲 Acknowledgments
- **بِسْمِ ٱللَّهِ ٱلرَّحْمَـٰنِ ٱلرَّحِيمِ** — In the name of Allah, the Most Gracious, the Most Merciful
- Fonts: [Amiri](https://fonts.google.com/specimen/Amiri), [Aref Ruqaa](https://fonts.google.com/specimen/Aref+Ruqaa), [Scheherazade New](https://fonts.google.com/specimen/Scheherazade+New)
- Encryption: [CryptoJS](https://github.com/brix/crypto-js)
- Hosting: [GitHub Pages](https://pages.github.com/)
- Backend: [Firebase](https://firebase.google.com/)

---

**May this app help you stay organized and focused on what matters. بارك الله فيكم** 🌙✨
