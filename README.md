⭐ RecruitIQ — Intelligent HR Analytics & Interview Evaluation Platform

RecruitIQ is an end-to-end Human Resource Intelligence system built to modernize how companies evaluate talent, predict workforce risks, and make data-driven hiring decisions.
Designed for HR teams, interview panels, and decision-makers, RecruitIQ blends interactive dashboards, candidate scoring, session-based interview tracking, data visualization, and predictive analytics into a single unified platform.

Traditional hiring and HR analytics rely on manual spreadsheets, inconsistent scoring methods, and static dashboards. RecruitIQ eliminates these limitations by providing a fully dynamic, real-time, and scalable solution built on top of:

Streamlit UI layer for fast, interactive dashboards

Python-based analytics engine for scoring, ranking, and data prep

Plotly, Seaborn & Matplotlib for rich visualizations

SQLite / DB layer for storing candidates, interview sessions, and historical results

ML-ready pipelines for attrition prediction, workforce risk detection, and promotion insights

Whether you're evaluating candidates during interviews, tracking long-term employee performance, analyzing department-level workforce metrics, or predicting attrition trends — RecruitIQ provides everything you need in a clean, intuitive interface.







✨What makes RecruitIQ different?
🔍 1. Session-Based Interview Evaluation

Interviewers can create sessions dedicated to a hiring round and:

Add candidate profiles

Assign scores across several standardized metrics:
Communication, Technical Skills, Projects, Problem Solving, Culture Fit

Record interviewer notes

Store data automatically for analytics & comparison

📊 2. Advanced Candidate Ranking Engine

The platform includes a flexible and robust ranking system:

Rank candidates by any individual metric

Display a dynamic Top-N list

Provide a comparative multi-metric visualization

View normalized scores to maintain fairness

Ensure candidates are never deleted — filters only change the view, not the data

🎨 3. Visual Intelligence for Hiring Decisions

Visualizations for:

Single-parameter comparison (e.g., top communication scorers)

Multi-parameter grouped bar charts for comparative evaluation

Radar charts for skill distribution (optional)

Performance distributions and segment analysis

These visuals convert subjective impressions into objective insights.

🧠 4. Predictive Analytics for HR

Beyond recruitment, RecruitIQ supports analytics for:

Attrition risk prediction

Workforce stability & retention insights

Promotion readiness

Employee performance cluster analysis

Department-level workforce health overview

This extends the platform's value far beyond interviews into continuous HR intelligence.

💾 5. Lightweight Local Database

The entire platform works with:

SQLite for local persistence

Seamless connection with candidate save functions

Historical session integrity (no overwriting or forced deletions)

⚡ 6. Built for Scalability & Extensibility

RecruitIQ has a clean modular architecture:

Add new metrics? → Easy

Integrate machine learning? → Already prepped

Replace SQLite with MySQL/Postgres? → Replace 2 DB functions

Add authentication? → Sidebar login is modular

Deploy on Cloud / Docker? → Already prepared in structure

🛡 7. Simple UI with Powerful Controls

Unlike HRMS tools that overwhelm users with complexity, RecruitIQ focuses on clarity:

Clean forms

Card-based sections

Responsive layout

Easy navigation across modules

High readability for decision-makers






Tech stack

Python 3.10+

Streamlit

Pandas, NumPy

Plotly / Seaborn / Matplotlib (visuals)

SQLite (simple persistence)

Optional: scikit-learn (models)




RecruitIQ/
├─ src/
│  ├─ app.py                # main entry
│  ├─ tab_interview.py      # interview UI, ranking logic
│  ├─ data.py               # data loading & transforms
│  ├─ plots.py              # plotting helpers
│  └─ ...                   # other modules
├─ database/                # sqlite DB (not checked in)
├─ data/
├─ assets/
├─ requirements.txt
├─ README.md
└─ .gitignore



DATABASE SCHEMA
-- sessions table
CREATE TABLE sessions (
  id TEXT PRIMARY KEY,
  name TEXT NOT NULL,
  interviewer TEXT,
  date TEXT,
  notes TEXT
);

-- candidates table
CREATE TABLE candidates (
  id TEXT PRIMARY KEY,
  session_id TEXT REFERENCES sessions(id) ON DELETE CASCADE,
  name TEXT,
  email TEXT,
  phone TEXT,
  position TEXT,
  experience_years INTEGER,
  notes TEXT
);

-- scores table (one row per candidate per metric)
CREATE TABLE scores (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  candidate_id TEXT REFERENCES candidates(id) ON DELETE CASCADE,
  metric TEXT NOT NULL,
  value REAL NOT NULL
);

-- optional: saved computed ranking snapshot
CREATE TABLE rankings_snapshot (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  session_id TEXT,
  created_at TEXT,
  snapshot_json TEXT
);



ENVIRONMENT VARIABLES
# .env
DATABASE_URL=sqlite:///database/recruitiq.db
STREAMLIT_SERVER_PORT=8501
STREAMLIT_SERVER_HEADLESS=true
SECRET_KEY=your-random-secret
GITHUB_OAUTH_CLIENT_ID=
GITHUB_OAUTH_CLIENT_SECRET=
LOG_LEVEL=INFO













