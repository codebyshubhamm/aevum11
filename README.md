# THERMOS — Thermal Event Recognition and Monitoring Operational System

[![SIH 2026](https://img.shields.io/badge/SIH-2026-orange.svg?style=flat-square)](https://www.sih.gov.in/)
[![Problem Statement](https://img.shields.io/badge/PS_ID-SIH26162-blue.svg?style=flat-square)](https://www.sih.gov.in/)
[![Category](https://img.shields.io/badge/Category-Software-green.svg?style=flat-square)](https://www.sih.gov.in/)
[![Theme](https://img.shields.io/badge/Theme-Disaster_Management-red.svg?style=flat-square)](https://www.sih.gov.in/)
[![Live App](https://img.shields.io/badge/Demo-Live_on_Vercel-success.svg?style=flat-square&logo=vercel)](https://sih-2026-nu-ten.vercel.app/)
[![React](https://img.shields.io/badge/Frontend-React_19_+_Vite-61dafb.svg?style=flat-square&logo=react)](https://react.dev/)
[![TailwindCSS v4](https://img.shields.io/badge/Styling-TailwindCSS_v4-38bdf8.svg?style=flat-square&logo=tailwindcss)](https://tailwindcss.com/)
[![MapLibre GL](https://img.shields.io/badge/Maps-MapLibre_GL-3274a3.svg?style=flat-square)](https://maplibre.org/)
[![Three.js](https://img.shields.io/badge/3D-Three.js_WebGL-black.svg?style=flat-square&logo=threedotjs)](https://threejs.org/)
[![XGBoost](https://img.shields.io/badge/ML-XGBoost_99.4%25_Acc-eb5424.svg?style=flat-square)](https://xgboost.readthedocs.io/)
[![FastAPI](https://img.shields.io/badge/Backend-FastAPI-009688.svg?style=flat-square&logo=fastapi)](https://fastapi.tiangolo.com/)
[![AI Copilot](https://img.shields.io/badge/RAG_AI-Gemini_Disaster_Copilot-8E75B2.svg?style=flat-square)](https://deepmind.google/technologies/gemini/)

> **Smart India Hackathon (SIH 2026) Project Repository**  
> **AI-Powered Earth Observation, Geospatial ML & Tactical Intelligence Platform for Real-Time Satellite Thermal Anomaly Classification, Risk Prioritization, and Emergency Dispatch.**

---

## 1. Project Information

- **Project Title:** THERMOS (Thermal Event Recognition and Monitoring Operational System)
- **Problem Statement ID:** SIH26162
- **PS Title:** AI-Based Detection and Classification of Industrial Fires and Persistent Thermal Sources Using NASA FIRMS, OSM & Satellite Data
- **Category:** Software
- **Theme:** Disaster Management
- **Institution:** Netaji Subhas University of Technology (NSUT), New Delhi
- **Team:** Team THERMOS
- **Live Web Application:** [https://sih-2026-nu-ten.vercel.app/](https://sih-2026-nu-ten.vercel.app/)
- **Presentation Deck:** [Google Slides Presentation](https://docs.google.com/presentation/d/1ORwPvLgP6Ni3FeG5BahZI_S0C2mZuAu9/edit?slide=id.p1#slide=id.p1)
- **Demo Video Walkthrough:** [Google Drive Video Demo](https://drive.google.com/drive/folders/16Wlb9OPWw7XWWOp1OCEa2qXNFlJxGEv3)
- **Repository URL:** [https://github.com/codebyshubhamm/THERMOS-LIVE2](https://github.com/codebyshubhamm/THERMOS-LIVE2)
- **Team Composition (6 Members):**
  - **Frontend Engineering & Spatial GIS:** MapLibre GL 2D/3D layers, Spatial clustering, WebGL Canvas architecture, responsive layout engineering.
  - **Tactical UI & Real-Time Visualization:** Incident triage queues, dynamic forensic drawers, Recharts analytics, telemetry streams.
  - **UI/UX Design & Human-in-the-Loop:** Ergonomic tactical dark palette, high-contrast hazard indicators, operator review workflows.
  - **AI/ML Pipeline & Geospatial Engineering:** 14-feature KD-Tree spatial feature extractor, 6-class XGBoost classifier (99.4% accuracy), SHAP explainability.
  - **RAG Disaster Intelligence & Backend:** FastAPI REST architecture, RAG Hazmat Copilot (Google Gemini + NDMA SOPs/MSDS), MongoDB `2dsphere` / PostGIS geospatial storage.
  - **Systems Integration & Reliability:** NASA FIRMS automated stream ingestion, dual-mode live/offline resilience, end-to-end integration testing.

---

## 2. Problem Statement & Motivation

Every 10 to 20 minutes, Earth-observing satellites—including **NASA VIIRS (Suomi NPP & NOAA-20 / NOAA-21)** and **MODIS (Aqua & Terra)**—detect thousands of active thermal anomalies across the globe. However, disaster management authorities, civil defence control rooms, and industrial safety regulators face three critical operational bottlenecks:

1. **Context Blindness & Identity Ambiguity:**
   Raw FIRMS telemetry delivers only geographic coordinates (`latitude`, `longitude`), Brightness Temperature ($K$), and Fire Radiative Power (MW). It **cannot distinguish between benign routine industrial heat and catastrophic emergencies**. A permitted petrochemical flare stack or steel foundry furnace emits thermal signatures nearly identical to a sudden refinery explosion, chemical tank farm blaze, or spreading wildfire.
2. **Severe Alert Fatigue & False Alarms:**
   Industrial corridors and agricultural belts generate tens of thousands of unclassified hotspots daily. Operators are inundated with alerts, leading to delayed responses to genuine industrial disasters.
3. **Lack of Actionable Context & Escalation Speed:**
   Without automated fusion of satellite telemetry with industrial facility perimeters, chemical inventories (MSDS), land cover, and population density, responders cannot triage incidents or dispatch resources with necessary speed.

---

## 3. Proposed Solution

**THERMOS** transforms raw satellite heat spots into **actionable tactical intelligence** through an automated, end-to-end multi-modal pipeline:

```text
┌────────────────────────┐      ┌────────────────────────┐      ┌────────────────────────┐
│    NASA FIRMS API      │ ───► │  14-Feature KD-Tree    │ ───► │ 6-Class XGBoost Model  │
│ (VIIRS 375m, MODIS 1km)│      │  Spatial Engine        │      │   (99.40% Accuracy)    │
└────────────────────────┘      └────────────────────────┘      └───────────┬────────────┘
                                                                            │
┌────────────────────────┐      ┌────────────────────────┐                  ▼
│ Tactical GIS Dashboard │ ◄─── │ RAG Hazmat AI Copilot  │ ◄─── ┌────────────────────────┐
│ (MapLibre + 3D Globe)  │      │ (NDMA SOPs + MSDS KB)  │      │ Operational Risk Engine│
└────────────────────────┘      └────────────────────────┘      │   (Score: 0 - 100)     │
                                                                └────────────────────────┘
```

1. **Automated Satellite Stream Ingestion:** Continuously pulls active thermal anomaly detections from NASA FIRMS with spatial clustering (DBSCAN) to deduplicate multi-pass observations within a 750m radius.
2. **14-Feature Geospatial & Temporal Enrichment:**
   - **Scipy Spatial KD-Tree & Geodesics:** Fast microsecond spatial proximity calculation to 50+ Indian Major Accident Hazard (MAH) complexes, refineries, chemical hubs, coal mines, forests, and agricultural lands.
   - **OpenStreetMap (OSM Overpass API):** Cross-references coordinates against industrial park boundaries, storage tanks, and substations.
   - **ESA WorldCover & WorldPop:** Derives high-resolution land-cover classification and demographic population impact ($1\text{ km}$ and $5\text{ km}$ buffers).
   - **Temporal History Engine:** Computes thermal persistence across 24h, 7d, and 30d time horizons, tracking Fire Radiative Power escalation rates ($\Delta\text{FRP}$).
3. **High-Accuracy ML Classification:** An optimized **XGBoost Classifier (99.40% accuracy)** categorizes anomalies into **6 operational classes**:
   - `Industrial Fire` *(Emergency accidental blaze requiring urgent tactical dispatch)*
   - `Industrial Thermal Source` *(Permitted operational blast furnace, cement kiln, or foundry)*
   - `Gas Flare` *(Permitted petrochemical flare stack venting)*
   - `Wildfire` *(Forest, brush, and wildland fire spread)*
   - `Agricultural Burning` *(Seasonal crop residue and stubble burning)*
   - `Mining Activity` *(Open-cast and coal mining extraction heat signatures)*
4. **Operational Risk Engine:** Computes an actionable **Risk Score (0–100)** ranking incidents into `Critical` ($\ge 80$), `High` ($60–79$), `Moderate` ($35–59$), and `Low` ($< 35$) priority tiers based on hazard classification, infrastructure proximity, population density, and thermal spike rates.
5. **RAG Disaster Intelligence & Hazmat Copilot:** Integrates Google Gemini with a curated knowledge base of 50+ Indian MAH industrial facilities, chemical Material Safety Data Sheets (MSDS), and NDMA Standard Operating Procedures (SOPs) to produce instant Tactical Incident Action Plans (IAPs).
6. **Tactical GIS Command Centre:** A responsive web application featuring interactive MapLibre GL mapping, 3D WebGL thermal Earth globe, dynamic forensic drawers, SHAP explainability cards, and operational analytics.

---

## 4. Key Features

- 🌐 **Interactive 3D Thermal Globe:** High-performance WebGL digital Earth built with Three.js rendering active global satellite hotspots, thermal intensity gradients, and spatial density.
- 🗺️ **Tactical GIS Command Centre:** MapLibre GL map featuring thermal density heatmaps, individual hotspot markers with live popups, industrial perimeter polygons, and dynamic buffer circles.
- 🎯 **99.4% Accurate 6-Class ML Classification:** Real-time multi-class XGBoost model with per-category confidence probabilities and SHAP feature importance breakdown.
- 🚨 **Automated Priority Queue & Triage:** Algorithmic ranking sorting anomalies into `Critical`, `High`, `Moderate`, and `Low` priority tiers with instant multi-criteria filtering.
- 🧠 **RAG Hazmat AI Copilot (`Ask THERMOS`):** Interactive conversational AI assistant answering tactical queries on chemical hazards, evacuation radii, and fire suppression protocols using NDMA SOPs and MSDS sheets.
- 🔍 **Deep-Dive Forensic Incident Investigator:** Tabbed diagnostic suite featuring multi-spectral anomaly dynamics, local weather matrices, decision tree audit trails, and exportable incident briefs.
- 📊 **Historical Analytics & Trend Intelligence:** Spatial and temporal heatmaps, classification distributions, risk charts, and historical FRP trendlines powered by Recharts.
- 🛰️ **Satellite Overpass Schedule & Threat Correlation:** Ingestion monitoring of SNPP VIIRS, NOAA-20, Aqua/Terra MODIS, and Sentinel-2 correlated with Indian industrial cluster risk indices.
- ⚡ **Resilient Dual-Mode Operation:** Instant automatic fallback to high-fidelity simulated telemetry when offline or rate-limited, guaranteeing 100% operator uptime.

---

## 5. Technology Stack

### Frontend Client (React 19 + Vite)
- **Framework & Routing:** React 19 (`react` 19.2.8, `react-dom` 19.2.8), React Router v7 (`react-router-dom` 7.18.3)
- **Build Tooling:** Vite 8.2.2 with `@vitejs/plugin-react`
- **Styling:** TailwindCSS v4 (`@tailwindcss/vite` 4.3.3, `tailwindcss` 4.3.3) with `@theme` design tokens
- **Geospatial 2D Map:** MapLibre GL (`maplibre-gl` 6.6.0)
- **3D WebGL Graphics:** Three.js (`three` 0.185.1), `@react-three/fiber` 9.7.0, `@react-three/drei` 10.7.8
- **State Management:** Zustand (`zustand` 5.0.15)
- **Data Charts:** Recharts (`recharts` 3.10.1)
- **Animations:** Framer Motion (`framer-motion` 13.1.1)
- **Code Linter:** Oxlint (`oxlint` 1.79.0)

### Backend & Artificial Intelligence Pipeline
- **API Framework:** Python 3.10+, FastAPI, Uvicorn, Pydantic v2
- **Machine Learning:** XGBoost (`xgboost` 3.4.1), Scikit-Learn, NumPy, Pandas, Joblib
- **Geospatial Math:** Scipy Spatial (`cKDTree`), Geodesic Haversine formulas, Shapely
- **Explainability:** SHAP (SHapley Additive exPlanations)
- **RAG & GenAI:** Google Gemini 1.5 Flash + Local Knowledge Base (50+ Indian MAH facilities, NDMA Fire SOPs, Chemical MSDS)
- **Storage & Spatial Indexing:** MongoDB with `2dsphere` Geospatial Indexing / PostgreSQL + PostGIS
- **Containerization & Deployment:** Docker, Docker Compose, Nginx, Vercel, Render

---

## 6. System Architecture

See [docs/architecture.md](docs/architecture.md) for the complete architectural specification.

```text
                               ┌────────────────────────┐
                               │    NASA FIRMS API      │
                               │ (VIIRS SNPP/NOAA, MODIS│
                               └───────────┬────────────┘
                                           │
                                           ▼
                               ┌────────────────────────┐
                               │   Ingestion Service    │
                               │ (DBSCAN Cluster/Dedupe)│
                               └───────────┬────────────┘
                                           │
                               ┌───────────┴────────────┐
                               ▼                        ▼
                    ┌─────────────────────┐  ┌─────────────────────┐
                    │   Temporal Engine   │  │   Geo-Enrichment    │
                    │ (Persistence, Delta │  │ (OSM, KD-Tree MAH,  │
                    │   FRP, Recurrence)  │  │  ESA, WorldPop 5km) │
                    └──────────┬──────────┘  └──────────┬──────────┘
                               └───────────┬────────────┘
                                           │
                                           ▼
                               ┌────────────────────────┐
                               │ 14-Feature Schema Vector│
                               │ (Tabular Transformation│
                               └───────────┬────────────┘
                                           │
                                           ▼
                               ┌────────────────────────┐
                               │  ML Classification     │
                               │(XGBoost 99.4% Accuracy)│
                               └───────────┬────────────┘
                                           │
                               ┌───────────┴────────────┐
                               ▼                        ▼
                    ┌─────────────────────┐  ┌─────────────────────┐
                    │ Explainable Factors │  │ Operational Risk    │
                    │  (SHAP & Evidence)  │  │ Engine (0-100 Score)│
                    └──────────┬──────────┘  └──────────┬──────────┘
                               └───────────┬────────────┘
                                           │
                                           ▼
                               ┌────────────────────────┐
                               │ Database Storage Layer │
                               │ (MongoDB 2dsphere /    │
                               │  PostgreSQL + PostGIS) │
                               └───────────┬────────────┘
                                           │
                               ┌───────────┴────────────┐
                               ▼                        ▼
                    ┌─────────────────────┐  ┌─────────────────────┐
                    │     FastAPI REST    │  │ RAG Hazmat Copilot  │
                    │  Endpoints & Feeds  │  │(Gemini + NDMA/MSDS) │
                    └──────────┬──────────┘  └──────────┬──────────┘
                               └───────────┬────────────┘
                                           │
                                           ▼
                               ┌────────────────────────┐
                               │ THERMOS GIS Dashboard  │
                               │ (React 19 + MapLibre GL│
                               │  + 3D Globe + Triage)  │
                               └────────────────────────┘
```

---

## 7. Repository Structure

```text
THERMOS-LIVE2/
├── README.md                          # Primary project documentation
├── SUBMISSION_GUIDE.md                # SIH 2026 repository submission checklist
├── package.json                       # NPM dependencies and project scripts
├── vite.config.js                     # Vite bundler configuration
├── .oxlintrc.json                     # Oxlint code inspection configuration
├── .gitignore                         # Git exclusion rules
├── index.html                         # HTML5 entrypoint with typography fonts
├── vercel.json                        # Vercel deployment configuration
├── render.yaml                        # Render cloud deployment blueprint
├── docs/
│   └── architecture.md                # In-depth architectural & data-flow specification
├── submission/
│   ├── DEMO.md                        # Video demonstration outline & links
│   └── PRESENTATION.md                # Pitch presentation deck & slide notes
├── ai/                                # Standalone Unified AI & RAG Copilot Module
│   ├── __init__.py                    # Unified package exports
│   ├── api_router.py                  # FastAPI Router for /api/ai/*
│   ├── classifier.py                  # 99.4% Accurate XGBoost Multi-Class Classifier
│   ├── copilot.py                     # RAG Disaster Intelligence & Hazmat Copilot
│   ├── spatial_engine.py              # 14-Feature Scipy KD-Tree Geospatial Engine
│   ├── knowledge/
│   │   ├── hazmat_sop_kb.json         # Chemical MSDS Profiles & NDMA Fire SOPs
│   │   └── industrial_facilities.json # 50+ Indian Major Accident Hazard (MAH) Complexes
│   └── models/
│       ├── label_encoders.pkl         # Categorical & class encoders
│       ├── model_metadata.json        # Feature importance & evaluation metrics
│       └── xgboost_classifier.pkl     # Trained XGBoost model weights
├── backend-ml/                        # Complete Backend, Database & ML Pipeline
│   ├── Dockerfile                     # Docker container build definition
│   ├── docker-compose.yml             # Multi-container orchestration (FastAPI + MongoDB + Nginx)
│   ├── nginx.conf                     # Reverse proxy configuration
│   ├── DEPLOY.md                      # Backend deployment & environment guide
│   ├── API.md                         # Detailed API reference documentation
│   ├── Backend/                       # FastAPI application core & Alembic migrations
│   └── ml/                            # Model training, evaluation & feature pipelines
│       ├── train.py                   # XGBoost model training script
│       ├── evaluate.py                # Model evaluation and confusion matrix generator
│       ├── predict.py                 # Standalone prediction pipeline
│       ├── seed.py                    # Database seeder for Indian industrial facilities
│       └── requirements.txt           # Python backend dependencies
├── public/
│   └── vite.svg                       # Static vector assets
└── src/
    ├── components/
    │   ├── landing/
    │   │   └── GlobeCanvas.jsx        # Three.js 3D interactive satellite thermal globe
    │   ├── layout/
    │   │   ├── AppLayout.jsx          # Shell layout with navigation wrapper & drawer
    │   │   ├── Sidebar.jsx            # Tactical sidebar navigation & active route links
    │   │   └── TopBar.jsx             # Header with search, sensor count, and live feed badge
    │   ├── map/
    │   │   ├── HeatmapLayer.jsx       # MapLibre GL thermal density heatmap layer
    │   │   ├── HotspotLayer.jsx       # Cluster & individual hotspot markers with popups
    │   │   ├── IndustrialBoundaryLayer.jsx # OSM industrial perimeter polygons & buffers
    │   │   ├── MapControls.jsx        # Layer toggles, zoom, and spatial style switchers
    │   │   ├── MapCore.jsx            # Core MapLibre GL map instance initialization
    │   │   ├── MapView.jsx            # Composite map container with active store sync
    │   │   ├── PredictionPanel.jsx    # Real-time ML prediction summary panel
    │   │   └── TimeSlider.jsx         # Interactive temporal timeline scrubber (24H/7D/30D)
    │   └── shared/
    │       ├── AskThermos.jsx         # RAG AI conversational query assistant for event diagnostics
    │       ├── ChartCard.jsx          # Card wrapper for analytics charts
    │       ├── EventHistoryChart.jsx  # Recharts FRP historical trend visualization
    │       ├── EvidenceCard.jsx       # Explainable ML decision factors with percentage weights
    │       ├── IncidentDetailDrawer.jsx # Slide-out forensic inspection drawer
    │       ├── RiskFactorBreakdown.jsx# Detailed risk weight distribution component
    │       └── SkeletonLoader.jsx     # Sleek skeleton loading placeholders
    ├── data/
    │   └── mockData.js                # High-fidelity realistic telemetry across Indian industrial hubs
    ├── pages/
    │   ├── Analytics.jsx              # Temporal timelines, category pie charts, risk bar charts
    │   ├── CommandCentre.jsx          # Main GIS tactical map + live priority sidebar
    │   ├── Intelligence.jsx           # Sensor pass schedule, industrial cluster risk ranking
    │   ├── Investigator.jsx           # Tabbed forensic analysis (Spectral, Weather, Decision Tree)
    │   ├── Landing.jsx                # SIH presentation landing page with 3D globe & workflow
    │   ├── PriorityQueue.jsx          # Multi-filter operational triage list sorted by risk
    │   └── SystemHealth.jsx           # Pipeline telemetry, API latency, and sensor uptime
    ├── services/
    │   └── api.js                     # REST service client connecting to backend API
    ├── store/
    │   └── useStore.js                # Central Zustand store (filters, selection, live data)
    ├── utils/
    │   └── formatters.js              # Risk color coding, duration, coordinate, and label formatters
    ├── App.jsx                        # Client router configuration with React Router v7
    ├── index.css                      # Global styles, font imports, TailwindCSS v4 @theme tokens
    └── main.jsx                       # Application root bootstrap
```

---

## 8. Machine Learning & Operational Risk Details

### 8.1 6-Class ML Model
The classifier is an **XGBoost Classifier** (`n_estimators: 200`, `max_depth: 6`, `learning_rate: 0.1`) achieving **99.40% test accuracy**:
1. **Industrial Fire:** Accidental industrial escalation requiring emergency fire service dispatch.
2. **Industrial Thermal Source:** Continuous operational signature (blast furnace, cement kiln, foundry).
3. **Gas Flare:** Routine petrochemical flare stack flaring.
4. **Wildfire:** Vegetation, grassland, and forest wildfire spread.
5. **Agricultural Burning:** Seasonal crop residue and stubble burning.
6. **Mining Activity:** Active open-cast and coal mining extraction heat signatures.

### 8.2 14-Feature Input Vector & Importance Weights
| # | Feature Name | Description | Feature Importance Weight |
|---|:---|:---|:---:|
| 1 | `cropland_proximity_km` | Geodesic distance to nearest agricultural land | **0.170** |
| 2 | `mine_proximity_km` | Geodesic distance to nearest mining site | **0.156** |
| 3 | `forest_proximity_km` | Geodesic distance to nearest forest boundary | **0.144** |
| 4 | `observation_count_7d` | Frequency of thermal detections at coordinate over 7 days | **0.124** |
| 5 | `industrial_proximity_km` | Distance to nearest industrial complex / MAH facility | **0.106** |
| 6 | `population_5km` | Demographic population density within 5 km impact zone | **0.095** |
| 7 | `refinery_proximity_km` | Distance to nearest petrochemical refinery / storage tank | **0.079** |
| 8 | `land_cover` | Categorical ESA WorldCover classification | **0.052** |
| 9 | `persistence_hours_7d` | Cumulative thermal activity duration over past 7 days | **0.039** |
| 10 | `frp_trend_pct` | Percentage change in Fire Radiative Power ($\Delta\text{FRP}$) | **0.027** |
| 11 | `brightness_k` | Satellite sensor Brightness Temperature (Kelvin) | **0.003** |
| 12 | `frp_mw` | Fire Radiative Power (Megawatts) | **0.002** |
| 13 | `daynight` | Day / Night satellite pass flag | **0.002** |
| 14 | `firms_confidence_pct`| Raw NASA FIRMS detection confidence metric | **0.001** |

### 8.3 Operational Risk Score Formulation
$$\text{Risk Score} = \min\left(100, \;\; w_1 \cdot C_{\text{risk}} + w_2 \cdot P_{\text{prox}} + w_3 \cdot E_{\text{pop}} + w_4 \cdot \Delta_{\text{FRP}}\right)$$

- 🔴 **Critical ($\ge 80$):** Immediate emergency alert dispatched to responder queue. Automatic tactical action plan generated.
- 🟠 **High ($60–79$):** Active monitoring with priority responder verification.
- 🟡 **Moderate ($35–59$):** Scheduled operational review; typical for permitted continuous industrial sources.
- 🟢 **Low ($< 35$):** Benign low-impact thermal anomaly.

---

## 9. RAG Hazmat Copilot & Knowledge Base

THERMOS integrates a specialized Retrieval-Augmented Generation (RAG) disaster assistant powered by **Google Gemini** and a curated local intelligence database:
- **50+ Monitored Major Accident Hazard (MAH) Facilities:** Includes Jamnagar Refinery, Hazira LNG, Panipat Petrochemicals, Visakhapatnam Steel Plant, Singrauli Coal Belt, and Manali Chemical Corridor.
- **Chemical Hazard Profiles (MSDS):** Instant lookups for Ethylene, Benzene, Liquefied Natural Gas, LPG, Chlorine, Ammonia, etc., with NFPA 704 ratings, primary fire hazards, and health hazards.
- **NDMA Standard Operating Procedures:** Automated isolation distances, tactical water fog vs. dry chemical suppression recommendations, foam fire-fighting specifications, and multi-tier evacuation radii ($500\text{ m}$ to $5\text{ km}$).

---

## 10. API Endpoints Overview

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/health` | System health check (Model status, DB connectivity, Indexed facilities) |
| `GET` | `/api/anomalies` | **GeoJSON FeatureCollection** of classified anomalies (supports `min_frp`, `classification`, `risk_level`) |
| `GET` | `/api/anomalies/{id}` | Detailed telemetry, spatial features, and facility association for a specific event |
| `POST` | `/api/anomalies/ingest` | Ingests raw NASA FIRMS points, extracts 14 features, classifies, and saves to database |
| `GET` | `/api/facilities` | List of 50+ monitored Indian industrial facilities with hazardous materials |
| `GET` | `/api/facilities/nearby` | Geospatial proximity search finding facilities within `max_distance_km` radius |
| `GET` | `/api/stats` | Aggregated dashboard metrics (% Industrial vs Wildfire vs Agri, Total FRP, Active Count) |
| `POST` | `/api/ai/analyze` | Single-call end-to-end pipeline: raw coordinates $\to$ 14 features $\to$ XGBoost $\to$ IAP Action Plan |
| `POST` | `/api/ai/chat` | RAG Copilot: Conversational hazard analysis, evacuation radii, and fire SOP recommendations |
| `POST` | `/api/predict` | Core 14-feature XGBoost ML inference endpoint |
| `POST` | `/api/predict_batch` | Batch 14-feature XGBoost inference endpoint |

---

## 11. Setup & Run Instructions

### Prerequisites
- **Node.js**: `v18.0.0` or higher
- **Python**: `3.10` or higher
- **npm** (included with Node.js)
- **Modern Web Browser**: Chrome, Firefox, Safari, or Edge with WebGL enabled

### 1. Frontend Setup & Execution
```bash
# Clone the repository
git clone https://github.com/codebyshubhamm/THERMOS-LIVE2.git
cd THERMOS-LIVE2

# Install dependencies
npm install

# Start the Vite development server
npm run dev

# Code quality inspection
npm run lint

# Build for production
npm run build
npm run preview
```

### 2. Backend & ML Setup (FastAPI)
```bash
# Navigate to backend/ml directory
cd backend-ml/ml

# Create and activate virtual environment
python -m venv venv
# On Windows:
venv\Scripts\activate
# On Linux/macOS:
source venv/bin/activate

# Install Python requirements
pip install -r requirements.txt

# Seed the database with 50+ Indian industrial facilities & hotspots
python seed.py

# Start FastAPI server with live reloading
uvicorn api.main:app --host 0.0.0.0 --port 8000 --reload
```
* Interactive API Documentation (Swagger UI): `http://localhost:8000/docs`
* API Health Check: `http://localhost:8000/api/health`

### 3. Docker Compose Execution (Optional Full Stack)
```bash
# Start FastAPI, MongoDB, and Nginx in containerized environment
docker-compose up --build -d

# Seed the containerized database
docker exec -it thermos-api python seed.py
```

---

## 12. Future Scope & Roadmap

1. **Industrial IoT & Fence-Line Sensor Integration:** Real-time ground sensor ingestion (perimeter optical IR flame detectors, gas sensors, and VOC monitors) via MQTT / WebSockets.
2. **Autonomous Drone (UAV) Dispatch Triggers:** Automated waypoint mission generation for automated drone docking stations (e.g., DJI Dock / PX4) for instant aerial thermal reconnaissance.
3. **High-Resolution Optical Satellite Corroboration:** Automated tasking with Sentinel-2 ($10\text{ m}$) and PlanetScope ($3\text{ m}$) optical bands using Vision Transformers (ViT) for smoke plume validation.
4. **National Disaster Framework & CAP Integration:** Direct webhook integration with the Common Alerting Protocol (CAP) for instant NDRF, SDMA, and District Emergency Operation Centre (DEOC) broadcasts.
5. **Atmospheric Chemical Plume Dispersion Modeling:** Real-time Gaussian plume dispersion modeling coupled with IMD / ECMWF wind vectors to project toxic smoke and chemical hazard zones.

---

## 13. Live Demo & Submission Links

- **Live Web Application:** [https://sih-2026-nu-ten.vercel.app/](https://sih-2026-nu-ten.vercel.app/)
- **Presentation Deck:** [Google Slides Presentation](https://docs.google.com/presentation/d/1ORwPvLgP6Ni3FeG5BahZI_S0C2mZuAu9/edit?slide=id.p1#slide=id.p1)
- **Demo Video Walkthrough:** [Google Drive Video Demo](https://drive.google.com/drive/folders/16Wlb9OPWw7XWWOp1OCEa2qXNFlJxGEv3)
- **GitHub Repository:** [https://github.com/codebyshubhamm/THERMOS-LIVE2](https://github.com/codebyshubhamm/THERMOS-LIVE2)

---

## 14. Acknowledgements & Data Sources

- **NASA FIRMS (Fire Information for Resource Management System):** Real-time thermal anomaly data from VIIRS (SNPP & NOAA-20) and MODIS (Aqua & Terra) instruments.
- **OpenStreetMap & Overpass API:** Global open crowd-sourced spatial infrastructure and industrial boundary polygons.
- **ESA WorldCover:** 10m global land cover classification data derived from Sentinel-1 and Sentinel-2.
- **WorldPop:** High-resolution spatial demographic and population distribution estimates.
- **National Disaster Management Authority (NDMA):** Standard Operating Procedures for Industrial Hazard & Fire Management.
- **Smart India Hackathon (SIH 2026):** Ministry of Education’s Innovation Cell & AICTE.
