# 🍽️ BolBor — Voice Enabled Restaurant Management System

<div align="center">

![BolBor Logo](logo.png)

**Speak. Manage. Grow.**

[![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)](https://python.org)
[![Flask](https://img.shields.io/badge/Flask-3.0-green?logo=flask)](https://flask.palletsprojects.com)
[![React](https://img.shields.io/badge/React-18-61DAFB?logo=react)](https://react.dev)
[![Groq](https://img.shields.io/badge/Groq-LLaMA_3.3_70B-orange)](https://groq.com)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

*Built at Hackathon 2025 by Team BolBor*

</div>

---

## 📖 What is BolBor?

BolBor is an AI-powered, voice-enabled restaurant management system that allows restaurant staff to manage orders, tables, and billing entirely through voice commands — in **Hindi, Gujarati, or English**.

Instead of typing orders manually, a waiter simply speaks:
> *"do burger aur ek coke"* → System understands → Bill generated ✅

---

## 👥 Team Members

| Name | Role | Responsibility |
|------|------|---------------|
| **Dev Pawar** | Frontend | React UI, Figma Design |
| **Lakhan Karmur** | Backend | Flask APIs, Server |
| **Jasmin Thummar** | Database & Integration | MongoDB, API Integration |
| **Pratham Sonpal** | Voice & AI | Speech Recognition, NLP, Groq AI |

---

## ✨ Features

### 🎤 Voice System
- **Multilingual support** — Hindi, Gujarati, English, and mixed language
- **Wake word** — Say *"Hey Bol"* to activate hands-free
- **Smart NLP** — Understands natural sentences like *"mujhe 2 burger chahiye"*
- **Edit by voice** — *"remove one burger"*, *"add one more coke"*
- **Noise handling** — Auto-retry on silence, network errors handled gracefully
- **Text to Speech** — System speaks back order confirmation in customer's language

### 👨‍🍳 Role-Based Access
| Role | Features |
|------|---------|
| **Waiter** | Voice ordering, table booking, cart management, order history |
| **Chef** | Kitchen display, order timers, sound notifications, voice status updates |
| **Cashier** | Bill summary, payment method selection, UPI QR code, PDF bills |
| **Admin** | Live dashboard, revenue chart, staff overview, all tables |

### 🍽️ Restaurant Management
- Table booking and status tracking (Free / Occupied / Reserved)
- Real-time kitchen order display with timer warnings
- Sound notification when new order arrives at kitchen
- Order history for waiters

### 💳 Billing & Payment
- PDF bill generation with logo and tax breakdown
- Payment method selection — **Cash / Card / UPI**
- Auto-generated **UPI QR Code** with exact bill amount
- Table auto-cleared after payment

### 📊 Admin Dashboard
- Live revenue tracking
- Item popularity chart (Recharts)
- Active order monitoring
- Staff account management

---

## 🛠️ Tech Stack

### Backend (Python)
| Library | Purpose |
|---------|---------|
| `flask` | Web server & REST APIs |
| `flask-cors` | Cross-origin requests for React frontend |
| `groq` | Groq AI API — LLaMA 3.3 70B for NLP |
| `pyttsx3` | Text-to-Speech (system speaks back) |
| `SpeechRecognition` | Captures mic input |
| `pyaudio` | Microphone access |
| `reportlab` | PDF bill generation |
| `rapidfuzz` | Fuzzy matching for menu items |
| `word2number-i18n` | Converts number words (one, ek, be → 1, 1, 2) |
| `qrcode[pil]` | UPI QR code generation |

### Frontend (React + TypeScript)
| Library | Purpose |
|---------|---------|
| `React 18` | UI framework |
| `Vite` | Build tool |
| `TypeScript` | Type safety |
| `Tailwind CSS` | Styling |
| `React Router v7` | Page routing |
| `Recharts` | Revenue & analytics charts |
| `Lucide React` | Icons |
| `Sonner` | Toast notifications |
| `shadcn/ui` | UI component library |
| `Web Speech API` | Browser voice recognition (built-in Chrome) |

---

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- Node.js 18+
- Google Chrome (for Web Speech API)
- Groq API key (free at [console.groq.com](https://console.groq.com))

---

### 🔧 Backend Setup

**1. Clone the repository**
```bash
git clone https://github.com/PrathamSonpal/BolBor.git
cd bolbor
```

**2. Install Python dependencies**
```bash
pip install flask flask-cors groq pyttsx3 SpeechRecognition pyaudio reportlab rapidfuzz word2number-i18n qrcode[pil]
```

> ⚠️ If `pyaudio` fails on Windows:
> ```bash
> pip install pipwin
> pipwin install pyaudio
> ```

**3. Add your Groq API key**

Open `app.py` and replace:
```python
client = Groq(api_key="YOUR_GROQ_API_KEY_HERE")
```

Get your free key at [console.groq.com](https://console.groq.com)

**4. Add the BolBor logo**
```
bolbor-backend/
  └── static/
        └── logo.png   ← place logo here
```

**5. Run the Flask server**
```bash
python app.py
```
Flask runs at `http://localhost:5000`

---

### 🌐 Frontend Setup

**1. Go to the frontend folder**
```bash
cd frontend
```

**2. Install dependencies**
```bash
npm install
```

**3. Start the dev server**
```bash
npm run dev
```
React runs at `http://localhost:5173`

---

### 🔑 Demo Login Credentials

| Role | Username | Password |
|------|----------|---------|
| Waiter | `waiter1` | `waiter123` |
| Chef | `chef1` | `chef123` |
| Cashier | `cashier1` | `cashier123` |
| Admin | `admin` | `admin123` |

---

## 📁 Project Structure

```
bolbor/
│
├── 📂 backend/
│   ├── app.py              # Flask server — all routes & APIs
│   ├── menu.py             # Restaurant menu with prices
│   ├── ai_parser.py        # Groq AI order parser
│   ├── speak.py            # Text-to-Speech module
│   ├── bill.py             # PDF bill generator
│   ├── main.py             # CLI demo (terminal version)
│   └── static/
│       └── logo.png        # BolBor logo
│
├── 📂 frontend/
│   ├── src/
│   │   ├── api/
│   │   │   └── index.ts    # All Flask API calls
│   │   ├── app/
│   │   │   ├── hooks/
│   │   │   │   └── useVoice.ts         # Reusable voice hook
│   │   │   ├── components/
│   │   │   │   └── VoiceBar.tsx        # Voice status bar
│   │   │   └── pages/
│   │   │       ├── Login.tsx           # Role-based login
│   │   │       ├── Waiter.tsx          # Waiter dashboard
│   │   │       ├── Chef.tsx            # Kitchen display
│   │   │       ├── Cashier.tsx         # Billing & payment
│   │   │       └── Admin.tsx           # Admin dashboard
│   │   └── styles/
│   │       └── index.css               # Global styles
│   ├── package.json
│   ├── tailwind.config.js
│   └── vite.config.ts
│
└── README.md
```

---

## 🎤 Voice Commands Reference

### Waiter
| Command | Action |
|---------|--------|
| `"Hey Bol"` | Wake word — activates mic |
| `"do burger aur ek coke"` | Add 2 burgers and 1 coke |
| `"paanch pizza"` | Add 5 pizzas (Hindi number) |
| `"tran coke apjo"` | Add 3 cokes (Gujarati) |
| `"select table 3"` | Select table 3 |
| `"remove one burger"` | Remove 1 burger from order |
| `"place order"` | Confirm and place the order |
| `"clear cart"` | Empty the cart |

### Chef
| Command | Action |
|---------|--------|
| `"start order 3"` | Begin preparing order #3 |
| `"ready order 5"` | Mark order #5 as ready |
| `"served order 2"` | Mark order #2 as served |
| `"how many orders"` | Get order count summary |
| `"refresh"` | Reload kitchen display |

### Cashier
| Command | Action |
|---------|--------|
| `"select table 4"` | View bill for table 4 |
| `"generate bill"` | Open payment method selector |
| `"pay cash"` | Select cash payment |
| `"pay UPI"` | Show UPI QR code |
| `"clear table"` | Free the table after payment |

---

## 🌐 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/process_voice` | Process voice text with Groq AI |
| `GET` | `/api/orders` | Get all active orders |
| `POST` | `/api/place_order` | Place a new order |
| `POST` | `/api/update_order_status` | Update order status |
| `GET` | `/api/tables` | Get all table statuses |
| `POST` | `/api/book_table` | Book a table |
| `POST` | `/api/free_table` | Clear/free a table |
| `POST` | `/api/generate_bill` | Generate PDF bill |
| `POST` | `/api/get_payment_qr` | Generate UPI QR code |
| `POST` | `/api/speak` | Text-to-speech output |

---

## 🗺️ System Flow

```
Customer speaks order
        ↓
Web Speech API (Chrome)
        ↓
Groq LLaMA 3.3 70B NLP
        ↓
Parsed JSON (items, qty, price)
        ↓
Flask Backend API
        ↓
In-memory store (MongoDB in production)
        ↓
Kitchen Display (Chef) → Order Timer → Mark Ready
        ↓
Cashier → Payment Method → PDF Bill → QR Code
        ↓
Table Cleared ✅
```

---

## 📸 Screenshots

> Login Page · Waiter Dashboard · Kitchen Display · Cashier Billing · Admin Dashboard

*(Add screenshots here)*

---

## 🔮 Future Improvements

- [ ] MongoDB integration for persistent storage
- [ ] WebSocket real-time updates (no polling)
- [ ] Customer-facing menu QR code
- [ ] Inventory management & low stock alerts
- [ ] Daily sales report PDF
- [ ] Customer history & preferences
- [ ] Mobile app (React Native)
- [ ] Multi-restaurant support

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [Groq](https://groq.com) — for the blazing fast LLaMA 3.3 70B API
- [shadcn/ui](https://ui.shadcn.com) — for the beautiful component library
- [Anthropic Claude](https://anthropic.com) — AI assistance during development

---

<div align="center">

Made with ❤️ by **Team BolBor** at Hackathon 2025

**Bol<span>Bor</span> — Speak. Manage. Grow.**

</div>
