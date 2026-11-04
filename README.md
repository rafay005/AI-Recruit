
AI Recruit
An AI hiring platform that takes a job from post to hired. It ranks CVs by meaning, not just keywords, runs a personalised AI interview with every candidate, and can make hiring decisions automatically, while HR always keeps the final say.

Runs fully offline with a local open-source model. No paid API required.

Features
Meaning-based ranking: hybrid search (keywords + embeddings) matches "edited YouTube videos in Premiere Pro" to "video editing". Every score shows the CV line behind it.
CV reading: PDF, Word and scanned CVs (OCR), turned into structured data automatically.
Personalised AI interviews: questions are built from the job's responsibilities and each candidate's CV, so no two interviews are the same. Voice or typed answers.
Hands-free hiring: per-job thresholds invite strong CVs to interview and select top interview scores, first come first served until openings are filled. Every decision is logged with its reason.
Pipeline board: drag candidates between Under review, Shortlisted, Interview, Selected and Rejected.
Dashboard and analytics: hiring funnel, score distributions, skills demand vs supply, activity feed.
Tech stack
Layer	Technology
Backend	Python 3.11, FastAPI, SQLAlchemy, Alembic
Database	PostgreSQL
Frontend	Next.js 16, React 19, TypeScript, Tailwind CSS 4
AI / search	BGE-small embeddings (fastembed, ONNX Runtime), BM25, RapidOCR
Optional	Anthropic Claude or OpenAI for AI-written text
Quick start
Requirements: Python 3.11, Node.js 20+, PostgreSQL.

CREATE USER recruit_user WITH PASSWORD 'change-me';
CREATE DATABASE recruitment OWNER recruit_user;
# Backend
cd backend
python -m venv venv
venv\Scripts\activate        # macOS/Linux: source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env         # set DATABASE_URL and SECRET_KEY
alembic upgrade head
uvicorn app.main:app --reload --port 8000
# Frontend
cd frontend
npm install
npm run dev
Open http://localhost:3000 and register an HR account. API docs: http://localhost:8000/docs. The first start downloads the search model (~65 MB); after that it works offline.

Project structure
backend/    FastAPI app (api/, services/, models/), migrations, tests
frontend/   Next.js app (HR and candidate portals)
docs/       Full guide: architecture, database, API, deployment
Documentation
See docs/GUIDE.md for how ranking, interviews and automation work, the database schema, every API endpoint, configuration, deployment and privacy notes.

Credits
Built with the help of Claude Code.

