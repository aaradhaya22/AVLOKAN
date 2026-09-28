# AVLOKAN

### Sovereign Earth-Observation Intelligence Platform

> **Search the Earth. Detect change. Verify evidence. Preserve provenance.**

AVLOKAN is an **on-premises satellite-imagery intelligence platform** built for semantic search, temporal change detection, false-alarm suppression, multi-sensor verification, and analyst-led investigation.

It transforms large Earth-observation archives into a searchable intelligence layer — helping analysts move from **“Where should I look?”** to **“What changed, and what evidence supports it?”**

**Smart India Hackathon 2026 · SIH26227 · Space Technology**
**Team Codenostic · Team ID 171288**

---

## Why AVLOKAN?

Satellite archives are growing rapidly, while manually inspecting every scene is slow and prone to false alarms.

AVLOKAN combines **AI retrieval, temporal analysis, optical + SAR evidence, and analyst review** into a single sovereign workflow.

```text
        SATELLITE ARCHIVE
               │
               ▼
        ┌───────────────┐
        │ Semantic      │
        │ Search        │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │ Change        │
        │ Detection     │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │ False-Alarm   │
        │ Suppression   │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │ Optical + SAR │
        │ Verification  │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │ Evidence-Backed│
        │ Verdict        │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │ Analyst Review│
        │ + Provenance  │
        └───────────────┘
```

---

# Core Capabilities

### 🔎 Semantic & Image Search

Search satellite archives using **natural language or imagery**.

Examples:

* `Newly constructed buildings`
* `Infrastructure development`
* `Cleared land near an existing facility`

Results can be refined using **similarity, geography, acquisition date, sensor, metadata, and spatial context**.

Powered by Earth-observation multimodal embeddings and FAISS.

---

### 🛰️ Multi-Temporal Change Detection

Compare observations from different points in time to identify localized changes.

```text
Before Image ──┐
               ├──► Alignment & Quality Check
After Image  ──┘
                        │
                        ▼
                 Candidate Detection
                        │
                        ▼
                  Pixel Verification
                        │
                        ▼
                   Change Map
```

AVLOKAN produces:

* Before / after imagery
* Change probability maps
* Change masks
* Candidate regions
* Spatial geometry
* Candidate-level evidence

---

### 🛡️ False-Alarm Suppression

Not every visual difference represents a real-world change.

AVLOKAN explicitly accounts for factors such as:

**Clouds · Haze · Shadows · Snow · SAR noise · Radiometric differences · Geometric misalignment · Insufficient usable imagery**

Quality control includes normalization, masking, co-registration, spatial alignment, and sensor-specific processing.

The goal is simple:

> **Reduce apparent changes before they become analyst alerts.**

---

### 📡 Multi-Sensor Verification

AVLOKAN does not rely on a single observation source.

It combines:

**Sentinel-2 Optical + Sentinel-1 SAR**

to provide complementary evidence.

```text
             Optical Evidence
                    │
                    ├──────┐
                    │      │
                    ▼      ▼
                 Evidence  Sensor
                  Fusion   Agreement
                    ▲
                    │
                    │
                SAR Evidence
```

This enables the system to distinguish between:

* Optical-supported change
* SAR-supported change
* Cross-sensor agreement
* Weak or conflicting evidence

---

# 🧠 Evidence-Backed Verdicts

This is the core idea behind **AVLOKAN**.

Instead of simply saying:

> **“Change detected.”**

AVLOKAN provides the analyst with the evidence behind the finding:

```text
CHANGE CANDIDATE
       │
       ├── Before / After imagery
       ├── Change probability
       ├── Spatial extent
       ├── Optical evidence
       ├── SAR evidence
       ├── Sensor agreement
       ├── Data quality
       └── Processing provenance
                │
                ▼
       Evidence-Backed Verdict
                │
                ▼
          Analyst Review
```

The **analyst remains in control** of the final decision.

---

# 🔭 Discovery & Similar-Site Analysis

A confirmed location can become a starting point for discovering similar locations across the archive.

```text
Confirmed Site
      ↓
Generate Embedding
      ↓
Search Archive
      ↓
Similarity Ranking
      ↓
Related Sites
```

This supports investigation beyond a single area of interest.

---

# 📋 Analyst-in-the-Loop

AVLOKAN is designed as an intelligence-support system, not a black-box decision maker.

Analysts can inspect:

* Before / after imagery
* Change visualization
* Location
* Acquisition dates
* Sensor information
* Evidence
* Candidate metrics
* Processing history
* Provenance

and **Confirm / Reject** individual findings.

---

# 🧾 Provenance & Auditability

Every analytical result can be traced back through its processing lineage.

AVLOKAN records information such as:

* Source observations
* Acquisition timestamps
* Sensor
* Input imagery
* CRS
* Model checkpoint
* Configuration
* Processing stages
* Thresholds
* Generated artifacts
* Analyst decisions

This makes findings **traceable, reproducible, and reviewable**.

---

# ⚡ Incremental Intelligence

New imagery does not require rebuilding the entire archive.

```text
New Scene
   ↓
Preprocess
   ↓
Tile
   ↓
Generate Embedding
   ↓
Append to Index
   ↓
Update Metadata
   ↓
Immediately Searchable
```

AVLOKAN uses an incremental vector-indexing architecture to support continuously growing archives.

---

# 🏗️ Architecture

```text
                 SATELLITE DATA
             S1 / S2 / Landsat / EO
                       │
                       ▼
              Acquisition & QC
                       │
             ┌─────────┴─────────┐
             ▼                   ▼
      Optical Pipeline       SAR Pipeline
             │                   │
             └─────────┬─────────┘
                       ▼
                Tiling & Metadata
                       │
                       ▼
               AI / Embeddings
             ┌─────────┼─────────┐
             ▼         ▼         ▼
        RemoteCLIP    BIT     HDBSCAN
             │         │         │
             └─────────┼─────────┘
                       ▼
                FAISS + Metadata
                       │
                       ▼
                  FastAPI API
                       │
                       ▼
               Analyst Workstation
```

---

# 🔐 Sovereign by Design

AVLOKAN is designed for **local, offline and controlled environments**.

```text
┌───────────────────────────────────────┐
│             AVLOKAN NODE              │
│                                       │
│  Satellite Data                       │
│       ↓                               │
│  AI / Processing                      │
│       ↓                               │
│  Vector Index + Metadata              │
│       ↓                               │
│  FastAPI                              │
│       ↓                               │
│  Analyst Workstation                  │
│                                       │
└───────────────────────────────────────┘
```

Imagery, queries, models, metadata, and analyst decisions can remain within the controlled environment.

---

# 🧰 Technology Stack

| Layer           | Technologies                                         |
| --------------- | ---------------------------------------------------- |
| **AI / Vision** | PyTorch, RemoteCLIP, GeoRSCLIP, BIT, HDBSCAN, OpenCV |
| **Geospatial**  | Rasterio, GDAL, ESA SNAP, GeoTIFF                    |
| **EO Data**     | Sentinel-1, Sentinel-2, Landsat, Bhuvan / ISRO       |
| **Retrieval**   | FAISS, vector embeddings                             |
| **Storage**     | PostgreSQL, PostGIS                                  |
| **Backend**     | Python, FastAPI, REST                                |
| **Frontend**    | JavaScript, MapLibre GL JS                           |
| **Deployment**  | Docker / Docker Compose                              |

---

# 🚀 Quick Start

### Demo

The local demo uses prepared data and does **not require a GPU or the complete imagery/model pipeline**.

```powershell
# Create environment
python -m venv .venv

# Activate
.\.venv\Scripts\Activate.ps1

# Install demo dependencies
pip install -r requirements-demo.txt
```

Start the backend:

```powershell
$env:AVLOKAN_DEMO_MODE = "true"
python -m uvicorn pipeline.api.app:app --host 127.0.0.1 --port 8000
```

Start the frontend in a second terminal:

```powershell
cd frontend
python -m http.server 5500
```

Open:

```text
http://127.0.0.1:5500
```

API documentation:

```text
http://127.0.0.1:8000/docs
```

> The complete imagery and model pipeline requires additional dependencies and model checkpoints.

---

# 📊 Evaluation

AVLOKAN supports evaluation across:

* Precision
* Recall
* F1
* IoU
* PR-AUC
* Retrieval latency
* Inference latency
* Indexing latency
* Processing time
* Storage footprint

Change-detection evaluation focuses on balancing **false alarms against missed changes**.

---

# 🎯 Use Cases

### Border & Infrastructure Monitoring

Detect construction, structural changes, cleared areas, roads, and other infrastructure changes.

### Disaster Response

Compare pre-event and post-event imagery to identify affected regions.

### Environmental Monitoring

Track changes in vegetation, water bodies, land cover, and surface disturbance.

### Intelligence Analysis

Prioritize relevant imagery and candidate changes so analysts can focus on **verification rather than exhaustive scanning**.

---

# 🧪 Research Foundation

AVLOKAN builds upon research and open technologies including:

* RemoteCLIP
* GeoRSCLIP
* Bitemporal Image Transformer (BIT)
* HDBSCAN
* FAISS
* PyTorch
* Rasterio
* GDAL
* ESA SNAP
* OpenCV
* MapLibre

Reference datasets include Sentinel-1, Sentinel-2, Landsat, OGCD, WHU-CD, and BIChange.

---

# 👥 Project

**AVLOKAN**
**Team:** Codenostic
**Smart India Hackathon:** 2026
**Problem Statement:** SIH26227
**Theme:** Space Technology
**Category:** Software
**Team ID:** 171288

---

## AVLOKAN

> **Search the Earth. Detect change. Verify evidence. Preserve provenance.**