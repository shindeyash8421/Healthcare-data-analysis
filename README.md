# Healthcare Data Analytics Project

## 📌 Overview
This project analyzes a healthcare dataset of 54,966 patient records to uncover patterns in patient demographics, medical conditions, hospital billing, and treatment outcomes. It includes exploratory data analysis (EDA) and a predictive modeling experiment for hospital billing amounts.

## 📊 Dataset
- **Source:** `cleaned_healthcare_dataset.xlsx`
- **Records:** 54,966
- **Columns:** Name, Age, Gender, Blood Type, Medical Condition, Date of Admission, Doctor, Hospital, Insurance Provider, Billing Amount, Room Number, Admission Type, Discharge Date, Medication, Test Results

## 🔍 Exploratory Data Analysis
Key steps performed:
- Distribution checks for Gender, Medical Condition, Admission Type, Medication, and Test Results
- Correlation analysis between Age, Billing Amount, and Room Number
- Cross-tabulations: Medical Condition × Gender, Medication × Test Results
- Average Billing Amount by Medical Condition and Insurance Provider
- Age distribution across medical conditions (boxplot)

## 📏 Length of Stay Analysis
- Engineered a `length stay DAYS` feature from `Discharge Date - Date of Admission`.
- Average Length of Stay is ~15.5 days across the board, with no meaningful difference between medical conditions or admission types (range: 15.4–15.7 days).

## 🧪 Statistical Testing (Chi-Square)
Chi-square tests of independence were run to formally validate relationships observed in the crosstabs:

| Test | Chi² | p-value | Conclusion |
|---|---|---|---|
| Medication vs Test Results | 3.85 | 0.87 | No significant relationship |
| Medical Condition vs Gender | 1.07 | 0.96 | No significant relationship |
| Medical Condition vs Admission Type | 17.89 | 0.057 | No significant relationship |

All three tests confirm categorical variables in this dataset are statistically independent of one another.

## 🤖 Predictive Modeling
**Goal:** Predict `Billing Amount` from `Age`, `Medical Condition`, `Admission Type`, and `Insurance Provider` using Linear Regression.

**Result:**
| Metric | Value |
|---|---|
| R² Score | ≈ 0.00 (-0.0003) |
| MAE | ≈ $12,371 (on an average billing amount of $25,544, ≈48% error) |

**Interpretation:** The model performs no better than predicting the average billing amount for every patient. This confirms the EDA finding — these four features have no meaningful linear relationship with billing cost in this dataset. Rather than treating this as a failure, it's reported here as a validated finding: feature-target relationships should always be checked (via correlation/statistical testing) *before* trusting a model's predictions.

## 🔑 Key Findings

**Demographics & Medical Conditions**
- 54,966 patient records evenly split across 6 medical conditions (Arthritis, Asthma, Cancer, Diabetes, Hypertension, Obesity) — roughly 9,150 patients each.
- Gender distribution is balanced (~50/50) within every medical condition.
- Age distribution is nearly identical across all conditions (median ~51, range 13–90).

**Hospital Operations**
- Admission types are evenly distributed: Elective (18,473), Urgent (18,391), Emergency (18,102).
- Average Length of Stay is ~15.5 days with no meaningful variation by condition or admission type.

**Billing & Financial Patterns**
- Age, Billing Amount, and Room Number are effectively uncorrelated with one another (all |r| < 0.01).
- Average billing amount does not vary meaningfully by medical condition or insurance provider.

**Overall Conclusion**
Across every method used — correlation analysis, cross-tabulation, boxplots, Chi-square hypothesis testing, and predictive modeling — the data consistently shows **no meaningful relationship between patient demographics/condition and hospital billing or length of stay.** This strongly suggests the dataset's key numeric and categorical fields were generated independently/synthetically rather than reflecting real-world medical cost drivers.

**Skills Demonstrated**
- Data cleaning and preprocessing (Pandas)
- Exploratory Data Analysis (grouping, cross-tabulation, correlation)
- Data visualization (Seaborn/Matplotlib)
- Statistical hypothesis testing (Chi-square test of independence)
- Feature engineering (Length of Stay calculation)
- Predictive modeling and honest model evaluation (Linear Regression, R², MAE)

## 🛠️ Tools Used
- **Python:** pandas, numpy, matplotlib, seaborn, scikit-learn
- **Techniques:** EDA, correlation analysis, cross-tabulation, one-hot encoding, train/test split, Linear Regression, model evaluation (R², MAE)

## 📁 Project Structure
```
healthcare-data-analytics/
├── data/
│   └── cleaned_healthcare_dataset.xlsx
├── notebooks/
│   └── healthcare_analysis.ipynb
├── images/
├── README.md
```

## ▶️ How to Run
```bash
pip install -r requirements.txt
jupyter notebook notebooks/healthcare_analysis.ipynb
```

## 🚀 Future Work
- Build an interactive Power BI dashboard for hospital administrators
- Test additional features (Gender, Blood Type, Hospital) and non-linear models (Random Forest) to see if predictive power improves

## 👤 Author
Yash Shinde — [LinkedIn] — (https://github.com/shindeyash8421)
