# Firebase-Powered E-Commerce App – ShopSpark+

Live Site: https://shop-spark-firebase.vercel.app  
GitHub Repo: https://github.com/theller31/shop-spark-firebase

---


1. Go to [Firebase Console](https://console.firebase.google.com)
2. Create a project → Add a web app
3. Enable:
   - **Authentication > Email/Password**
   - **Cloud Firestore**
4. In `firebaseConfig.js`, paste your config:
```js
// src/firebase/firebaseConfig.js
import { initializeApp } from 'firebase/app';
import { getFirestore } from 'firebase/firestore';
import { getAuth } from 'firebase/auth';

const firebaseConfig = {
  apiKey: "YOUR_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "XXXXXXX",
  appId: "APP_ID"
};

const app = initializeApp(firebaseConfig);
export const db = getFirestore(app);
export const auth = getAuth(app);
```

---

## Features

### 👤 Authentication
- Register / Login via Email + Password
- Firestore `users` document created on signup
- Profile editing & deletion

### 🛍️ Products (Firestore `products`)
- View all products
- Admins can: Add / Edit / Delete

### 🧾 Orders (Firestore `orders`)
- Cart checkout saves an `order` with userID
- Order history per user
- Click to view full order details

---

## 🔄 Environment Variables

Create a `.env` file using `.env.example`:

```
VITE_FIREBASE_API_KEY=
VITE_FIREBASE_AUTH_DOMAIN=
VITE_FIREBASE_PROJECT_ID=
VITE_FIREBASE_STORAGE_BUCKET=
VITE_FIREBASE_MESSAGING_SENDER_ID=
VITE_FIREBASE_APP_ID=
```

---

## 🧪 Testing

- Unit tests for Auth + Firestore logic:
```bash
npm run test
```

---

## 🚀 CI/CD: GitHub Actions + Vercel

- Push to `main` → runs build + test via GitHub Actions
- On success, Vercel deploys live

> CI file: `.github/workflows/main.yml`

---

## 📦 Deployment (Vercel)
1. Import repo into Vercel
2. Add `.env` variables in Vercel settings
3. Deploy!

Live Link: https://shop-spark-firebase.vercel.app
