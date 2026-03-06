# 🎓 Smart College Assistant

A complete AI-powered college management system combining NLP Chatbot, Face Recognition Attendance, and Role-Based Dashboard for students and faculty.

---

## 📌 Project Overview

Smart College Assistant is a full-stack web application. It integrates three modules into one unified system:

- **Module 1** — NLP-based College Chatbot
- **Module 2** — Face Recognition Attendance System
- **Module 3** — Role-Based Access Dashboard (Student & Faculty)

---

## 🚀 Features

### 🤖 Module 1 — NLP Chatbot
- Trained on custom college dataset with 10 intents
- Uses TF-IDF Vectorizer + Logistic Regression
- Answers questions about admissions, fees, exams, placements, hostel, library, scholarships, and more
- Confidence score displayed with every response

### 👁️ Module 2 — Face Recognition Attendance
- Register face via webcam
- Automatic attendance marking using face recognition
- Stores 128-dimension face encodings in SQLite
- Attendance reports with CSV export

### 🔐 Module 3 — Role-Based Dashboard
- Login with credentials or face recognition
- New user registration with face capture (2-step process)
- **Student Dashboard:** Attendance %, grades, announcements, monthly planner, reminders, chatbot
- **Faculty Dashboard:** All students, mark attendance, upload grades, post announcements, monthly planner, chatbot
- Dark/Light mode toggle

---

## 🛠️ Tech Stack

### Backend
| Technology | Purpose |
|-----------|---------|
| Python 3.12 | Core language |
| Flask | REST API backend |
| SQLite | Database |
| scikit-learn | NLP model training |
| TF-IDF Vectorizer | Text to numbers conversion |
| Logistic Regression | Intent classification |
| face_recognition | Face encoding and matching |
| OpenCV | Webcam capture |
| dlib | Face detection |
| NumPy | Array processing |
| flask-cors | Cross-origin requests |

### Frontend
| Technology | Purpose |
|-----------|---------|
| Next.js 16 | React framework |
| TypeScript | Type-safe JavaScript |
| Tailwind CSS | Styling |
| Lucide React | Icons |

---

## 📁 Project Structure

```
smart_college_final/          ← Backend
├── main.py                   ← Combined Flask backend (all routes)
├── college.db                ← SQLite database
├── chatbot/                  ← Module 1
│   ├── predictor.py          ← Intent prediction
│   ├── response.py           ← Response generator
│   ├── intent_model.pkl      ← Trained ML model
│   ├── vectorizer.pkl        ← Trained TF-IDF vectorizer
│   ├── college_dataset.csv   ← Training dataset
│   └── __init__.py
└── face_module/              ← Module 2
    ├── database.py           ← Database setup
    ├── register_face.py      ← Face registration
    └── recognize_face.py     ← Face recognition + attendance

chatbot-ui-for-college-assistant/   ← Frontend
├── app/
│   ├── page.tsx              ← Chatbot UI
│   ├── dashboard/
│   │   └── page.tsx          ← Full dashboard UI
│   └── api/chat/             ← Chat API route
└── components/               ← Reusable UI components
    ├── chat-container.tsx
    ├── chat-message.tsx
    ├── chat-input.tsx
    ├── chat-header.tsx
    ├── chat-welcome.tsx
    └── typing-indicator.tsx
```

---

## 🗄️ Database Tables

| Table | Purpose |
|-------|---------|
| `users` | Name, roll number, password hash, role, face encoding |
| `attendance` | Date, time, subject, status per student |
| `grades` | Marks, grade, subject, semester per student |
| `announcements` | Faculty announcements for students |
| `todos` | Monthly planner tasks for both roles |
| `reminders` | Date/time reminders for both roles |

---

## ⚙️ Installation & Setup

### Prerequisites
- Python 3.12
- Node.js 18+
- CMake (for dlib)
- Visual C++ Build Tools (Windows)
- Git

### Backend Setup

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/smart-college-assistant.git

# Go to backend folder
cd smart_college_final

# Install Python packages
py -3.12 -m pip install flask flask-cors numpy scikit-learn face_recognition opencv-python

# Run the backend
py -3.12 main.py
```

### Frontend Setup

```bash
# Go to frontend folder
cd chatbot-ui-for-college-assistant

# Install Node packages
npm install

# Run the frontend
npm run dev
```

### Access the App
| Page | URL |
|------|-----|
| Chatbot | http://localhost:3000 |
| Dashboard | http://localhost:3000/dashboard |
| Backend API | http://localhost:5000 |

---

## 🔑 Demo Credentials

| Role | Roll Number | Password |
|------|------------|----------|
| 👨‍🏫 Faculty | FAC001 | faculty123 |
| 👨‍🎓 Student | STU001 | student123 |
| 👨‍🎓 Student | STU002 | student123 |

---

## 📡 API Endpoints

| Method | Endpoint | Purpose |
|--------|---------|---------|
| POST | `/auth/login` | Login with credentials |
| POST | `/auth/register` | Register new user with face |
| POST | `/auth/face-login` | Login with face recognition |
| GET | `/auth/me` | Get current user |
| GET | `/student/dashboard` | Student dashboard data |
| GET | `/student/attendance` | Student attendance records |
| GET | `/faculty/dashboard` | Faculty dashboard data |
| POST | `/faculty/attendance/mark` | Mark attendance |
| POST | `/faculty/grades/upload` | Upload grades |
| POST | `/faculty/announcement` | Post announcement |
| GET/POST | `/todos` | Manage todo tasks |
| GET/POST | `/reminders` | Manage reminders |
| POST | `/chat` | Chatbot endpoint |
| GET | `/health` | System health check |

---

## 🧠 How the NLP Chatbot Works

1. User types a message
2. TF-IDF Vectorizer converts text to numerical vector
3. Logistic Regression classifies the intent
4. If confidence > 35%, appropriate response is returned
5. If confidence < 35%, user is asked to rephrase

**Supported Intents:**
- Admissions, Fees, Exams, Attendance, Placements
- Hostel, Library, Scholarships, Certificates, General

---

## 👁️ How Face Recognition Works

1. **Registration:** Webcam captures face → 128-dimension encoding generated → stored in database
2. **Login/Attendance:** Webcam captures face → encoding compared with stored encodings → if distance < 0.50, match found
3. Attendance automatically marked after successful recognition

---

## ⚠️ Known Issues & Limitations

- Face recognition requires Python 3.12 (not compatible with 3.13+)
- dlib installation on Windows requires CMake + Visual C++ Build Tools
- Free API quota limits for AI chatbot
- SQLite suitable for small scale only (upgrade to PostgreSQL for production)

---


---

## 📄 License

This project is for educational purposes only.
