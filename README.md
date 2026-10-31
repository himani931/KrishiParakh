<div align="center">

# 🌾 KrishiParakh (कृषिपरख)

### _Smart Procurement. Transparent MSP. Empowered Farmers._

[![Smart India Hackathon](https://img.shields.io/badge/SIH-National%20Hackathon-orange.svg?style=for-the-badge)](https://www.sih.gov.in/)
[![React](https://img.shields.io/badge/Frontend-React%2018%20%2B%20Vite-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Backend-Node.js%20%7C%20Express-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Tailwind CSS v4](https://img.shields.io/badge/Styling-Tailwind%20CSS%20v4-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![MongoDB](https://img.shields.io/badge/Database-MongoDB%20Atlas-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

<p align="center">
  A digital agricultural procurement and yard-management ecosystem engineered to eliminate physical mandi choke points, guarantee algorithmic MSP compliance, and deliver tamper-evident settlement ledgers.
</p>

[Explore Key Features](#-key-features) • [System Architecture](#-system-architecture) • [Getting Started](#-getting-started) • [API Documentation](#-api-endpoints) • [Security & Audit](#-tamper-evident-audit-trail)

</div>

---

## 📌 Problem Statement

Agricultural procurement across physical APMC mandis often suffers from critical operational bottlenecks:

- **Severe Congestion & Gridlock**: Farmers wait in unscheduled physical queues outside mandi gates for days, leading to crop degradation and steep logistical costs.
- **Opaque Quality & Price Deductions**: Arbitrary dockage calculations on moisture and grade variance reduce farmers' effective take-home pay below statutory Minimum Support Price (MSP).
- **Paper-Based Fraud & Discrepancies**: Manual weighbridge slips and offline receipts create audit vulnerabilities, payment delays, and untraceable disputes.

**KrishiParakh** addresses these challenges by transforming physical procurement yards into synchronized, transparent, and digitally audited fulfillment centers.

---

## 🚀 Key Features

### 📍 Intelligent Mandi Discovery & Telemetry

- Interactive geospatial mapping powered by **Leaflet** and OpenStreetMap.
- Live capacity indicators across three states: `Available`, `Limited`, and `Congested`.
- Dynamic wait-time estimates calculated from active weighbridge throughput.

### 🎫 Dynamic QR Slot Scheduling

- Algorithmic arrival-window generation to prevent queue build-up.
- Tamper-proof, client-rendered QR gate passes containing cryptographically validated payload tokens.
- Single-scan automated check-in at mandi perimeter checkpoints.

### ⚖️ Digital Weighbridge & Grade-Based Payout Engine

- Direct operator terminal for logging gross, tare, and net weights.
- Automated moisture content deductions calibrated against official government grading schedules.
- Guaranteed statutory MSP baseline calculations with zero manual tampering.

### 🎙️ KrishiParakh Saathi (Multilingual Voice AI)

- Context-aware conversational AI assistant fluent in **Hindi** and **English**.
- Supports both speech-to-text queries and voice responses to bridge digital literacy barriers.
- Answers real-time questions regarding crop-specific MSP schedules, gate pass validity, and mandi rush.

### 🛡️ Tamper-Evident Audit Ledger

- Append-only ledger recording every phase: `SLOT_BOOKED`, `GATE_ENTRY`, `WEIGHMENT_COMPLETED`, and `DISBURSEMENT_INITIATED`.
- Cryptographic hash verification linking sequential events for dispute-free appellate auditing.

### 🧾 Instant Direct Benefit Transfer (DBT) Invoices

- Browser-level optimized PDF invoice and receipt rendering.
- Compliant with standard accounting formats including itemized deductions, gross weighbridge readings, and bank settlement identifiers.

---

## 🔄 Procurement Lifecycle

```text
[Farmer App]                   [Gate Checkpoint]              [Weighbridge Station]           [Settlement Ledger]
      │                                │                                │                               │
      ├──── Book Slot & Get QR ───────►│                                │                               │
      │                                ├── Verify QR Token ────────────►│                               │
      │                                │   (Status: GATE_ENTRY)         │                               │
      │                                │                                ├── Log Gross/Tare Weight ─────►│
      │                                │                                │   Log Moisture & Quality      │
      │                                │                                │                               ├── Calc MSP Payout
      │                                │                                │                               ├── Append Audit Hash
      │◄─── Instant DBT Receipt ───────┴────────────────────────────────┴───────────────────────────────┤
```

---

## 🛠️ Tech Stack

| Layer                    | Technologies                           |
| :----------------------- | :------------------------------------- |
| **Frontend Framework**   | React 18+ (Vite), React Router DOM v6+ |
| **Styling & Icons**      | Tailwind CSS v4, Lucide React          |
| **Geospatial & Visuals** | Leaflet, React-Leaflet, OpenStreetMap  |
| **Client Utilities**     | Axios, `qrcode.react`, Web Speech API  |
| **Backend Runtime**      | Node.js (v18+ LTS), Express.js         |
| **Database & ODM**       | MongoDB Atlas, Mongoose ODM            |
| **Security & Auth**      | CORS, Dotenv, SHA-256 Ledger Hashing   |

---

## 📂 Project Architecture

```text
KrishiParakh/
├── client/                     # Frontend React Application
│   ├── public/                 # Static assets & map markers
│   ├── src/
│   │   ├── components/         # Reusable UI primitives
│   │   │   ├── MandiMap.jsx    # Geospatial yard visualizer
│   │   │   └── Navbar.jsx      # Global navigation header
│   │   ├── pages/              # Routed application views
│   │   │   ├── AuthSelect.jsx          # Role switcher (Farmer / Operator)
│   │   │   ├── FarmerDashboard.jsx     # Active bookings & quick actions
│   │   │   ├── FindMandi.jsx           # Yard discovery & slot reservation
│   │   │   ├── KisanSaathi.jsx         # Multilingual AI assistant
│   │   │   ├── Landing.jsx             # Platform homepage
│   │   │   ├── MandiDashboard.jsx      # Operator scale & yard terminal
│   │   │   ├── PaymentReceipt.jsx      # Digital DBT slip & PDF generator
│   │   │   ├── QRToken.jsx             # Dynamic gate token modal
│   │   │   ├── TrackProcurement.jsx    # Real-time state visualizer
│   │   │   └── TransactionLedger.jsx   # Cryptographic audit explorer
│   │   ├── App.jsx             # Route definitions
│   │   ├── index.css           # Tailwind v4 configuration & map styles
│   │   └── main.jsx            # DOM entry
│   ├── package.json
│   └── vite.config.js
│
├── server/                     # Backend REST API
│   ├── models/                 # Database Schemas
│   │   ├── Mandi.js            # Yard metadata, coordinates, capacity
│   │   ├── SlotRequest.js      # Booking state machine & weighment payload
│   │   └── LedgerEvent.js      # Append-only cryptographic audit event
│   ├── routes/                 # API controllers
│   │   ├── aiRoutes.js         # Kisan Saathi AI proxy
│   │   └── mandiRoutes.js      # Procurement, check-in, & scale operations
│   ├── index.js                # Express app setup & DB connection
│   ├── seed.js                 # Sample mandi & slot dataset
│   └── package.json
│
└── README.md
```

---

## ⚡ Getting Started

### Prerequisites

- **Node.js**: `v18.x` or higher
- **npm**: `v9.x` or higher (or `pnpm` / `yarn`)
- **MongoDB**: A running local instance or a [MongoDB Atlas](https://www.mongodb.com/atlas) cluster URI

---

### Installation & Local Setup

#### 1. Clone the Repository

```bash
git clone https://github.com/your-username/KrishiParakh.git
cd KrishiParakh
```

#### 2. Configure the Backend

```bash
cd server
npm install
```

Create a `.env` file inside the `server/` directory:

```env
PORT=5000
MONGODB_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/krishiparakh?retryWrites=true&w=majority
FRONTEND_URL=http://localhost:5173
```

Seed the database with test yards and baseline MSP schedules:

```bash
node seed.js
```

Start the API server:

```bash
npm run dev
# Server running at http://localhost:5000
```

#### 3. Configure the Frontend

Open a separate terminal session:

```bash
cd client
npm install
```

Create a `.env` file inside the `client/` directory:

```env
VITE_API_BASE_URL=http://localhost:5000/api
```

Start the Vite development server:

```bash
npm run dev
# Application running at http://localhost:5173
```

---

## 📡 API Reference

### Mandi & Booking Endpoints (`/api/mandis`)

| Method | Endpoint                         | Description                                                      |
| :----- | :------------------------------- | :--------------------------------------------------------------- |
| `GET`  | `/api/mandis`                    | Fetch all procurement yards with live capacity indices           |
| `GET`  | `/api/mandis/:id`                | Fetch detailed metrics for a specific yard                       |
| `POST` | `/api/mandis/book-slot`          | Reserve an arrival slot and generate a token                     |
| `GET`  | `/api/mandis/track/:token`       | Fetch real-time progress for an active token                     |
| `POST` | `/api/mandis/operator/weighment` | Submit weighbridge metrics, moisture %, and calculate MSP payout |

### Audit Ledger Endpoints (`/api/mandis/ledger`)

| Method | Endpoint                        | Description                                   |
| :----- | :------------------------------ | :-------------------------------------------- |
| `GET`  | `/api/mandis/ledger`            | Fetch complete immutable audit log            |
| `GET`  | `/api/mandis/ledger/verify/:id` | Cryptographically verify state hash integrity |

### AI Assistant Endpoints (`/api/ai`)

| Method | Endpoint        | Description                                                |
| :----- | :-------------- | :--------------------------------------------------------- |
| `POST` | `/api/ai/query` | Process bilingual natural language queries (Hindi/English) |

---

## 🔒 Tamper-Evident Audit Trail

Every operational step generates an immutable state record chained to the previous state using SHA-256 block hashing:

```json
{
  "eventId": "EVT-8921-X9",
  "tokenId": "KP-WHEAT-2026-041",
  "eventType": "WEIGHMENT_CERTIFIED",
  "timestamp": "2026-10-31T17:02:18.412Z",
  "metadata": {
    "grossWeightKg": 4200,
    "tareWeightKg": 1200,
    "netWeightKg": 3000,
    "moisturePercentage": 11.4,
    "payableAmountINR": 68250
  },
  "previousHash": "a4f89d34e9bc3...e411",
  "currentHash": "7f8b901cd43ea...991a"
}
```

Any retrospective modification to weighment figures, moisture deductions, or MSP payment amounts breaks the hash chain, immediately raising discrepancy flags during audit inspection.

---

## 👥 Contributors

Built with dedication for the **Smart India Hackathon (SIH)**.

- **Team Name**
  - Lead Developer / System Architect — [Your Name](https://github.com/your-profile)
  - Frontend & UI/UX Engineer — [Member Name](https://github.com/your-profile)
  - Backend & Database Specialist — [Member Name](https://github.com/your-profile)
  - AI & Integration Engineer — [Member Name](https://github.com/your-profile)

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.
