# 🏥 MedScript BD — AI-Powered Prescription App

> Bangladesh's most complete AI-assisted clinical prescription system

---

## 🚀 Quick Start

```bash
# 1. Install dependencies
npm install

# 2. Set up your API keys
cp .env.example .env
# Edit .env with your keys

# 3. Run development server
npm run dev

# 4. Open http://localhost:3000
```

---

## 🔑 API Keys Setup (.env file)

```env
# Required for AI features
VITE_ANTHROPIC_API_KEY=sk-ant-api03-your-key-here

# Required for patient database (add when ready)
VITE_FIREBASE_API_KEY=your-firebase-api-key
VITE_FIREBASE_AUTH_DOMAIN=your-project.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your-project-id
VITE_FIREBASE_STORAGE_BUCKET=your-project.appspot.com
VITE_FIREBASE_MESSAGING_SENDER_ID=your-sender-id
VITE_FIREBASE_APP_ID=your-app-id

# Optional — increases OpenFDA rate limit
VITE_OPENFDA_API_KEY=your-openfda-key

# Optional — premium drug interactions (subscribe at drugbank.com)
VITE_DRUGBANK_API_KEY=your-drugbank-key
```

---

## 📁 Project Structure

```
medscript-bd/
│
├── data/                         ← Drug databases (JSON)
│   ├── medex-db.json             ← 21,714 BD drugs (MedEx 2021)
│   ├── generics-db.json          ← 1,711 generics with monographs
│   ├── indications-db.json       ← 2,043 indications
│   ├── manufacturers-db.json     ← 240 BD manufacturers
│   ├── dosage-forms-db.json      ← 113 dosage forms
│   └── drug-classes-db.json      ← 453 drug classes
│
├── src/
│   ├── config/
│   │   ├── app-config.js         ← ⚙️ MASTER CONTROL — all settings
│   │   └── api-keys.js           ← 🔑 All API keys
│   │
│   ├── components/               ← UI Components (one per feature)
│   │   ├── PatientPanel.jsx      ← Patient search, create, history
│   │   ├── VitalsPanel.jsx       ← Vitals + red flag alerts
│   │   ├── SymptomAnalyzer.jsx   ← AI symptom analysis
│   │   ├── DiagnosisPanel.jsx    ← AI differential diagnosis
│   │   ├── InvestigationPanel.jsx← AI investigation suggestions
│   │   ├── PrescriptionWriter.jsx← Drug writing in BD format
│   │   ├── DrugSearch.jsx        ← Autocomplete drug search
│   │   ├── InteractionChecker.jsx← Drug interaction safety
│   │   ├── DoseCalculator.jsx    ← Age/weight dose calculator
│   │   ├── FollowUpPanel.jsx     ← Follow-up scheduler
│   │   └── PDFExport.jsx         ← Print-ready prescription
│   │
│   ├── databases/                ← Data source modules
│   │   ├── medex-db.js           ← MedEx BD drug database
│   │   └── openfda-api.js        ← OpenFDA + NLM live APIs
│   │
│   ├── modules/                  ← AI & logic engines
│   │   └── claude-ai.js          ← All Claude AI features
│   │
│   ├── firebase/
│   │   └── firebase-config.js    ← Firebase patient database
│   │
│   └── utils/
│       └── patient-utils.js      ← Patient helpers, dose calc, red flags
│
├── .env                          ← Your API keys (never commit!)
├── .env.example                  ← Template to share
├── package.json
└── vite.config.js
```

---

## 🔧 Updating Databases

### Update BD Drug List (MedEx):
1. Get new CSV from MedEx / DGDA
2. Run: `python3 scripts/convert-medex.py new-file.csv`
3. Replace `data/medex-db.json`
4. Done — no code changes needed ✅

### Enable Firebase:
1. Add Firebase keys to `.env`
2. In `app-config.js`: set `DATA_SOURCES.firebase.enabled = true`
3. Done ✅

### Enable DrugBank:
1. Subscribe at drugbank.com
2. Add key to `.env`
3. In `app-config.js`: set `DATA_SOURCES.drugBank.enabled = true`
4. Done ✅

---

## 🤖 AI Features Toggle

In `src/config/app-config.js`:

```js
export const AI_FEATURES = {
  masterSwitch: true,          // Turn ALL AI on/off
  symptomAnalysis: { enabled: true },
  differentialDiagnosis: { enabled: true },
  investigationSuggestions: { enabled: true },
  drugSuggestions: { enabled: true },
  doseCalculator: { enabled: true },
  interactionChecker: { enabled: true },
}
```

---

## ⚠️ Medical Disclaimer

All AI suggestions are for **doctor review only**.
Final clinical decisions remain with the treating physician.
This app does not replace clinical judgment.

---

## 🏥 Built For

Bangladeshi doctors using BD trade names, Bengali meal instructions,
and MedEx drug database. Designed for daily outpatient use.

**Data Sources:**
- MedEx Bangladesh (medex.com.bd) — BD drug database
- OpenFDA — Drug interactions & adverse events
- NLM RxNorm — Drug standardization
- WHO Essential Medicines List
- Claude AI — Clinical reasoning
