# 🏥 MedScript BD — Setup Guide

## ⚡ Everything is Pre-Configured!

Both Firebase and Anthropic AI keys are already inside the app.
You just need to deploy it.

---

## Deploy to Vercel (Free — No Terminal Needed)

1. Go to **https://vercel.com** → Sign up with Google
2. Click **"Add New Project"**
3. Click **"Upload"** → select the ZIP file
4. Framework will auto-detect as **Vite**
5. Click **Deploy**
6. Your app is live! 🎉

Your URL will be something like: `medscript-bd.vercel.app`

---

## Enable Firestore Database (One Time)

1. Go to **https://console.firebase.google.com**
2. Open project **dhanvantari-108**
3. Click **"Firestore Database"** → **"Create Database"**
4. Choose **"Start in test mode"**
5. Select region: **asia-south1 (Mumbai)**
6. Click **Enable** — Done ✅

---

## Using the App

```
Step 1: Patient        → Search or create (auto PT-ID)
Step 2: Vitals         → BP, Temp, SpO₂ — red flags auto
Step 3: History        → Type or speak — AI follow-ups
Step 4: Diagnosis      → AI differential diagnosis
Step 5: Investigations → AI suggestions + manual
Step 6: Prescription   → BD drug search + AI doses
Step 7: Preview/Print  → Review, follow-up, print A4
```

---

⚠️ All AI suggestions are for doctor review only.
Final clinical decisions remain with the treating physician.
