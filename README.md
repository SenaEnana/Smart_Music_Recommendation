# 🎵 Smart Music Recommendation Engine

> **A metadata-driven music discovery platform and real-time recommendation API built with FastAPI, SQLite, React (TypeScript), and Tailwind CSS.**

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)

### 🌐 [Live Demo — Try the App Here](https://smart-music-recommendation.vercel.app/)

Smart Music Recommendation Engine computes track similarity using multi-dimensional song metadata—including **genres, moods, thematic tags, explicit flags, and artist attributes**—delivering instant algorithmic matches through a responsive, master-detail web dashboard.

> 📸 **[Insert Screenshot or GIF of the Master-Detail Dashboard Here]**  
> *(Tip: Add a `docs/preview.png` or `demo.gif` showing a selected song on the left and live similarity recommendations updating on the right.)*

---

## 🏗️ System Architecture & How It Works

Instead of relying on heavy collaborative filtering matrices that suffer from the cold-start problem, this engine uses **content-based metadata scoring**:

```text
┌──────────────────────┐      REST / JSON       ┌──────────────────────────┐
│   React + TS Client  │ ◄────────────────────► │     FastAPI Backend      │
│  (Master-Detail UI)  │                        │  (Pydantic Validation)   │
└──────────────────────┘                        └────────────┬─────────────┘
                                                             │ SQL Queries
                                                             ▼
                                                ┌──────────────────────────┐
                                                │     PostgreSQL Database  │
                                                │ (Indexed Track Metadata) │
                                                └──────────────────────────┘
```

---

1. Metadata Extraction & Indexing: Tracks are structured around normalized attributes (genre, mood, theme, artist, explicit).

2. Weighted Similarity Scoring: Selecting a seed track triggers GET /recommendations/?song_id={id}, which evaluates candidate tracks across overlapping metadata dimensions and ranks results by similarity score.

3. Zero-Reload Reactive UI: The frontend fetches ranked matches asynchronously and updates the sticky recommendation drawer without interrupting browsing or pagination state.

```"Note: Initial search/recommendation request may take ~15s while the free-tier backend wakes up."```

---

## ✨ Key Engineering Highlights

* ⚡ Asynchronous REST API: Built with FastAPI and Pydantic v2 for strict request/response schema validation, automatic OpenAPI/Swagger documentation, and configured CORS middleware.

* 🎛️ Master-Detail Split Workspace: Sticky recommendation sidebar pairs seamlessly with a paginated master library (20 tracks/page) for rapid exploration without screen reloads.

* 🔍 Debounced & Auto-Reset Search: Instant filtering by title or artist that automatically restores the default catalog view when the search query is cleared.

* 🎨 Cyberpunk Dark UI: High-contrast Amber & Indigo theme crafted with Tailwind CSS v4 and Lucide icons for clean visual hierarchy.

* 🔒 Public Demo Ready: Configured to run out-of-the-box with a sample seed dataset so reviewers can test the engine immediately without needing private data dumps.

---

```
ℹ️ Disclaimer: This project is strictly an algorithmic 
 recommendation and metadata discovery showcase. It does not 
 host, stream, or distribute copyrighted audio files.
```
---

## 🛠️ Tech Stack

|| **Layer** ||        || **Technologies** ||

|| Backend ||       || Python 3.10+, FastAPI, Uvicorn, Pydantic v2 ||

Database      PostgreSQL(Relational schema with sample seed script)

Frontend      React 18, Vite, TypeScript, Tailwind CSS v4, Lucide React

---

## 📂 Repository Structure

```Plaintext
├── backend/
│   ├── app/
│   │   ├── routers/         # Modular API endpoints (songs, search, recommendations)
│   │   ├── crud/            # Optimized SQLite query & scoring handlers
│   │   ├── schemas/         # Pydantic v2 data validation models
│   │   └── database.py      # Database connection & session management
│   ├── main.py              # FastAPI app initialization & CORS setup
│   └── seed_sample.py       # Script to generate sample demo tracks (SQLite)
│
├── frontend/
│   ├── src/
│   │   ├── components/      # Reusable UI modules (Header, SongTable, RecommendationList)
│   │   ├── views/           # Master-detail page layouts (SongDiscoveryView)
│   │   ├── services/        # Typed Fetch API client (api.ts)
│   │   └── types.ts         # Shared TypeScript interfaces
│   └── package.json
│
└── README.md
```

---

## 🗺️ Roadmap & Future Improvements

* [ ] Add audio feature vector support (BPM, key, energy) alongside categorical metadata

* [ ] Dockerize frontend and backend with docker-compose for one-command deployment

* [ ] Add unit tests with pytest for similarity scoring edge cases

---

## 📝 License

Distributed under the MIT License. See LICENSE for more information.

---

## Author

Sena Adane