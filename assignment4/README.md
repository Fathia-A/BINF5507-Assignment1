# 📊 Survival Analysis of Head and Neck Cancer Patients

![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg) ![License](https://img.shields.io/badge/License-MIT-green.svg)

## 📌 Overview
This project analyzes survival data from head and neck cancer patients using three survival analysis methods:
- **Kaplan-Meier Estimation**: To visualize survival probability over time.
- **Cox Proportional Hazards Model**: To identify factors affecting survival.
- **Random Survival Forest (RSF)**: To model survival using machine learning.

The dataset contains clinical information, including tumor stage, treatment modality, and HPV status. The analysis compares survival outcomes across different tumor stages and evaluates the predictive performance of different models using the concordance index (C-index).

---

## 🛠 Requirements
To run this analysis, install the necessary Python libraries:
```bash
pip install pandas numpy matplotlib seaborn lifelines scikit-survival openpyxl
```

---

## 📂 Data Processing
1. Load the dataset from an Excel file.
2. Convert the survival status column into a binary event indicator (`1 = Death`, `0 = Alive`).
3. Define survival time as `Length FU` (follow-up length in months).
4. Group tumor stages into "Early" (Stage I & II) and "Advanced" (Stage III & IV).
5. Drop missing values to ensure data integrity.

---

## 📈 Kaplan-Meier Survival Analysis
- Uses **Kaplan-Meier Fitter** from `lifelines`.
- Plots survival curves for early vs. advanced tumor stages.
- Performs a **log-rank test** to compare survival distributions between groups.

Example plot:
```python
kmf.plot_survival_function()
plt.title("Kaplan-Meier Survival Curves by Tumor Stage")
plt.xlabel("Time (Months)")
plt.ylabel("Survival Probability")
plt.legend(title="Tumor Stage")
plt.grid(True)
plt.show()
```

---

## 📊 Cox Proportional Hazards Model
- Fits a **Cox Proportional Hazards model** to identify survival predictors.
- Encodes categorical variables (tumor stage, treatment modality, HPV status).
- Outputs hazard ratios and statistical significance of predictors.

Example model fitting:
```python
cph = CoxPHFitter()
cph.fit(cox_data, duration_col="survival_time", event_col="event")
cph.print_summary()
```

---

## 🌲 Random Survival Forest (RSF)
- Trains a **Random Survival Forest** using `sksurv.ensemble`.
- Computes **feature importance** based on C-index drop.
- Evaluates model performance using the **C-index**.

Feature importance calculation:
```python
feature_importance = compute_feature_importance(rsf, X_rsf, y_rsf)
pd.Series(feature_importance).sort_values(ascending=False).plot(kind="bar")
plt.show()
```

---

## 📊 Performance Comparison
| Model | C-Index |
|--------|---------|
| Random Survival Forest | `c_index_rsf` |
| Cox Proportional Hazards | `c_index_cox` |

Higher C-index values indicate better model performance.

---

## 🚀 Usage
Run the Python script to:
- Load and preprocess the dataset.
- Perform Kaplan-Meier survival analysis.
- Fit and interpret the Cox model.
- Train and evaluate the Random Survival Forest.
- Compare model performance.

```bash
python survival_analysis.py
```

---

## 📜 Results
- Kaplan-Meier plots show differences in survival between early and advanced tumor stages.
- Cox model identifies statistically significant survival predictors.
- RSF provides feature importance rankings and a robust predictive model.

---

## ✍️ Author
**Fathia Abdelkader**  
📧 [fathia.abdelkader4@gmail.com](mailto:fathia.abdelkader4@gmail.com)

---

## 📄 License
This project is licensed under the **MIT License** and is part of the BINF5501 course assignment.

---

🔗 **GitHub Repository**: [Your Repository Link Here]

