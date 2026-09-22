# 🌫️ India AQI Data Analysis

A comprehensive data analysis project on the **Air Quality Index (AQI) of India** using historical monitoring data from 26 cities and 230 stations across the country (2015–2020).

---

## 📌 Project Description

This project explores air pollution trends across India using real-world data collected by the **Central Pollution Control Board (CPCB)**. The analysis covers:

- Loading and joining 5 related CSV datasets into unified master tables
- Thorough data cleaning following **CPCB AQI standards** — handling missing values, outliers, and recalculating AQI using the official sub-index formula
- Extracting **10+ analytical insights** including seasonal patterns, city/state rankings, pollutant correlations, and the measurable impact of the COVID-19 lockdown on air quality

---

## ⭐ Top 5 Insights

| # | Insight | Key Number |
|---|---|---|
| 1 | **National AQI improved 47%** from 2015 to 2020 | 212.5 → 113.5 |
| 2 | **PM10 is the #1 AQI driver** (r = 0.80) — road dust dominates | Correlation 0.80 |
| 3 | **Winter is 2× worse than Monsoon** — PM2.5 peaks at 110 µg/m³ in Nov | Winter avg AQI 220 |
| 4 | **Delhi, Patna & Gurugram most polluted; Aizawl cleanest** | Delhi avg AQI 259 vs Aizawl 35 |
| 5 | **COVID-19 lockdown cut AQI by 42%** in Q2 2020 vs Q1 | 145 → 83 |

---

## 📂 Dataset

**Source:** [Air Quality Data in India — Kaggle](https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india?resource=download)

| File | Rows | Description |
|---|---|---|
| `city_day.csv` | 29,531 | Daily AQI & pollutant readings per city |
| `city_hour.csv` | 707,875 | Hourly AQI & pollutant readings per city |
| `stations.csv` | 230 | Monitoring station metadata (name, city, state) |
| `station_day.csv` | 108,035 | Daily readings per monitoring station |
| `station_hour.csv` | 2,589,083 | Hourly readings per monitoring station |

> Download the dataset from the Kaggle link above and place all 5 CSV files inside a `dataset/` folder in the project root.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| **Python 3.9+** | Core programming language |
| **pandas** | Data loading, cleaning, joining, and analysis |
| **NumPy** | Numerical operations, NaN handling, clipping |
| **Jupyter Notebook** | Interactive analysis environment |
| **CPCB AQI Standard** | Official India AQI breakpoints and sub-index formula |

---

## 🗂️ Project Structure

```
AQI data analysis project/
│
├── dataset/                  # Raw CSV files (download from Kaggle)
│   ├── city_day.csv
│   ├── city_hour.csv
│   ├── stations.csv
│   ├── station_day.csv
│   └── station_hour.csv
│
├── AnkitGupta_AQIAnalysis.ipynb  # Main analysis notebook
├── requirements.txt          # Python dependencies
└── README.md                 # Project documentation
```

---

## ⚙️ Setup & Run Instructions

### 1. Clone or download the project

```bash
git clone <your-repo-url>
cd "AQI data analysis project"
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Download the dataset

Download the dataset from Kaggle:
👉 [https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india?resource=download](https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india?resource=download)

Extract all 5 CSV files into the `dataset/` folder.

### 4. Launch Jupyter Notebook

```bash
jupyter notebook AnkitGupta_AQIAnalysis.ipynb
```

Or with JupyterLab:

```bash
jupyter lab AnkitGupta_AQIAnalysis.ipynb
```

### 5. Run the notebook

Run all cells top to bottom using **Kernel → Restart & Run All**.

---

## 📊 Notebook Sections

| Section | Description |
|---|---|
| **1. Import Libraries** | Load pandas, NumPy, warnings |
| **2. Load Data** | Read all 5 CSV files with correct date parsing |
| **3. Data Cleaning** | 9-step CPCB-standard cleaning pipeline |
| **4. Join Tables** | Build 4 master tables via merge and concat |
| **5. Top 5 Key Insights** | Five major analytical findings with supporting code |
| **6. Extended Analysis** | 10 additional analyses: seasonal, hourly, city, state, lockdown |
| **7. Export** | Optionally save cleaned tables back to CSV |

---

## 🧹 Data Cleaning Pipeline

| Step | Action |
|---|---|
| Deduplication | Remove duplicate `(City/StationId, Date/Datetime)` rows |
| Empty record removal | Drop rows where **all** pollutants are missing |
| Physical caps | Values beyond CPCB instrument range → `NaN` (e.g. AQI > 500) |
| Outlier clipping | Per-group 99th-percentile ceiling |
| Interpolation | Linear time-series interpolation within each city/station |
| Forward/back fill | Gap-fill up to 3 h (hourly) or 7 d (daily) |
| Group median fill | Remaining gaps filled with city/station median |
| AQI recalculation | CPCB sub-index formula re-applied where AQI was missing or out-of-range |
| AQI_Bucket | Fully re-derived using official CPCB breakpoints |

---

## 📜 License

This project is for educational and analytical purposes.  
Dataset credit: [Rohan Rao on Kaggle](https://www.kaggle.com/rohanrao) — sourced from CPCB India.
