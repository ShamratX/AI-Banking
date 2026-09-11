# AI Banking (Banker Expert)

npm-workspace app: **Express** backend + **React** frontend for authenticated users, wallet-oriented reporting, and LLM-assisted insights.

## Features

- JWT auth: register, login, profile/email/password updates, delete, preferences
- Report pipeline via Moralis wallet data + action / P&amp;L style report services
- React UI: home, profile, protected report page
- Jest tests under the backend workspace

## How it works

Root `npm run dev` starts backend and frontend via `concurrently`. Frontend talks to the API (report UI targets `http://localhost:8000`). Backend connects MongoDB, authenticates with JWT, and builds reports from wallet services. LLM calls in code target an Ollama-compatible HTTP endpoint (not a third-party TinyLlama cloud key in the JS path).

## Requirements

- Node.js 18+
- MongoDB
- Moralis API access for wallet features used by the backend

## Quick start

```bash
git clone https://github.com/ShamratX/AI-Banking.git
cd AI-Banking
cp .env.example .env
npm install
npm run dev
```

- Backend: `http://localhost:8000` (port is set in `backend/src/api.js`)
- Frontend: CRA default (usually `http://localhost:3000`)

```bash
npm run start:backend
npm run start:frontend
npm --workspace backend test
```

## Config (env names)

Documented in `.env.example`: `MONGO_URI`, `JWT_SECRET`, `TINYLLAMA_API_KEY`, `COINGECKO_API_KEY`, `NODE_ENV`, `PORT`, optional SMTP/Redis keys.

**Used by backend code today:** `MONGO_URI`, `JWT_SECRET`, `MORALIS_API_KEY` (add to `.env` even if not listed in the example).

Treat example-only keys as optional until wired in code.

## Main API routes

| Method | Path | Notes |
|--------|------|-------|
| POST | `/auth/register` | Create account |
| POST | `/auth/login` | Login |
| PATCH | `/auth/update` | Auth required |
| PATCH | `/auth/updateEmail` | Auth required |
| PATCH | `/auth/updatePassword` | Auth required |
| PATCH | `/auth/updatePreferences` | Auth required |
| DELETE | `/auth/delete` | Auth required |
| POST | `/report` | Auth required |
| POST | `/user/preferences` | Auth required |

## Project structure

```text
backend/     # Express API, services, tests
frontend/    # React (CRA)
readmeFiles/ # diagrams
package.json # workspaces root
```

## Limitations

- `PORT` in `.env` may not override the hardcoded `8000` listen port.
- Some README/example AI/market keys are not referenced in backend JS; Moralis + Ollama paths are.
- Requires local/remote Ollama (or compatible) if LLM insights are expected.

## License

MIT (per project docs).
