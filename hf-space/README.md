---
title: Skill Optimizer API
emoji: 🔧
colorFrom: blue
colorTo: indigo
sdk: docker
app_port: 7860
pinned: false
license: mit
---

# Skill Optimizer API

Free Hugging Face Spaces deployment of the Self-Improving Agent Skills backend.

A FastAPI + Google ADK multi-agent engine that runs/analyzes/mutates your agent skills with Gemini.
Requires a Gemini API key, entered per-request from the frontend (never stored server-side).

- **Health check:** `GET /health` -> `{"status":"healthy"}`
- **Docs:** `GET /docs` (OpenAPI / Swagger UI)
- **Examples:** `GET /api/examples` (sibling skills bundled under `agent_skills/`)

## Point a frontend at this API

```
NEXT_PUBLIC_API_URL=https://<your-space-name>.hf.space
```

If the backend is used by the frontend in this repo, build it with that env var set:
the frontend falls back to `http://localhost:8891` when it is unset.

## Project layout

```
hf-space/
├── Dockerfile              # python:3.12-slim + uvicorn on $PORT (7860 on HF)
└── agent_skills/
    ├── backend/            # app.py, adk_optimizer.py, requirements.txt
    ├── project-graveyard/  # bundled example skills (serve /api/examples)
    ├── commit-archaeologist/
    └── ...
```