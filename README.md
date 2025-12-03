# AstroPlanner 🌙🔭
AstroPlanner is a full-stack web app for planning and tracking astronomy observing sessions. It includes a React (Vite) frontend and a FastAPI backend with a relational database.
## Demo Video
https://www.youtube.com/watch?v=WGe1oc-r15o
## Tech Stack
- **Frontend:** React + TypeScript + Vite
- **Backend:** FastAPI (Python)
- **Database:** SQLAlchemy ORM (SQLite by default)
- **Auth:** JWT-based authentication
- **External integrations:** Weather + geocoding/target lookup (via backend API routes)

## Key Features
- User authentication (register/login) and protected routes
- CRUD for core entities (sessions, logs, locations, etc.)
- Planner-style endpoints for observation/target planning
- Weather + geocoding endpoints used by the planner/locations features
- Auto-generated API docs via FastAPI OpenAPI (`/docs`)

## Repo Structure
```
astroplanner-clean/
  backend/                 # FastAPI app
  frontend/                # React/Vite app
  docker-compose.yml       # Run full stack
```

---

# ✅ Run with Docker (Recommended)
From the repo root:

```bash
docker compose up --build
```

Then open:
- Frontend: http://localhost:5173
- Backend API docs: http://localhost:8000/docs

Stop:
```bash
Ctrl+C
docker compose down
```

---

# Run Locally (No Docker)

## Backend (FastAPI)
From `backend/`:

```powershell
py -m venv .venv
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\.venv\Scripts\Activate.ps1

python -m pip install --upgrade pip
pip install -r requirements.txt

uvicorn app.main:app --reload
```

Backend docs:
- http://127.0.0.1:8000/docs

## Frontend (Vite)
From `frontend/`:

```powershell
npm install
npm run dev
```

Frontend:
- http://localhost:5173

### Frontend → Backend base URL
Configure your frontend API base URL using an environment variable:

- **Docker compose sets:** `VITE_API_BASE_URL=http://localhost:8000`
- Locally, you can set it for the current PowerShell session:
```powershell
$env:VITE_API_BASE_URL="http://localhost:8000"
npm run dev
```

> If your frontend currently hardcodes the API URL, switch it to:
> `import.meta.env.VITE_API_BASE_URL ?? "http://localhost:8000"`

---


# API Documentation
FastAPI auto-generates OpenAPI docs:
- Swagger UI: `/docs`
- OpenAPI JSON: `/openapi.json`

---

# Testing (if enabled)
From `backend/`:
```bash
pytest
```

---


---

# Authors / Contributions
- Ben Walsh 
