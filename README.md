# 🏠 Irish New Homes Market Analyser

> Automated data collection, cleaning, and analysis tools for the Irish new homes property market.
> Built by [Daniel Howley](https://github.com/) and [Ciaran Corrigan](https://github.com/)

---

## Overview

This project automates the collection of new home listings from Ireland's two largest property portals — **Daft.ie** and **MyHome.ie** — and produces clean, analysis-ready datasets with province and county tagging, data quality checks, and formatted summary reports.

The tools were built to support property market research and ad performance analysis, with a focus on accuracy, reproducibility, and ease of use for non-technical users.

---

## Projects

### 1. Daft.ie Scraper
**File:** `daft_ie/Step_2_Data_Extraction_Daft_ie_v2.ipynb`

Scrapes individual new home listing pages from daft.ie using a real Chrome browser (Selenium) to handle JavaScript-rendered content.

**Extracts:**
| Field | Description |
|-------|-------------|
| Title & Address | Full listing title and address |
| Price | Asking price in EUR |
| Beds / Baths | Number of bedrooms and bathrooms |
| Area (m²) | Floor area in square metres |
| BER Rating | Energy rating A1 through G |
| Views | Ad view count from performance section |
| Date Listed | When the ad was first posted |
| Agent Details | Name, agency, phone, PSR licence number |
| Coordinates | Latitude and longitude from map |
| Nearest Schools | Primary and secondary school from local area section |
| Daft ID | Unique listing reference from daft.ie URL |

---

### 2. MyHome.ie Scraper
**File:** `myhome_ie/MyHome_ie_New_Homes.ipynb`

Fetches all new home listings from the MyHome.ie JSON feed — no HTML scraping required. Handles price ranges, POA listings, and multi-page pagination automatically.

**Extracts:**
| Field | Description |
|-------|-------------|
| Full Address | Complete property address |
| Property Type | House, apartment, semi-detached etc. |
| Beds / Baths | Number of bedrooms and bathrooms |
| Area (m²) | Floor area where provided |
| Price Min / Max | Full price range parsed from feed |
| Price Mid | Midpoint for analysis and sorting |
| Price per m² | Calculated automatically |
| Agent Name | Listing agent |
| MyHome ID | Unique reference from MyHome.ie |
| Status | ForSale etc. |

---

## Shared Features

- **County and province standardisation** across all 32 Irish counties
- **Unique ID generation** per listing (e.g. `MHWW2026001` = MyHome, Wicklow, 2026, 1st listing)
- **Data quality sense-checking** with flagging for implausible values
- **EUR formatted outputs** readable directly in Excel
- **UTF-8 encoding** so euro signs and special characters display correctly

---

## Output Files

Each scraper produces the following CSVs automatically:

| File | Contents |
|------|----------|
| `listings_full` | Every listing, every field |
| `by_province` | Aggregated stats by province and county |
| `by_agent` | Listing count and average price by agent |
| `quality_flags` | Rows with data quality issues for review |

---

## Requirements

```bash
pip install selenium webdriver-manager beautifulsoup4 lxml pandas requests
```

You will also need:
- **Google Chrome** installed
- **ChromeDriver** (installed automatically by webdriver-manager)

---

## Usage

1. Clone or download this repository
2. Install requirements using the command above
3. Open the relevant notebook in Jupyter
4. Edit the output folder path in **Cell 1** to match your machine
5. Run cells from top to bottom

> All configuration is in Cell 1 of each notebook. No other cells need to be edited to get started.

---

## Data Sources

| Source | URL | Method |
|--------|-----|--------|
| Daft.ie | https://www.daft.ie/new-homes-for-sale/ireland | Selenium scraper |
| MyHome.ie | https://www.myhome.ie/feed/residential/ireland/new-homes/property-for-sale | JSON feed |

---

## Authors

**Daniel Howley** and **Ciaran Corrigan**

---

## Disclaimer

This project is intended for personal research and educational purposes.
Always respect the terms of service of any website you interact with.
Data collected should not be used for commercial purposes without permission.

---

*Last updated: May 2026*