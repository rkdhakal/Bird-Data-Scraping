# Bird Data Scraping Pipeline — EcoEye Project

> Automated web scraping pipeline built with Python and Selenium to collect bird image data for the EcoEye Online Bird Monitoring System — a group project developed at Loyalist College (AI & Data Science, Semester 2).

---

## Overview

This repository contains the data collection component of the EcoEye project. The scraper automates paginated image retrieval from iStock, filters by file type, and downloads images with unique timestamped filenames — producing the raw image dataset used to train EcoEye's bird species classification model.

**Output:** 128,997 observation records across 53 bird species and 170 countries, consolidated from 25+ per-species CSV exports.

---

## What the Scraper Does

- Navigates paginated web content automatically using Selenium WebDriver
- Filters results by image file type (`.jpg`, `.jpeg`, `.png`)
- Downloads images locally with unique filenames based on species name and datetime
- Handles dynamic page loading and browser automation without manual intervention

---

## Notebooks

| File | Description |
|---|---|
| `Web Scraping.ipynb` | Initial scraping prototype |
| `WebScraping_new.ipynb` | Revised version with improved pagination handling |
| `Web Scraping with names and datetime(Final).ipynb` | Enhanced version — adds species name tagging and datetime-based unique filenames |
| `Final Scraping (Code).ipynb` | Production-ready final scraper used to collect the full dataset |

---

## Tech Stack

- **Python 3.6+**
- **Selenium WebDriver** — browser automation and pagination
- **ChromeDriver** — headless Chrome browser control
- **pandas** — data consolidation and CSV merging

---

## Getting Started

### Prerequisites

```bash
pip install selenium pandas
```

Download [ChromeDriver](https://chromedriver.chromium.org/) matching your Chrome version and place it in your system PATH.

### Run the Scraper

```bash
# Clone the repo
git clone https://github.com/rkdhakal/Bird-Data-Scraping.git
cd Bird-Data-Scraping

# Open the final notebook
jupyter notebook "Final Scraping (Code).ipynb"
```

Run all cells to begin scraping. Images will be saved locally to a `/data` output folder.

---

## Project Context

This scraping pipeline was my contribution to **EcoEye**, a full-stack bird conservation monitoring platform built by a team at Loyalist College. My responsibilities included:

- Building and iterating the Selenium scraping pipeline (4 notebook versions)
- Consolidating 25+ per-species CSV exports into a single master dataset
- Cleaning and standardizing 128,997 records (resolved naming inconsistencies, removed formatting artifacts, enforced consistent schema)
- Building the **Power BI Bird Tracking dashboard** — global species presence map, quarterly migration trends, yearly/daywise sighting charts, and top state/county breakdowns

The full EcoEye project (ML model + web application) is available at: [github.com/TechnoVishalGirase/EcoEye-Online_Bird_Monitoring_System](https://github.com/TechnoVishalGirase/EcoEye-Online_Bird_Monitoring_System)

---

## Data Source

Bird observation data sourced from **iStock** and the **eBird Macaulay Library** (Cornell Lab of Ornithology), used for academic and conservation research purposes.

---

## License

Developed as part of an academic project at Loyalist College, Ontario. Contact via [GitHub](https://github.com/rkdhakal) for reuse or collaboration inquiries.
