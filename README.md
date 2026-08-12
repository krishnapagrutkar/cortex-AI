# Cortex AI

A multi-service AI application with frontend and backend services.

## Overview

This repository contains the full Cortex AI project: a frontend (Vite + React) and a multi-service backend (Node.js services with Docker). The project was originally inside the `1.cortexAI` folder; it has been moved to the repository root so `frontend/` and `backend/` appear directly at the top level.

## Repository structure

- `backend/` — API gateway and microservices (auth, agent, chat, billing, etc.)
- `frontend/` — Vite + React web client
- `.gitignore` — ignored files
- `README.md` — this file

(If you see a `1.cortexAI/` folder, its contents should be moved to the repo root. See the "Restructure" section below.)

## Installation (development)

Requires Node.js (16+ recommended), Docker (optional), and npm/yarn.

1. Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/cortex-AI.git
cd cortex-AI
```

2. Install frontend dependencies and run the dev server:

```bash
cd frontend
npm install
npm run dev
# frontend will run on the port shown by Vite (usually http://localhost:5173)
```

3. Install backend dependencies and run (example: run gateway and agent services):

```bash
# in a new terminal
cd backend
# example for running one service locally (inspect package.json in each service)
cd services/gateway
npm install
npm start
```

Or start everything via Docker Compose (if Docker is installed):

```bash
cd backend
docker-compose up --build
```

## Environment and secrets

- Do NOT commit secrets (service account keys, `.env` files). Use `.gitignore` to exclude them.
- For CI/CD or deployment, store secrets in GitHub Actions Secrets or your cloud provider's secret manager.

## Running tests

Check each service for tests (many services may not include automated tests). For example:

```bash
cd frontend
npm test
```

## CI/CD (GitHub Actions)

You can add a GitHub Actions workflow under `.github/workflows/ci.yml` to lint, build, and test the frontend and backend. If you want, I can add a starter workflow that:

- Installs Node
- Runs `npm ci` and `npm test` for frontend
- Builds Docker images and pushes to GHCR/Docker Hub (requires registry secrets)

Say `add workflow` if you want me to create the workflow file.

## Deployment

Choose a target: VPS with Docker Compose, AWS ECS, Google Cloud Run, Azure App Service, or Vercel/Netlify (frontend only).

Example: deploy via Docker images to a server (high level):

1. Build images locally or in CI.
2. Push images to a registry (Docker Hub or GitHub Container Registry).
3. Pull and run images on your server with Docker Compose.

If you want an automated GitHub Action to build/publish images and SSH-deploy to a server, I can add one.

## Restructure (move files to repo root)

If the project is currently under `1.cortexAI/`, run this from the repository root to move everything out so `frontend/` and `backend/` are at the top level:

```powershell
# from repo root
Move-Item .\1.cortexAI\* . -Force -Verbose
Remove-Item .\1.cortexAI -Recurse -Force
```

Commit and push after verifying the layout:

```bash
git add -A
git commit -m "Move project files to repo root"
git push
```

I can run this restructure and commit for you — reply `move now` and I'll perform it.

## Screenshots

Add screenshots to a `screenshots/` folder and reference them in this README. Example:

```md
### Screenshot: App home
![App home](screenshots/home.png)
```

Please put image files in `screenshots/`.

## Notes and next steps

- I can move project files to root now and update the repo (will commit and push).
- I can add a GitHub Actions CI workflow and a Docker-based deployment pipeline.
- I can also generate a `README.md` section for each service (gateway, auth, agent, chat) if you want deeper documentation.

Tell me which of the following to do next:

- `move now` — I will move files from `1.cortexAI` to repo root, commit, and push.
- `add workflow` — I will add a starter GitHub Actions workflow.
- `document services` — I will add per-service README sections.

If you want the restructure now, reply `move now`.