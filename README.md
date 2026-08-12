docker-compose up --build
# Cortex AI — Multi-Agent AI Platform

This repository contains a production-style Multi-Agent AI Platform built with the MERN stack (MongoDB, Express, React, Node) and a microservices architecture. The contents here summarize the project's purpose, architecture, core features, and development roadmap — based directly on the tutorial reference you provided.

## About

Cortex AI is a multi-agent platform designed to combine several specialized AI agents into a single application that can answer questions, fetch and summarize web data, analyze documents, and assist with coding tasks. It demonstrates how to build a scalable, production-ready system using microservices, vector search (Qdrant), caching/memory (Redis), and agent orchestration (LangGraph + LangChain). The frontend provides a modern chat-style UX built with React and Redux Toolkit that streams AI responses and shows conversation history.

## Key Project Features

- Multi-Agent System: orchestrated with LangGraph and LangChain to coordinate multiple agents:
  - Chat Agent — general conversational responses
  - Search Agent — real-time web data retrieval and summarization (RAG)
  - Coding Agent — assists with code tasks and generation
- Vector Search: Qdrant is used as the vector database for retrieval-augmented generation (RAG).
- Caching & Memory: Redis is used for session management and short-term AI conversation memory.
- Authentication: Firebase auth with JWTs to secure user sessions.
- UI/UX: Frontend built with React.js + Redux Toolkit, delivering a responsive sidebar, streaming AI responses, and markdown rendering.
- Infrastructure: Docker for containerization and guidance for AWS deployment.

## Core Architecture and Functionality

- Microservices: The backend is split into independent services (Auth Service, Chat Service, Agent Service, Billing, etc.) with an API Gateway routing requests. Each service runs separately and may be containerized.
- Agent Orchestration: LangGraph structures agent workflows. A router agent directs queries to specialized agents (e.g., search, code) and aggregates their outputs.
- Vector Retrieval: Documents and embeddings are stored in Qdrant to enable efficient semantic search used by RAG flows.
- Redis Sessions & Memory: Redis stores session state and short-term conversation memory enabling continuity across requests and services.

## Development Roadmap (high level)

1. Initialize API Gateway and base services (Auth, Chat).
2. Implement LangGraph workflows and LangChain connectors for agent logic.
3. Integrate Qdrant for vector storage and retrieval.
4. Add Redis-based session and memory handling.
5. Build frontend (React + Redux) with streaming UI for live AI responses and conversation history.
6. Add Docker Compose for local multi-service orchestration and CI pipeline for build/test and image publishing.

## How core pieces work (answers)

- How does the Search Agent fetch data?
  - The Search Agent issues real-time web fetches using external search or scraping connectors, then converts retrieved content into embeddings and queries Qdrant to perform similarity search. Results are passed into the RAG pipeline to generate informed responses.

- What is the role of LangGraph?
  - LangGraph defines the agentic logic and workflow graphs: it composes multiple agents, defines routing rules, and controls decision-making so agents collaborate rather than operate independently. It enables complex, conditional flows and chaining between agents.

- How are sessions managed with Redis?
  - Redis stores short-lived session data (user session tokens, conversation context pointers, and in-memory chat history). Services read/write session keys so requests routed through the gateway preserve continuity without heavy DB reads.

## Project Scope & Use Cases

- Build conversational assistants that combine live web knowledge with private documents via RAG.
- Automate developer tasks using the Coding Agent (generate, explain, and refactor code).
- Provide secure multi-user access with Firebase + JWT.

## Where to start (developer quick-start)

1. Clone the repo and inspect `frontend/` and `backend/`.
2. Start individual services for development (each service has `package.json`).
3. For multi-service local runs, use `docker-compose` from `backend/`.

If you want a detailed per-service README, run commands, or a CI workflow next, ask `document services` or `add workflow`.

## Proof of work — Screenshots

Place screenshots in `screenshots/` with these filenames so they render inline:

- `home.png` — App home / Chat UI
- `api_guide.png` — API Guide / PDF preview
- `ppt_preview.png` — PPT preview
- `dashboard.png` — Dashboard analysis view
- `search.png` — Search results

Reply `import attachments` if you want me to import the chat images into `screenshots/` and commit them. Alternatively, upload images into the `screenshots/` folder now (drag-and-drop in VS Code) with these filenames:

- `home.png`
- `api_guide.png`
- `ppt_preview.png`
- `dashboard.png`
- `search.png`

After you upload, reply `uploaded` and I will add/commit/push the images so they render inline in the README.

