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
├── src/                         # helper code (optional)
├── environment.yml              # reproducible conda environment
└── README.md

---

## ⚙️ Environment Setup

```bash
conda env create -f environment.yml
conda activate cycling
python -m ipykernel install --user --name=cycling --display-name "Python (cycling)"
jupyter lab
