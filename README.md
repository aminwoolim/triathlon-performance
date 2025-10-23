# Triathlon Performance

A data science project exploring **endurance sports performance** across cycling, running, and swimming.  
The initial phase focuses on **cycling effectiveness** — comparing **indoor vs. outdoor sessions** and analyzing **time of day** impacts on performance.  
Future phases will expand to **running and swimming**, culminating in a unified **triathlon performance dashboard**.

---

## 📊 Current Results (Cycling Phase)

- **Effectiveness definition**: higher **calories per minute** and **Training Stress Score (TSS) per minute**.  
- **ANOVA results**:  
  - Session type (indoor vs. outdoor) showed *no significant difference*.  
  - Time of day (morning vs. afternoon/evening) showed a *significant effect* on both calories burned and TSS.  
- **Machine learning models (TensorFlow)**:  
  - Regression model predicts calories per minute with strong performance (**R² ≈ 0.85**).  
  - Classification model identifies “high effectiveness” sessions with promising accuracy.

---

## 🏃🏻 Running Results & Findings
- **Regression (Pace Prediction)
	- Mean Absolute Error (MAE): 0.46 min/km (~28 seconds/km)
   	- R^2: 0.85 -> model explains 85% of variance in running pace
   	- Interpretation: The regression model accurately predicts pace using distance, elevation, and time-of-day features.
- ** Classification (High Effectiveness Runs)
  	- Accuracy: 80%
  	- Recall (High Effectiveness): 1.00 -> model catches all high-performing rungs
  	- ROC AUC: 1.0 -> perfect separation of high vs. low effectiveness
  	- Interpretation: The classifier is highly effective at identifying "top quartile" runs (based on pace), never missing a high-performing run.

## 📂 Repository Structure

triathlon-performance/
├── data/              # raw and cleaned datasets
├── docs/              # schema and design notes
│   └── schema.md
├── notebooks/         # Jupyter notebooks (currently cycling only)
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
- 🔜 **Phase 3:** Unified triathlon schema ([docs/schema.md](docs/schema.md)).  
- 🔜 **Phase 4:** Streamlit dashboard for real-time KPIs and predictions.  
- 🔜 **Phase 5:** Strava API integration for live data sync.  

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
