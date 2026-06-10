# PitchForge AI

PitchForge AI is a production-ready SaaS prototype that converts raw startup ideas into investor-ready pitch reports with AI-generated pitch sections, scoring, SWOT analysis, competitor analysis, valuation estimates, history, and PDF export.

## Stack

- Frontend: React, Vite, Tailwind CSS, Framer Motion
- Backend: FastAPI, Pydantic, ReportLab
- Database: MongoDB with in-memory fallback for demos
- AI: Gemini API with deterministic fallback generation

## Run locally

```bash
cd backend
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
copy .env.example .env
uvicorn main:app --reload
```

```bash
cd frontend
npm install
copy .env.example .env
npm run dev
```

Frontend runs on `http://localhost:5173`; backend runs on `http://localhost:8000`.

## Environment

Set `GEMINI_API_KEY` and `MONGODB_URI` in `backend/.env` for full production behavior. Without them, the app still runs in demo mode with in-memory history and structured fallback pitch generation.

## Deployment

- Vercel: deploy `frontend/`, set `VITE_API_URL` to the backend URL.
- Render: use `render.yaml` or create a Python web service from `backend/`.
- Railway: use `railway.json` from the repo root or deploy the `backend/` directory directly.

## API

- `POST /generate-pitch`
- `POST /generate-swot`
- `POST /generate-score`
- `POST /generate-valuation`
- `POST /generate-competitors`
- `GET /history`
- `POST /export-pdf`

`/api/...` aliases are also available for deployment routing flexibility.
