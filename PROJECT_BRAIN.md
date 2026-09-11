# PROJECT_BRAIN — AI-Banking

## Purpose

Personal “banker-style” reporting app with auth + wallet analytics. Monorepo name in package.json: `my-banker`.

## Architecture

- Workspaces: `frontend` (react-scripts), `backend` (Express on port 8000)
- Auth service modules + JWT middleware
- Report controller → generateReport / P&L / action report services
- Wallet layer uses Moralis SDK utilities
- LLM: HTTP to `ollama:11434` style endpoint with a local model name in code

## Workflow

1. Mongo up; set `MONGO_URI`, `JWT_SECRET`, `MORALIS_API_KEY`
2. `npm install` at root
3. `npm run dev`
4. Register/login in UI; open `/report`

## Gotchas

- Do not document CoinGecko/TinyLlama as live integrations unless code is updated to use them
- Keep frontend API base URL aligned with backend port
- Diagram asset: `readmeFiles/Diagram.png`

## Rebuild notes

Preserve workspace scripts; backend tests use Jest + mongodb-memory-server where configured.
