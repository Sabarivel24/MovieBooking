# 🎬 MovieBooking

A full‑stack movie‑ticket booking application.  
This repository contains three separate apps:

- **backend** – an Express/MongoDB API
- **frontend** – the user‑facing React/Vite UI
- **admin** – an administrator panel built with Vite

Each service lives in its own folder. You can run them independently or together during development.

---

## 🚀 Quick start

### Prerequisites

- Node 18+ / npm 9+
- MongoDB (Atlas or local)
- (optional) Stripe account for payments

---

## 🗂 Folder overview
moviebooking/
├── backend/ ← server, API and database models
├── frontend/ ← public site
└── admin/ ← admin dashboard


Each sub‑project has its own `package.json` and may be started separately.

---

## 🛠 Backend

1. `cd backend`
2. Copy `.env.example` to `.env` and add:

   ```env
   MONGO_URI=<your-mongo-connection-string>
   STRIPE_SECRET_KEY=<your-stripe-secret-key>
3. Ensure .env is ignored (a .gitignore is already added).
4. Install & start:
   npm install
   npm start         # uses nodemon, listens on 5000
5.API routes:

  GET / – health check
  /api/auth – user registration/login
  /api/movies – CRUD for movies
  /api/bookings – create/search bookings
  /uploads – static serve of uploaded images


Frontend & Admin:
Navigate into the respective directory, install dependencies and run the dev server:

cd frontend
npm install
npm run dev        # http://localhost:5173 by default

cd ../admin
npm install
npm run dev        # http://localhost:5174 (or similar)

🔐 Environment & Secrets:
Never commit secrets (API keys, passwords, etc.).
Backend already has a .gitignore ignoring .env, node_modules, uploads.
After accidentally committing a Stripe key, the history was rewritten and pushed (git push --force).
If you pull, get a fresh clone or run git fetch && git reset --hard origin/main.

Common workflows:
1. Add a new endpoint – modify backend/controllers, update the router, restart npm start.
2. Create frontend page – add component under src/pages and route in App.jsx.
3. Upload images – POST to /uploads; they’re saved under backend/uploads and served statically.

 Development tips:
1. Use Postman or a similar tool to exercise the API.
2. When updating database schemas, adjust the Mongoose models in backend/models.
3. The payment flow uses Stripe test keys; swap in live keys only in production.

Deploying:
For a simple deployment you can:

1. Push code to GitHub (already cleaned of secrets).
2. Use services like Heroku/Vercel for each part; set the appropriate environment variables.
3. Ensure MongoDB is accessible from the host.
