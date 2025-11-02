# Triathlon Performance

A data science project exploring endurance performance across cycling, running, and swimming.
The goal is to uncover what factors drive training effectiveness across sports — including time of day, indoor vs. outdoor conditions, and physical metrics such as distance, duration, and elevation.

The project combines **data engineering**, **statistical analysis**, and **machine learning** to model and compare performance patterns, forming the foundation for a future triathlon performance dashboard.

---

## Cycling Results & Findings

**Effectiveness definition**: higher **calories per minute** and **Training Stress Score (TSS) per minute** indicate higher effectiveness  

**Key Insights**:  
  - Session type (indoor vs. outdoor) showed *no significant difference*.  
  - Time of day (morning vs. afternoon/evening) showed a *significant effect* on both calories burned and TSS.  
  - Regression model (Tensorflow) predicts calories per minute with strong performance (**R² ≈ 0.85**).  
  - Classification model identifies “high effectiveness” sessions.

---

## Running Results & Findings
- Regression (Pace Prediction)
	- Mean Absolute Error (MAE): 0.46 min/km (~28 seconds/km)
   	- R^2: 0.85 -> model explains 85% of variance in running pace
   	- Interpretation: Distance, elevation, and time-of-day are strong predictors of pace.
- Classification (High Effectiveness Runs)
  	- Accuracy: 80%
  	- Recall (High Effectiveness): 1.00 -> model catches all high-performing rungs
  	- ROC AUC: 1.0 -> perfect separation of high vs. low effectiveness
  	- Interpretation: The classifier is highly effective at identifying "top quartile" runs (based on pace).

## Swimming Results & Findings

Classification (High-Effectiveness Swims):
- Accuracy: 95%
- Precision: 1.00 (for standard sessions)
- Recall: 0.93 (for high-effectiveness swims)
- ROC AUC: 0.88
- Interpretation: The model successfully distinguishes high-performing swim sessions, through regression analysis was not performed due to limited continuous performance metrics (e.g., pace or TSS data).

## Cross-Sport Effectiveness Analysis

Combined all sports into a single normalized effectiveness framework.

| Factor         | Statistical Test | p-value | Interpretation                                      |
|----------------|------------------|----------|----------------------------------------------------|
| **Sport**      | Two-Way ANOVA    | 0.9866   | No significant difference — balanced effectiveness across sports |
| **Time of Day**| Two-Way ANOVA    | 0.5166   | No significant difference — consistent performance regardless of training time |

**Normalized Metric:**
Each sport's effectiveness score was scaled from 0-1 (e.g., lower pace = higher effectiveness for running).


| Sport     | Count | Mean   | Std    | 25%   | 50%   | 75%   |
|------------|--------|--------|--------|--------|--------|--------|
| Cycling    | 299    | 0.502  | 0.289  | 0.25   | 0.50   | 0.75   |
| Running    | 180    | 0.503  | 0.289  | 0.26   | 0.50   | 0.75   |
| Swimming   | 100    | 0.505  | 0.290  | 0.26   | 0.51   | 0.75   |

**Findings:**
- **Distance** and **duration** are universal predictors of performance across sports
- **Morning sessions** show slightly higher average effectiveness across all activities
- Cycling effectiveness varies most by duration, while running is more sensitive to elevation
- Combined model explains ~80% of variance in session effectiveness (R^2 = 0.8)



## Repository Structure

triathlon-performance/
├── data/                  # Raw and cleaned datasets
├── notebooks/             # Analysis notebooks
│   ├── cycling_01_data_cleaning.ipynb
│   ├── cycling_02_eda_anova.ipynb
│   ├── cycling_03_ml_models.ipynb
│   ├── running_01_data_cleaning.ipynb
│   ├── running_02_eda_ml.ipynb
│   ├── running_03_ml_retrain.ipynb
│   ├── swimming_01_data_cleaning.ipynb
│   ├── swimming_02_eda.ipynb
│   ├── swimming_03_ml_models.ipynb
│   └── triathlon_04_effectiveness_summary.ipynb
├── results/               # Plots, models, and statistical outputs
├── docs/                  # Schema and design notes
│   └── schema.md
├── environment.yml        # Conda environment specification
└── README.md

---

## Roadmap

- ✅ **Phase 1:** Cycling analysis (cleaning, EDA, ANOVA, ML models).  
- ✅ **Phase 2:** Running and swimming datasets and analysis  
- ✅ **Phase 3:** Unified triathlon effectiveness summary (cross-sport comparison).

## Key Insights
- Machine learning models can successfully predict and classify endurance effectiveness across multiple sports
- Statistical tests confirm balanced performance across all three disciplines
- The framework enables future work in performance optimization, load management, or personalized training modeling

## Conclusion

This project demonstrates a complete data science workflow — from raw data cleaning and exploratory analysis to predictive modeling and cross-sport evaluation. Through systematic feature engineering and normalization, it shows how quantitative metrics (pace, calories, TSS) can be harmonized across different endurance sports to measure training effectiveness and performance consistency.
  

---

## ⚡ Getting Started

Clone the repo and install dependencies:

```bash
git clone https://github.com/aminwoolim/triathlon-performance.git
cd triathlon-performance
conda env create -f environment.yml
conda activate cycling
```

