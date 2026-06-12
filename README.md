# 💌 สมุดของเรา (Our Notebook)

เว็บแอปสมุดบันทึกสำหรับคู่รัก — วาดรูปส่งหากัน เก็บความทรงจำ นัดเดท และเขียนโน้ตถึงกัน
ข้อมูลทุกอย่าง **sync กันแบบ real-time** ระหว่างสองเครื่องผ่าน Firebase 💕

🔗 **Live Demo:** https://surasitz.github.io/our-notebook/

## ✨ ฟีเจอร์

| | ฟีเจอร์ | รายละเอียด |
|---|---|---|
| 🎨 | **วาดรูปให้กัน** | จานสี ปรับขนาดหัวปากกา ยางลบ (พร้อมวงแสดงขนาด) Undo รองรับทั้งนิ้ว ปากกา และเมาส์ |
| 🖼️ | **แกลเลอรีของเรา** | รูปวาดที่ส่งหากันทั้งหมด กดขยายดูเต็มจอ กดหัวใจถูกใจได้ ❤️ |
| 🧳 | **สมุดทริป** | สร้างอัลบั้มทริป อัปโหลดรูปถ่ายพร้อมแคปชั่น (ย่อรูปอัตโนมัติ) เก็บความทรงจำว่าไปเที่ยวไหนมาบ้าง |
| 📅 | **ปฏิทินคู่** | ลงนัดพร้อมอีโมจิ รายละเอียดนัด นัดหลายวันได้ มีนับถอยหลัง "อีก X วัน" |
| 💌 | **โน้ตรัก** | เขียนข้อความถึงกัน ปักหมุด 📌 อันสำคัญไว้บนสุดได้ |
| 💞 | **ตัวนับวันครบรอบ** | โชว์ "คบกันมา X วัน" ตลอดบนหัวเว็บ |
| 🌙 | **โหมดกลางวัน/กลางคืน** | สลับธีมได้ จำค่าอัตโนมัติ |
| 📱 | **Responsive + PWA-ish** | ใช้ได้ทั้งมือถือและคอม เพิ่มลงหน้าจอโฮม iOS ได้พร้อมไอคอนน่ารัก |

## 🛠️ เทคโนโลยี

- **HTML / CSS / JavaScript** ล้วนๆ ไฟล์เดียวจบ ไม่มี framework ไม่ต้อง build
- **Firebase Firestore** — เก็บข้อมูลและ sync แบบ real-time
- **GitHub Pages** — โฮสต์ฟรี
- ฟอนต์ [Mali](https://fonts.google.com/specimen/Mali) และ IBM Plex Sans Thai

## 🚀 วิธีติดตั้งใช้เอง

1. **Fork หรือดาวน์โหลด** repo นี้
2. สร้างโปรเจกต์ที่ [Firebase Console](https://console.firebase.google.com) → เปิด **Firestore Database** (เลือก asia-southeast1, Start in test mode)
3. ตั้ง **Firestore Rules**:
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
4. สร้าง Web app (ไอคอน `</>`) → ก๊อป `firebaseConfig` มาวางใน `index.html` (ค้นหาคำว่า `PASTE_YOUR_API_KEY`)
5. Deploy ขึ้น GitHub Pages: Settings → Pages → Deploy from branch `main`
6. เปิดเว็บ ตั้ง **รหัสคู่** + ชื่อเล่น แล้วส่งลิงก์กับรหัสให้คนพิเศษ 💑

## 🔐 ความปลอดภัย

- ชื่อห้องใน database ถูกแปลงเป็น **SHA-256 hash** — เปิด Firestore เห็นก็เดารหัสคู่กลับไม่ได้
- API key ของ Firebase Web เป็นข้อมูลเปิดเผยได้ตามดีไซน์ของ Google (ความปลอดภัยอยู่ที่ Rules) แนะนำให้**ล็อกโดเมน** API key ใน Google Cloud Console เพิ่ม
- ความปลอดภัยหลักอยู่ที่ **รหัสคู่** — ตั้งให้ยาวและเดายาก อย่าแชร์ให้คนอื่น
- รองรับ **Firebase App Check** (ใส่ reCAPTCHA v3 site key ที่ตัวแปร `APPCHECK_SITE_KEY`)
- ⚠️ เหมาะสำหรับใช้กันสองคน ไม่ควรเก็บรูปหรือข้อมูลที่เป็นความลับระดับสูง

## 📝 หมายเหตุ

- รูปถ่ายถูกย่อให้ไม่เกิน ~800KB ต่อรูปเพื่อให้พอดีกับ Firestore (โควต้าฟรี 1GB ≈ 1,500+ รูป)
- ถ้ายังไม่ใส่ firebaseConfig แอปจะทำงานแบบออฟไลน์ (เก็บข้อมูลในเครื่องเดียว) พร้อมแถบเตือน

---

สร้างด้วย ❤️ เพื่อคนพิเศษ


English Version.
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
