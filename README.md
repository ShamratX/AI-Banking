# AI Banking (Banker Expert)

Personal financial assistant that turns user data into banker-style reports. Modular Node.js backend + React frontend.

## Features

- JWT auth (register, login, profile updates)
- AI-assisted financial reports
- Crypto wallet / market data hooks (CoinGecko)
- Modular Express services with Jest tests
- React UI (home, profile, reports)

## Requirements

- Node.js 18+
- MongoDB (Atlas or local)
- Git

## Quick start

```bash
git clone https://github.com/ShamratX/AI-Banking.git
cd AI-Banking
cp .env.example .env
npm install
npm run dev
```

- Backend: `http://localhost:8000`
- Frontend: React default (usually `http://localhost:3000`)

Fill `.env` before first run (see Config).

## Config

Copy `.env.example` → `.env` at the repo root:

| Variable | Purpose |
|----------|---------|
| `MONGO_URI` | MongoDB connection string |
| `JWT_SECRET` | JWT signing secret |
| `TINYLLAMA_API_KEY` | AI report engine |
| `COINGECKO_API_KEY` | Market / wallet data |
| `NODE_ENV` | `development` / `production` |

Never commit a real `.env`.

## Usage

| Command | What it does |
|---------|----------------|
| `npm run dev` | Backend + frontend together |
| `npm run start:backend` | Backend only |
| `npm run start:frontend` | Frontend only |
| `npm --workspace backend test` | Backend Jest tests |

### Main API routes

| Method | Path | Notes |
|--------|------|-------|
| POST | `/auth/register` | Create account |
| POST | `/auth/login` | Login |
| PATCH | `/auth/update` | Update user (auth) |
| PATCH | `/auth/updateEmail` | Change email (auth) |
| PATCH | `/auth/updatePassword` | Change password (auth) |
| DELETE | `/auth/delete` | Delete account (auth) |
| POST | `/report` | Generate report (auth) |
| POST | `/user/preferences` | User preferences (auth) |

## Project structure

```text
AI-Banking/
├── backend/          # Express API, services, tests
├── frontend/         # React app
├── readmeFiles/      # Diagrams / assets
├── .env.example
└── package.json      # npm workspaces root
```

## Notes

- Backend listens on port **8000** (`backend/src/api.js`).
- Architecture overview: [readmeFiles/Diagram.png](readmeFiles/Diagram.png)

## License

MIT
