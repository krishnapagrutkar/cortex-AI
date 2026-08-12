# Cortex AI

Professional multi-service AI application (frontend + backend).

This repository contains the Cortex AI project: a Vite + React frontend and a Node.js backend composed of multiple services (gateway, auth, agent, chat, billing, etc.). The project has been moved to the repository root so `frontend/` and `backend/` are top-level folders.

---

## Quick links

- Repository: https://github.com/krishnapagrutkar/cortex-AI
- Frontend: `frontend/`
- Backend: `backend/`

---

## Contents

- `frontend/` — Vite + React single-page app
- `backend/` — Node.js services and `docker-compose.yml`
- `screenshots/` — app screenshots (place images here)
- `.gitignore`
- `README.md` (this file)

---

## Summary

Cortex AI is a multi-container (Docker) application. You can run services individually for local development or run everything with Docker Compose.

---

## Prerequisites

- Node.js 16+ (recommended)
- npm or yarn
- Docker & Docker Compose (optional, required for multi-service Docker runs)
- Git

---

## Local development (recommended flow)

1. Clone the repository:

```bash
git clone https://github.com/krishnapagrutkar/cortex-AI.git
cd cortex-AI
```

2. Frontend (run locally):

```bash
cd frontend
npm install
npm run dev
# open the URL printed by Vite (usually http://localhost:5173)
```

3. Backend (run a single service for development):

```bash
# open a new terminal
cd backend/services/gateway
npm install
npm start
```

Repeat for other services as needed (each service has its own `package.json`).

4. Run everything with Docker Compose (optional):

```bash
# requires Docker running
cd backend
docker-compose up --build
```

This builds and starts all configured services.

---

## Environment variables & secrets

- Do NOT commit secrets, API keys, or service account JSON files.
- Use `.env` files for local development and add them to `.gitignore` (already done).
- For CI and production, store secrets in GitHub Secrets or your cloud provider's secret store.

Example `.env` (per-service may differ):

```env
PORT=3000
MONGO_URI=mongodb://localhost:27017/cortex
JWT_SECRET=your_jwt_secret
AWS_ACCESS_KEY_ID=...
AWS_SECRET_ACCESS_KEY=...
```

---

## Tests

- Check each service for tests (not every service includes tests).
- Example (frontend):

```bash
cd frontend
npm test
```

---

## Docker & Deployment

You can deploy using Docker images pushed to a registry (Docker Hub or GHCR) and run them on a server, or use a managed platform (ECS, Cloud Run, Azure, etc.). If you want, I can add a GitHub Actions workflow to build and push images.

---

## Proof of work — Screenshots (inline)

Below are inline screenshots that demonstrate the UI. Place the image files in the `screenshots/` folder with the exact filenames used below so they render directly in GitHub. If the files are not present the image placeholders will appear broken until the images are added.

- App home / Chat UI

  ![Home Chat UI](screenshots/home.png)

- API Guide / PDF preview

  ![API Guide](screenshots/api_guide.png)

- PPT Preview

  ![PPT Preview](screenshots/ppt_preview.png)

- Dashboard analysis view

  ![Dashboard](screenshots/dashboard.png)

- Search results

  ![Search](screenshots/search.png)

If you want, I can import the images attached in this chat into `screenshots/` and commit them for you. Reply `import attachments` and I will add the images and push the commit.

---

## Project structure (short)

- `backend/` — contains `docker-compose.yml`, `gateway/`, and `services/` (agent, auth, chat, billing)
- `frontend/` — Vite React app in `frontend/`

For service-specific README or operation instructions, say `document services` and I will generate README fragments for each service.

---

## Next steps I can do for you

- `import attachments` — import images from this chat into `screenshots/` and commit them.
- `add workflow` — add a starter GitHub Actions workflow (`.github/workflows/ci.yml`) to build/test.
- `document services` — add README sections for each backend service with run instructions.

If you want me to import the chat screenshots now, reply `import attachments` and I'll proceed.
