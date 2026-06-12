# 💌 Our Notebook

A cozy little web app for couples — draw pictures for each other, collect memories, plan dates, and leave love notes.
Everything **syncs in real-time** between two devices via Firebase 💕

🔗 **Live Demo:** https://surasitz.github.io/our-notebook/

🇹🇭 [อ่านภาษาไทย](README.md)

## ✨ Features

| | Feature | Details |
|---|---|---|
| 🎨 | **Draw for each other** | Color palette, adjustable brush size, eraser with size indicator, undo — works with touch, stylus, and mouse |
| 🖼️ | **Shared gallery** | Every drawing you send each other, with fullscreen view and a like button ❤️ |
| 🧳 | **Trip book** | Create trip albums and upload photos with captions (auto-compressed) to remember everywhere you've been together |
| 📅 | **Couple calendar** | Plan dates with emoji and details, supports multi-day trips, with a "X days to go" countdown |
| 💌 | **Love notes** | Leave messages for each other, pin 📌 the important ones to the top |
| 💞 | **Anniversary counter** | "Together for X days" always shown in the header |
| 🌙 | **Light/Dark mode** | Toggle anytime, preference is remembered |
| 📱 | **Responsive + PWA-ish** | Works on mobile and desktop, can be added to the iOS home screen with a cute custom icon |

## 🛠️ Tech Stack

- Plain **HTML / CSS / JavaScript** — a single file, no framework, no build step
- **Firebase Firestore** — real-time data sync
- **GitHub Pages** — free hosting
- Fonts: [Mali](https://fonts.google.com/specimen/Mali) & IBM Plex Sans Thai

## 🚀 Set Up Your Own

1. **Fork or download** this repo
2. Create a project at [Firebase Console](https://console.firebase.google.com) → enable **Firestore Database** (pick a region near you, start in test mode)
3. Set the **Firestore Rules**:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /couples/{code}/{document=**} {
         allow read, write: if true;
       }
     }
   }
   ```
4. Register a Web app (the `</>` icon) → copy your `firebaseConfig` into `index.html` (search for `PASTE_YOUR_API_KEY`)
5. Deploy to GitHub Pages: Settings → Pages → Deploy from branch `main`
6. Open the site, set a **couple code** + your nickname, then share the link and code with your special someone 💑

## 🔐 Security

- Room names in the database are **SHA-256 hashed** — looking at Firestore won't reveal the actual couple code
- The Firebase Web API key is publishable by design (security lives in the Rules); locking the API key to your domain in Google Cloud Console is recommended
- The main line of defense is the **couple code** — make it long, hard to guess, and keep it between the two of you
- Supports **Firebase App Check** (drop a reCAPTCHA v3 site key into the `APPCHECK_SITE_KEY` variable)
- ⚠️ Designed for two people. Not intended for storing highly sensitive photos or data

## 📝 Notes

- Photos are compressed to ~800KB max each to fit Firestore documents (the free 1GB quota ≈ 1,500+ photos)
- Without a firebaseConfig, the app runs in offline mode (data stays on one device) and shows a setup banner

---

Built with ❤️ for someone special
