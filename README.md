# EduMartX — Student Marketplace (v1)

Full-stack campus marketplace: registration, profiles, buy/sell, notes upload, search, real-time chat, and Razorpay payments.

## Quick start

**Terminal 1 — API**

```bash
cd server
cp .env.example .env
npm install
npm run dev
```

**Terminal 2 — App**

```bash
cd EduMart
cp .env.example .env
npm install
npm run dev
```

- **App:** http://localhost:5173  
- **API:** http://localhost:5000  

If MongoDB is not installed locally, the server uses an **in-memory database** (data resets when the server stops).

**Demo admin** (empty DB): `admin@college.edu` / `admin123`

## MVP features

| Feature | Status |
|---------|--------|
| Email + Google login (JWT) | ✅ |
| Guided onboarding → register | ✅ |
| Student profile | ✅ |
| Sell / buy / marketplace | ✅ |
| Notes PDF upload | ✅ |
| Search & filter | ✅ |
| Buyer–seller chat (Socket.io) | ✅ |
| Razorpay (or demo checkout) | ✅ |
| Admin listing approval | ✅ |

**Version 2 (planned):** AI notes quality checker, trust scores, full AI pricing engine.

## Project structure

```
EduMart/
  EduMart/     # React + Vite frontend
  server/      # Express + MongoDB API
```

## Environment

| App | File | Key variables |
|-----|------|----------------|
| Server | `server/.env` | `JWT_SECRET`, `MONGODB_URI`, `GOOGLE_CLIENT_ID`, `CLOUDINARY_*`, `RAZORPAY_*`, `ADMIN_EMAIL` |
| Client | `EduMart/.env` | `VITE_GOOGLE_CLIENT_ID`, `VITE_SOCKET_URL` |

Set `ADMIN_EMAIL` to your email when registering to receive admin access.

## Main routes

| Route | Page |
|-------|------|
| `/` | Home |
| `/get-started` | Onboarding wizard |
| `/marketplace` | Browse listings |
| `/product/:id` | Product details & checkout |
| `/sell` | Create listing (auth) |
| `/dashboard`, `/profile`, `/chat` | User area |
| `/admin` | Admin moderation |

## Sell flow

Log in → **Sell** → upload images/PDF → set price → **Publish** → admin approves → listing goes live on the marketplace.

## Payments

Without Razorpay keys in `server/.env`, checkout runs in **demo mode**. Add test keys for UPI, cards, and net banking.
