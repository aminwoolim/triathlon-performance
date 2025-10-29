# Triathlon Performance

A data science project exploring endurance performance across cycling, running, and swimming.
The goal is to uncover what factors drive training effectiveness across sports — including time of day, indoor vs. outdoor conditions, and physical metrics such as distance, duration, and elevation.

The project combines **data engineering**, **statistical analysis**, and **machine learning** to model and compare performance patterns, forming the foundation for a future triathlon performance dashboard.

---

## 📊 Cycling Results & Findings

**Effectiveness definition**: higher **calories per minute** and **Training Stress Score (TSS) per minute** indicate higher effectiveness  

**Key Insights**:  
  - Session type (indoor vs. outdoor) showed *no significant difference*.  
  - Time of day (morning vs. afternoon/evening) showed a *significant effect* on both calories burned and TSS.  
  - Regression model (Tensorflow) predicts calories per minute with strong performance (**R² ≈ 0.85**).  
  - Classification model identifies “high effectiveness” sessions.

---

## 🏃🏻 Running Results & Findings
- **Regression (Pace Prediction)
	- Mean Absolute Error (MAE): 0.46 min/km (~28 seconds/km)
   	- R^2: 0.85 -> model explains 85% of variance in running pace
   	- Interpretation: Distance, elevation, and time-of-day are strong predictors of pace.
- ** Classification (High Effectiveness Runs)
  	- Accuracy: 80%
  	- Recall (High Effectiveness): 1.00 -> model catches all high-performing rungs
  	- ROC AUC: 1.0 -> perfect separation of high vs. low effectiveness
  	- Interpretation: The classifier is highly effective at identifying "top quartile" runs (based on pace).

## 🏊🏻‍♂️ Swimming Results & Findings

Classification (High-Effectiveness Swims):
- Accuracy: 95%
- Precision: 1.00 (for standard sessions)
- Recall: 0.93 (for high-effectiveness swims)
- ROC AUC: 0.88
- Interpretation: The model successfully distinguishes high-performing swim sessions, through regression analysis was not performed due to limited continuous performance metrics (e.g., pace or TSS data).

## 🥇 Cross-Sport Effectiveness Summary

**Goal**: Unify insights from cycling, running, and swimming to measure effectiveness across disciplines.

**Normalized Metric:**
Each sport's effectiveness score was scaled from 0-1 (e.g., lower pace = higher effectiveness for running).

**Findings:**
- **Distance** and **duration** are universal predictors of performance across sports
- **Morning sessions** show slightly higher average effectiveness across all activities
- Cycling effectiveness varies most by duration, while running is more sensitive to elevation
- Combined model explains ~80% of variance in session effectiveness (R^2 = 0.8)

See anaysis notebook:
notebooks/triathlon_04_effectiveness_summary.ipynb

## 📂 Repository Structure

triathlon-performance/
├── data/              # raw and cleaned datasets
├── docs/              # schema and design notes
│   └── schema.md
├── notebooks/         # Jupyter notebooks for each sport
│   ├── cycling_01_data_cleaning.ipynb
│   ├── cycling_02_eda_anova.ipynb
│   └── cycling_03_ml_models.ipynb
├── results/           # plots, models, and outputs
├── src/               # helper Python code (future use)
├── environment.yml    # conda environment specification
├── .gitignore
└── README.md

---

## 🚀 Roadmap

- ✅ **Phase 1:** Cycling analysis (cleaning, EDA, ANOVA, ML models).  
- ✅ **Phase 2:** Add running and swimming datasets.  
- ✅ **Phase 3:** Unified triathlon schema ([docs/schema.md](docs/schema.md)).  
  

---

## ⚡ Getting Started

Clone the repo and install dependencies:

```bash
git clone https://github.com/aminwoolim/triathlon-performance.git
cd triathlon-performance
conda env create -f environment.yml
conda activate cycling
```

## 🎯 Vision

The long-term goal is to build a triathlon performance dashboard where:
  - Athletes can track cycling, running, and swimming sessions in real time.
	- Machine learning models predict effectiveness and progress toward race readiness (e.g., triathlon, half-Ironman).
  - Visual KPIs compare predicted vs. actual performance.
  - Data can be ingested from the Strava API or uploaded manually.
