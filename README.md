# 🎧 HearSafe - AI-Powered Hearing Test & Analysis

An innovative web application that provides **professional-grade hearing testing** combined with **AI-powered risk analysis** to detect hearing loss early and recommend preventive measures.

## ✨ Features

- 🔊 **Interactive Hearing Test** - Frequency-based tone testing (250Hz - 8kHz)
- 🤖 **AI Risk Analysis** - Machine learning model predicts hearing loss risk
- 📊 **Audiogram Visualization** - Real-time hearing threshold graphs
- 👤 **User Authentication** - Firebase-based sign-up and login
- 💾 **Test History** - Track hearing tests over time
- 🎯 **Risk Classification** - GREEN, YELLOW, ORANGE, RED risk levels
- 📋 **WHO Classification** - International hearing loss grading
- 🌐 **Responsive Design** - Works on desktop and mobile

---

## 🏗️ Tech Stack

### Frontend
- **Framework**: Next.js 15 (React)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **UI Components**: Shadcn/ui
- **Database**: Firebase Firestore
- **Authentication**: Firebase Auth
- **State Management**: React Hooks

### Backend
- **Framework**: FastAPI (Python)
- **ML Model**: Random Forest (scikit-learn)
- **Data Processing**: Pandas, NumPy
- **Server**: Uvicorn
- **API**: RESTful

---

## 🚀 Quick Start

### Prerequisites
- Node.js 16+ and npm/pnpm
- Python 3.8+
- Git

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/yourusername/hearsafe.git
cd hearsafe/hearsafe
```

**2. Install Frontend Dependencies**
```bash
npm install
```

**3. Install Backend Dependencies**
```bash
cd backend
python -m venv venv
venv\Scripts\activate  # On Windows
pip install fastapi uvicorn joblib pandas numpy scikit-learn
```

### Configuration

**1. Create `.env.local` in the project root** (`hearsafe/hearsafe/`)
```env
NEXT_PUBLIC_FIREBASE_API_KEY=your_api_key_here
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id
```

Get these values from [Firebase Console](https://console.firebase.google.com/)

### Running the Application

**Terminal 1 - Frontend (http://localhost:3001)**
```bash
cd hearsafe
npm run dev
```

**Terminal 2 - Backend (http://127.0.0.1:8000)**
```bash
cd backend
uvicorn app:app --host 127.0.0.1 --port 8000 --reload
```

Open your browser: **http://localhost:3001**

---

## 📁 Project Structure

```
hearsafe/
├── app/                      # Next.js app directory
│   ├── page.tsx             # Home page
│   ├── layout.tsx           # Root layout
│   ├── test/                # Hearing test pages
│   ├── results/             # Results display
│   ├── login/               # Login page
│   ├── sign-up/             # Sign-up page
│   └── globals.css          # Global styles
├── components/              # React components
│   ├── AuthForm.tsx         # Authentication form
│   ├── common/              # Common components
│   └── ui/                  # Shadcn UI components
├── backend/                 # FastAPI backend
│   ├── app.py              # Main API
│   ├── train_fixed.py      # ML model training
│   └── hearsafe_rf.pkl     # Trained model
├── lib/                     # Utilities
│   └── firebase/            # Firebase config
└── public/                  # Static assets
```

---

## 🔐 Firebase Setup

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project: `majorpro-hearsafe`
3. Enable **Authentication** (Email/Password)
4. Enable **Firestore** database
5. Copy credentials to `.env.local`

---

## 📊 How It Works

### Hearing Test Flow
1. User completes frequency-based tone test
2. Hearing thresholds are recorded for each ear
3. PTA (Pure Tone Average) is calculated
4. Results sent to backend for analysis

### Backend Analysis
1. **Presbycusis Correction** - Age-related hearing loss adjustment
2. **Metric Calculation** - EHFA, HF Shift Index, Cochlear Load Index
3. **Rule Engine** - Applies medical thresholds
4. **ML Prediction** - Random Forest model predicts risk
5. **Risk Classification** - Returns GREEN/YELLOW/ORANGE/RED

### Risk Levels
- 🟢 **GREEN** - Normal hearing, minimal risk
- 🟡 **YELLOW** - Mild hearing loss, moderate risk  
- 🟠 **ORANGE** - Moderate hearing loss, high risk
- 🔴 **RED** - Severe hearing loss, critical risk

---

## 🤖 Machine Learning Model

The AI model uses a **Random Forest classifier** trained on:
- Demographic data (age, sex)
- Listening habits (hours/day, volume level)
- Environmental exposure (noisy environment)
- Event frequency (concerts, loud events)
- Hearing test metrics (EHFA, HF Shift Index, CLI)

**Model Accuracy**: ~85% on validation set

---

## 🧪 Testing

**Run Frontend Tests**
```bash
npm run test
```

**Backend Testing**
```bash
cd backend
pytest
```

---

## 📝 API Endpoints

### Backend API (`http://127.0.0.1:8000`)

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Health check |
| POST | `/analyze` | Analyze hearing test results |

**POST `/analyze` Request:**
```json
{
  "age": 30,
  "sex": "M",
  "hours_per_day": 2,
  "volume_level": 75,
  "noisy_environment": false,
  "events_per_month": 1,
  "left_thresholds": [20, 15, 10, 15, 20, 25, 30],
  "right_thresholds": [22, 18, 12, 17, 22, 27, 32]
}
```

**Response:**
```json
{
  "risk": "GREEN",
  "overall_score": 92,
  "cli": 155,
  "hf_shift_index": 5,
  "ehfa_mean": 19
}
```

---

## 🔗 Environment Variables

| Variable | Description |
|----------|-------------|
| `NEXT_PUBLIC_FIREBASE_API_KEY` | Firebase API Key |
| `NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN` | Firebase Auth Domain |
| `NEXT_PUBLIC_FIREBASE_PROJECT_ID` | Firebase Project ID |
| `NEXT_PUBLIC_FIREBASE_APP_ID` | Firebase App ID |

---

## 🛠️ Build & Deployment

**Build Frontend**
```bash
npm run build
```

**Deploy to Vercel**
```bash
npm i -g vercel
vercel
```

**Deploy Backend**
- Use Railway, Render, or Heroku
- Set environment variables
- Configure database path

---

## 📄 License

MIT License - See LICENSE file for details

---

## 👨‍💻 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

---

## 📞 Support

For issues or questions:
- Open an issue on GitHub
- Email: support@hearsafe.app

---

## 🙏 Acknowledgments

- WHO Hearing Loss Classification
- ISO 7029 Presbycusis Standards
- Shadcn/ui Component Library
- FastAPI Framework

---

**Made with ❤️ for hearing health awareness**


This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
