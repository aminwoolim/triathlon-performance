# Cycling Effectiveness Analysis 🚴‍♂️

**Goal:**  
Determine whether indoor vs. outdoor cycling and time of day influence training effectiveness.  
Effectiveness is defined as **calories per minute** and **training stress score (TSS) per minute**.

---

## 📂 Project Structure
cycling-effectiveness/
├── notebooks/
│   ├── 01_data_cleaning.ipynb   # load & clean data, feature engineering
│   ├── 02_eda_anova.ipynb       # exploratory viz + two-way ANOVA
│   └── 03_ml_models.ipynb       # TensorFlow regression & classification
├── data/
│   └── README.md                # how to obtain the dataset
├── results/                     # saved models & plots
├── src/                         # helper code
├── environment.yml              # reproducible conda environment
└── README.md

---

## ⚙️ Environment Setup

```bash
conda env create -f environment.yml
conda activate cycling
python -m ipykernel install --user --name=cycling --display-name "Python (cycling)"
jupyter lab
```
## Results and Findings

- Data Cleaning & Preparation:
  - Extracted and standardized dats/times into Date and Time columns
  - Engineered features such as Session_Type (Indoor vs. Outdoor), Time_of_Day (Morning, Afternoon, Evening), and normalized metrics (Calories/min, TSS/min)
  - Removed duplicates, handled missing values, and ensured numeric consistency for analysis and ML
 
- Exploratory Data Analysis (EDA):
  - Indoor sessions: mostly classified as indoor cycling and virtual rides
  - Outdoor sessions: road biking, cycling, cyclocross
  - Calories burned and TSS showed wide variance, with time of day as stronger differentiator than indoor vs. outdooe
  - Violin plots revealed that afternoon sessions tended to produce high calorie burn and TSS distributions

- Statistical Testing (Two-Way ANOVA):
  - Session Type (Indoor vs. Outdoor): Not statistically significant (p > 0.01)
  - TIme of Day (Morning/Afternoon/Evening): Highly significant - afternoon rides had measurably higher effectiveness
  - Interaction (Session Type x Time of Day): Not significant - the effect of time of day holds across both indoor and outdoor rides

- ML Models (TensorFlow):
  - Regression (Calories/min): Achieved strong predictive performance with R^2 approximately 0.86, showing that ride metrics can explain most variance in caloric efficiency
  - Classification (High vs. Low effectiveness): Classifier successfully separated high-effectiveness rides (top 25% calories/min) from others, with good acuracy and ROC/AUC
  - Important features included duration, distance, average HR, average speed, and time of day dummies

## Conclusion

- Time of day is the dominant factor: afternoon sessions consistently yield higher training stress and calorie burn efficiency
- Indoor vs. outdoor distinction does not significantly change training effectiveness in this dataset
- Predictive models are able to generalize well, suggesting potential for real-time effectiveness forecasting on new ride data



