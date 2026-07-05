# ICE Train Delay Prediction — ML Capstone

Predict ICE train delays using Deutsche Bahn operational data and Open-Meteo historical weather.

## Problem

- **Classification:** Will an ICE stop be delayed (≥ 6 minutes)?
- **Regression:** How many minutes late?

## Data sources

| Source | Link |
|--------|------|
| Deutsche Bahn | [piebro/deutsche-bahn-data](https://huggingface.co/datasets/piebro/deutsche-bahn-data) |
| Weather | [Open-Meteo Historical API](https://open-meteo.com/en/docs/historical-weather-api) |

Raw DB data (~54 GB) is **not** in this repo. Notebooks download one monthly Parquet shard from Hugging Face.

## Notebooks

| # | Notebook | Status |
|---|----------|--------|
| 01 | Project Definition & Data Understanding | Done |
| 02 | Data Acquisition & Initial Inspection | Done |
| 03 | Data Cleaning & Standardization | Done |
| 04 | Data Integration (Merge DB + Weather) | Done |
| 05 | Exploratory Data Analysis | Done |
| 06 | Feature Engineering | Planned |
| 07 | Baseline ML Models | Planned |
| 08 | Advanced ML Models | Planned |
| 09 | Model Evaluation & Tuning | Planned |
| 10 | Final Pipeline & Conclusion | Planned |

## Setup

```bash
pip install -r requirements.txt
```

Run notebooks from the `Notebooks/` folder in order. Each notebook loads config from `Notebooks/data/reference/*.json`.

## Project structure

```
ML Project/
├── Notebooks/           # Jupyter notebooks (01–05)
│   └── data/
│       ├── reference/   # JSON configs & reports (committed)
│       └── processed/   # Parquet files (gitignored — regenerate locally)
├── requirements.txt
└── README.md
```

## License & attribution

- Deutsche Bahn data: CC BY 4.0
- Open-Meteo: open API with attribution
- OpenStreetMap/Nominatim: ODbL (station geocoding)
