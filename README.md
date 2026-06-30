# ⚽ FIFA World Cup 2026 — AmSty Predictor Challenge

Live site: **https://mmacy01.github.io/wc2026-amst/**

---

## 🚀 Setup (one-time, ~10 minutes)

### Step 1 — Firebase (real-time submissions)

1. Go to **https://console.firebase.google.com**
2. Click **Add project** → name it `wc2026-amst` → Create
3. Click **Build** → **Firestore Database** → **Create database** → **Start in test mode** → pick `us-central` → Enable
4. Click ⚙️ **Project Settings** → scroll to **Your apps** → click **</>** Web icon
5. Name it `wc2026-web` → Register app → copy the config object

### Step 2 — Paste your Firebase config into index.html

Open `index.html` in any text editor and find this block near the top of the `<script>` section:

```javascript
var FIREBASE_CONFIG = {
  apiKey:            "PASTE_YOUR_API_KEY_HERE",
  authDomain:        "PASTE_YOUR_PROJECT_ID.firebaseapp.com",
  projectId:         "PASTE_YOUR_PROJECT_ID",
  storageBucket:     "PASTE_YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "PASTE_YOUR_SENDER_ID",
  appId:             "PASTE_YOUR_APP_ID"
};
```

Replace each `PASTE_YOUR_...` value with your real Firebase values. Save the file.

### Step 3 — Push to GitHub

```bash
git add .
git commit -m "Add Firebase config"
git push
```

GitHub Actions will deploy automatically. Your site will be live at:
`https://YOUR-USERNAME.github.io/wc2026-amst/`

### Step 4 — Enable GitHub Pages (first time only)

1. Go to your repo on GitHub → **Settings** → **Pages**
2. Source: **GitHub Actions**
3. Done — it auto-deploys on every push from now on

---

## 🔐 Admin Access

- Click the **Admin** tab on the site
- Password: `Robschallenge`
- All participant submissions appear automatically in real time
- Enter actual results as the tournament plays out → hit **Calculate Scores**

---

## 🏆 How participants submit

1. Open the site link
2. Fill out all picks (Steps 1, 2, 3)
3. Hit **⚽ Submit My Picks**
4. Done — instantly appears in Rob's Admin portal on any device

---

## 📋 Scoring (Option A — Classic)

| Round | Points |
|---|---|
| Group Stage Winner | 1 pt × 12 |
| 3rd Place Qualifier | 2 pts × 8 |
| Round of 32 | 3 pts × 16 |
| Round of 16 | 5 pts × 8 |
| Quarterfinals | 7 pts × 4 |
| Semifinals | 10 pts × 2 |
| Final Winner | 15 pts |
| Champion Bonus | +10 pts |
| **Maximum** | **189 pts** |

---

## 🔧 Firestore Security Rules (paste after 30 days)

In Firebase Console → Firestore → Rules:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /wc2026_amst_submissions/{doc} {
      allow read, write: if true;
    }
  }
}
```
