# EcoEye — Bird Monitoring: Data Pipeline & Species Classification

> End-to-end machine learning project for bird species monitoring — from automated data collection through deep learning classification and interactive Power BI visualization. Built as part of the EcoEye Online Bird Monitoring System at Loyalist College (AI & Data Science Program).

---

## Project Overview

This repository covers two core components of the EcoEye project:

1. **Data Pipeline** — Automated Selenium-based web scraper that collected bird image data from iStock and eBird, producing a structured dataset of 128,997 observation records across 53 species and 170 countries
2. **Species Classification Model** — EfficientNetB0 transfer learning model trained on 1,695 labeled bird images achieving **97.35% test accuracy** across 10 species
3. **Power BI Dashboard** — Interactive Bird Tracking dashboard visualizing migration trends, global species presence, and population statistics

---

## Power BI Dashboard

![Bird Tracking Dashboard](images/dashboard_preview.png)

The Bird Tracking dashboard provides:

| Panel | Description |
|---|---|
| **Quarterly Migrations** | Q1–Q4 bar chart showing seasonal sighting volume |
| **Species Panel** | Population counts per monitored species |
| **Population Counter** | 288,562 total observations tracked |
| **Global Presence Map** | Bubble map of species sighting density across 170 countries |
| **Yearly Seeings** | Line chart of annual observation growth (1964–2024) |
| **Daywise Seeings** | Area chart of intra-week sighting patterns |
| **Top States / Counties** | Florida, California leading; Orange (290), San Diego (149), Palm Beach (110) |

---

## ML Model Results

| Metric | Score |
|---|---|
| Test Accuracy | **97.35%** |
| Macro Avg Precision | 0.98 |
| Macro Avg Recall | 0.97 |
| Macro Avg F1-Score | 0.97 |
| Test Set Size | 339 images |

**Species classified:** African Emerald Cuckoo · African Pied Hornbill · Albatross · American Bittern · Golden Cheeked Warbler · Gray Kingbird · Long-Eared Owl · Myna · Razorbill · Red Tailed Hawk

---

## Repository Structure

```
EcoEye-Bird-Monitoring/
├── notebooks/
│   ├── 01_scraping/
│   │   ├── Web Scraping.ipynb                                  # Initial prototype (eBird)
│   │   ├── WebScraping_new.ipynb                               # Improved pagination handling
│   │   ├── Web Scraping with names and datetime(Final).ipynb   # Species-tagged filenames
│   │   └── Final Scraping (Code).ipynb                         # Production scraper (iStock)
│   └── 02_model/
│       └── Bird_Species_Classification.ipynb                   # EfficientNetB0 model (97.35%)
├── images/
│   └── dashboard_preview.png                                   # Power BI dashboard screenshot
├── requirements.txt
├── .gitignore
└── README.md
```

---

## Tech Stack

| Component | Tools |
|---|---|
| Data Collection | Python, Selenium, requests |
| Data Processing | Python, pandas |
| Machine Learning | TensorFlow, Keras, EfficientNetB0, scikit-learn |
| Visualization | Power BI, matplotlib, seaborn |
| Environment | Google Colab, Jupyter Notebook |

---

## Dataset

- **Source:** iStock (image scraping) + eBird Macaulay Library (observation records)
- **Training images:** 1,695 across 10 species (80/20 train/test split)
- **Observation records:** 128,997 records across 53 species and 170 countries
- **Fields:** Species name, date, latitude/longitude, country, state/county, behaviors, community rating

---

## Model Architecture

- **Base model:** EfficientNetB0 pretrained on ImageNet (frozen weights)
- **Custom head:** Dense(128, ReLU) → Dropout(0.45) → Dense(256, ReLU) → Dropout(0.45) → Dense(10, Softmax)
- **Data augmentation:** Random flip, rotation (±10°), zoom (±10%), contrast (±10%)
- **Optimizer:** Adam (lr=0.0001) with ReduceLROnPlateau
- **Callbacks:** EarlyStopping (patience=5), ModelCheckpoint (best val_accuracy)
- **Interpretability:** Grad-CAM heatmap visualization showing model attention regions

---

## Getting Started

### Prerequisites

```bash
pip install -r requirements.txt
```

For the scraper, also download [ChromeDriver](https://chromedriver.chromium.org/) matching your Chrome version.

### Run the Scraper

1. Open `notebooks/01_scraping/Final Scraping (Code).ipynb`
2. Update the `CONFIGURATION` cell (species name, page range, ChromeDriver path)
3. Run all cells — images save to `downloaded_images/<species_name>/`

### Run the Classification Model

1. Open `notebooks/02_model/Bird_Species_Classification.ipynb` in Google Colab
2. Mount your Google Drive and update the dataset path
3. Run all cells to train, evaluate, and visualize predictions

---

## My Contribution

This was a group project. My responsibilities:

- **Scraping pipeline** — built and iterated 4 versions of the Selenium scraper to collect per-species bird images from iStock and eBird
- **Data consolidation** — merged 25+ per-species CSV exports, resolved naming inconsistencies, standardized schema across 128,997 records
- **ML model** — built the EfficientNetB0 transfer learning classifier achieving 97.35% accuracy; implemented data augmentation, callbacks, Grad-CAM interpretability, and single-image prediction
- **Power BI dashboard** — designed the Bird Tracking dashboard including global species presence map, quarterly migration charts, yearly/daywise sighting trends, and county-level breakdowns

---

## Full Project

The complete EcoEye web application (UI + deployment) is available at:
[github.com/TechnoVishalGirase/EcoEye-Online_Bird_Monitoring_System](https://github.com/TechnoVishalGirase/EcoEye-Online_Bird_Monitoring_System)

---

## License

Developed as part of an academic project at Loyalist College, Ontario. Contact via [GitHub](https://github.com/rkdhakal) for reuse or collaboration inquiries.
