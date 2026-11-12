# 🎵 Smart Music Recommendation Engine

> **A metadata-driven music discovery platform and real-time recommendation API built with FastAPI, SQLite, React (TypeScript), and Tailwind CSS.**

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)

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
                                                │     SQLite Database      │
                                                │ (Indexed Track Metadata) │
                                                └──────────────────────────┘