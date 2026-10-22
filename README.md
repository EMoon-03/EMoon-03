<div align="center">

# Hey, I'm Eddie 👋

### AI/ML Engineer · Data Engineering · Software Engineering

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=16&pause=1200&color=14B8A6&center=true&vCenter=true&width=650&lines=Machine+Learning+%C2%B7+LLM+Apps+%C2%B7+Data+Pipelines+%C2%B7+Cloud;Python+%C2%B7+TypeScript+%C2%B7+SQL+%C2%B7+React+%C2%B7+AWS;Turning+models+into+software+people+actually+use" alt="Typing SVG" />

<br>

<a href="https://www.linkedin.com/in/edward-moon-972007237"><img src="https://img.shields.io/badge/LinkedIn-0F766E?style=flat-square&logo=linkedin&logoColor=white" /></a>
<a href="mailto:sungjune.moon@gmail.com"><img src="https://img.shields.io/badge/Gmail-0F766E?style=flat-square&logo=gmail&logoColor=white" /></a>
<a href="https://github.com/EMoon-03?tab=repositories"><img src="https://img.shields.io/badge/All_Repos-0F766E?style=flat-square&logo=github&logoColor=white" /></a>

</div>

---

## 👨‍💻 About Me

I'm a Rutgers Computer Science graduate, now an **MSCS student at Stevens Institute of Technology** focusing on **machine learning and AI**.

I like the part of ML that comes *after* the notebook: wrapping models in **APIs, CLIs, and full-stack apps** that people can actually run. Most of what I build is Python, with React and TypeScript when it needs a face.

I've also spent a lot of time teaching code, as a tutor at Rutgers' CS help center and as a Python instructor. That's made me much better at explaining, and documenting, what I build.

> 🎯 **Looking for:** internships and roles in **AI/ML engineering, data engineering, and software engineering**.

---

## 🧠 Model Card

<sub>Every good model ships with a model card. So does this one.</sub>

```yaml
model:        eddie-moon
version:      v2026.10-beta          # stable release expected Dec 2027 (MSCS)
architecture: Python-first, full-stack capable

training_data:
  - B.A. Computer Science · Rutgers University (2021–2025) · Dean's List ×4
  - M.S. Computer Science · Stevens Institute of Technology · ML & AI · GPA 3.83
  - 6 months of live-debugging other people's code at the Rutgers CS help center

fine_tuned_on: [FastAPI, React, TypeScript, scikit-learn, PyTorch, LLM APIs]

intended_use:
  - Turning ML ideas into shippable services and tools
  - Backend APIs, data pipelines, developer CLIs

out_of_scope:
  - Leaving a model in a Jupyter notebook forever

known_limitations:
  - Will refactor your CLI into a plugin system
  - Caffeine-dependent (prior production deployment as a barista, 2025–2026)

current_epoch: Iterating on SpectrumSense v2 and One Trip
next_epoch:    GovSpend AI · ML + RAG over government spending data
```

---

## ⚡ Featured Engineering

### 📡 SpectrumSense
**Signal Classifier That Knows When to Say "Uncertain"** &nbsp;
![Status](https://img.shields.io/badge/status-v2-14B8A6?style=flat-square)
![Tests](https://img.shields.io/badge/tests-376-14B8A6?style=flat-square)

*Simulates radio I/Q samples, classifies them as noise, BPSK, or QPSK, and refuses to guess on signals it was never trained on.*

**Highlights**

- 🎯 **Abstains instead of guessing:** a plain classifier confidently labels unseen signals (8PSK, 16-QAM, a pure tone) as QPSK or BPSK, so the model returns **"uncertain"** when an input falls outside what it learned
- 🧮 **Explainable features + logistic-regression baseline** in a scikit-learn pipeline, evaluated on **1,024-sample windows**
- 📻 Analyze your **own SDR recordings**, validated against one **real satellite QPSK recording** (SigMF, CC BY 4.0)
- 🔗 **Typed API contract:** frontend types generated from FastAPI's OpenAPI schema
- ✅ **376 tests** plus **GitHub Actions CI** (Python 3.10 & 3.12, lint + type-checked Next.js build); Render deploy config
- 🏗️ Grew from a Streamlit prototype into a **FastAPI + Next.js** app

<details>
<summary><b>🔍 View pipeline</b></summary>
<br>

```mermaid
flowchart LR
    A[Simulated or uploaded I/Q] --> B[Feature extraction]
    B --> C[Logistic regression]
    C --> D{Confident?}
    D -->|yes| E[Noise · BPSK · QPSK]
    D -->|no| F[Uncertain]
    E --> G[FastAPI]
    F --> G
    G --> H[Next.js dashboard]
```

</details>

**Stack**
- **ML & DSP:** `Python` `NumPy` `SciPy` `scikit-learn` `Matplotlib` `Plotly`
- **Backend:** `FastAPI` `Uvicorn` `Pydantic` `Streamlit` (original lab)
- **Frontend:** `TypeScript` `Next.js 16` `React 19` `Tailwind CSS 4` `Recharts` `openapi-typescript`
- **Testing & Ops:** `unittest` `httpx` `ESLint` `GitHub Actions` `Render`

<a href="https://github.com/EMoon-03/spectrum_sense"><img src="https://img.shields.io/badge/View_Repo-1F2937?style=for-the-badge&logo=github&logoColor=white" /></a>

<br>

### ✈️ One Trip
**Travel Itinerary, Budget & Reminders App** &nbsp;
![Status](https://img.shields.io/badge/status-active-14B8A6?style=flat-square)
![Tests](https://img.shields.io/badge/tests-21-14B8A6?style=flat-square)

*Plan the days, track the budget, never miss a departure. One trip is the hub for its stops, expenses, and reminders.*

**Highlights**

- 🧭 **Linked data model:** an expense can belong to a specific stop (the $52 dinner), and a reminder can be pinned to one ("leave 2h before the flight")
- 🔐 **Multi-user JWT auth** with bcrypt-hashed passwords; every trip is scoped to its owner
- 🗺️ **Swappable geocoding:** Google Places or free OpenStreetMap/Nominatim behind one interface, with the API key kept server-side
- 📊 **Budget charts** with Recharts, and maps with Leaflet or Google Maps
- ⚡ Axios interceptors (auth headers, 401 handling) + **TanStack Query** caching
- 🕒 Next up: a scheduled **background worker** for reminders with correct time zones

**Stack**
- **Backend:** `Python` `FastAPI` `SQLModel` `Pydantic` `Uvicorn` `MySQL 8` `SQLite` `PyJWT` `bcrypt` `httpx`
- **Frontend:** `TypeScript` `React 19` `Vite` `React Router` `Axios` `TanStack Query` `Recharts`
- **Maps:** `Google Maps / Places API` `Leaflet` `OpenStreetMap` `Nominatim`
- **Testing & Ops:** `pytest` `Docker Compose`

<a href="https://github.com/EMoon-03/One-Trip"><img src="https://img.shields.io/badge/View_Repo-1F2937?style=for-the-badge&logo=github&logoColor=white" /></a>

---

## 🧩 More Engineering Work

<table>
<tr>
<td width="50%" valign="top">

### 🧞 DevGenie
**AI Developer Assistant for the Terminal**

One CLI over **Ollama (local), OpenAI, and Anthropic**, switchable with one setting. **8 commands:** commit messages, code review, changelogs, docstrings, shell commands, test generation, standups, and error triage.

- Provider plugin system + TOML config
- **29 tests**

`Python` `Click` `Requests` `TOML` `Git` `Ollama` `OpenAI API` `Anthropic API` `pytest`

<a href="https://github.com/EMoon-03/devgenie"><img src="https://img.shields.io/badge/View_Repo-1F2937?style=flat-square&logo=github&logoColor=white" /></a>

</td>
<td width="50%" valign="top">

### 🔢 Face & Digit Classification
**Classifiers From Scratch vs. a Framework**

Compared a **perceptron** and a **three-layer neural network built from scratch** against a **PyTorch** network, on handwritten digits (0–9) and face / not-face images.

- Accuracy and training-time plots per model
- Saved models for a demo script

`Python` `NumPy` `PyTorch` `Matplotlib`

<a href="https://github.com/EMoon-03/Face-and-Digit-Classification"><img src="https://img.shields.io/badge/View_Repo-1F2937?style=flat-square&logo=github&logoColor=white" /></a>

</td>
</tr>
</table>

---

## 🏫 Experience

**🧑‍🏫 Student Tutor** · Rutgers University CS Help Center &nbsp; <sub>Sept 2024 – Feb 2025</sub>
- Helped students debug and understand assignments across introductory and core CS courses.
- Explained programming concepts one-on-one, adapting to each student's level.

**🐍 Python Instructor & ACSL Coach**
- Teach Python to students preparing for certification exams.
- Coach students for **ACSL** (American Computer Science League) competitions.

---

## 🛠️ Technical Toolkit

<div align="center">

| | |
|:--:|:--|
| **Languages** | <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" /> <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" /> <img src="https://img.shields.io/badge/SQL-336791?style=flat-square&logo=postgresql&logoColor=white" /> <img src="https://img.shields.io/badge/CSS-1572B6?style=flat-square&logo=css3&logoColor=white" /> |
| **Cloud** | <img src="https://img.shields.io/badge/Google_Cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=white" /> <img src="https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white" /> |
| **ML & Data** | <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white" /> <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" /> <img src="https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white" /> <img src="https://img.shields.io/badge/SciPy-8CAAE6?style=flat-square&logo=scipy&logoColor=white" /> <img src="https://img.shields.io/badge/Matplotlib-11557C?style=flat-square" /> <img src="https://img.shields.io/badge/Plotly-3F4F75?style=flat-square&logo=plotly&logoColor=white" /> <img src="https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white" /> |
| **Backend** | <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white" /> <img src="https://img.shields.io/badge/SQLModel-7E56C2?style=flat-square" /> <img src="https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white" /> <img src="https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white" /> <img src="https://img.shields.io/badge/JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white" /> <img src="https://img.shields.io/badge/Click_CLI-1F2937?style=flat-square" /> |
| **Frontend** | <img src="https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB" /> <img src="https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white" /> <img src="https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white" /> <img src="https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white" /> <img src="https://img.shields.io/badge/TanStack_Query-FF4154?style=flat-square&logo=reactquery&logoColor=white" /> <img src="https://img.shields.io/badge/Axios-5A29E4?style=flat-square&logo=axios&logoColor=white" /> <img src="https://img.shields.io/badge/Recharts-22B5BF?style=flat-square" /> <img src="https://img.shields.io/badge/Leaflet-199900?style=flat-square&logo=leaflet&logoColor=white" /> |
| **AI & APIs** | <img src="https://img.shields.io/badge/Ollama-000000?style=flat-square&logo=ollama&logoColor=white" /> <img src="https://img.shields.io/badge/OpenAI_API-412991?style=flat-square&logo=openai&logoColor=white" /> <img src="https://img.shields.io/badge/Anthropic_API-191919?style=flat-square&logo=anthropic&logoColor=white" /> <img src="https://img.shields.io/badge/Google_Maps_API-4285F4?style=flat-square&logo=googlemaps&logoColor=white" /> |
| **Testing & Ops** | <img src="https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white" /> <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" /> <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" /> <img src="https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white" /> <img src="https://img.shields.io/badge/ESLint-4B32C3?style=flat-square&logo=eslint&logoColor=white" /> <img src="https://img.shields.io/badge/Render-46E3B7?style=flat-square&logo=render&logoColor=black" /> |

</div>

---

## 📋 Background

| | |
|:--:|:--|
| 🎓 | **M.S. Computer Science** (ML & AI) · Stevens Institute of Technology · Expected Dec 2027 |
| 🎓 | **B.A. Computer Science** · Rutgers University · 2025 |
| 🧑‍🏫 | **Student Tutor** · Rutgers CS Help Center |
| 🎯 | AI/ML · Data Engineering · Software Engineering |
| 🔨 | Iterating on SpectrumSense v2 & One Trip · next up: GovSpend AI |

---

<div align="center">

### 🤝 Let's Connect

I'm always up for talking about ML in production, Python tooling, LLM apps, or whatever bug you're stuck on.

<a href="https://www.linkedin.com/in/edward-moon-972007237"><img src="https://img.shields.io/badge/LinkedIn-Connect-0F766E?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
<a href="mailto:sungjune.moon@gmail.com"><img src="https://img.shields.io/badge/Email-Reach_Out-0F766E?style=for-the-badge&logo=gmail&logoColor=white" /></a>

</div>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:14B8A6,100:0F766E&height=110&section=footer" width="100%" />
