# Data Driven Flight Delay Forecasting

## Project Overview

This repository contains a project focused on analysing historical flight operations data to understand, model, and predict flight delays. The project applies machine learning techniques to predict whether a flight will be delayed by 15 minutes or more and to estimate delay durations by different causal factors. In addition, an Operational Adjustability Index (OAI) is proposed to identify delay causes that are more controllable from an operational standpoint.

The complete implementation is provided in the Jupyter Notebook, and a detailed technical report explaining the methodology, experiments, and results is included in PDF format.

---

## Objectives

* To perform exploratory data analysis (EDA) on large-scale flight delay data.
* To build a classification model to predict whether a flight will be delayed by 15 minutes or more.
* To build regression models to estimate delay duration for different delay causes.
* To introduce and compute an Operational Adjustability Index (OAI) for prioritising operational interventions.
* To interpret model predictions using explainable AI techniques.

---

## Dataset Description

* Initial dataset size: ~179,000 flight records.
* Final dataset size after preprocessing: ~179,000 records.
* Features include airline information, airport details, temporal features, cancellation and diversion indicators, and delay causes.
* Target variable for classification: `arr_del15` (arrival delay ≥ 15 minutes).

Detailed dataset statistics and visualisations are provided in the project report.

---

## Methodology

### 1. Data Preprocessing

* Handling missing values using median imputation for numerical features.
* Treating categorical delay causes with appropriate zero-filling.
* Capping extreme outliers at the 99th percentile to reduce skew.
* Creating a binary target variable for delay classification.

### 2. Feature Engineering

* Temporal features such as quarter and time-of-day buckets.
* Ratio-based features capturing operational inefficiencies.
* Target encoding for airlines and airports based on historical delay behaviour.
* Separation of delay durations by cause (carrier, weather, NAS, security, late aircraft).

### 3. Modeling

* **Classification:** Random Forest Classifier with class balancing to predict flight delays.
* **Regression:** Multi-output Random Forest Regressor to estimate delay durations for each delay cause.
* **Explainability:** SHAP-based analysis to understand feature importance and model behaviour.

---

## Results Summary

### Classification Performance

* Model: Random Forest Classifier
* AUC-ROC: 0.89
* Recall (Delayed class): 0.98
* Precision (Delayed class): 0.97
* F1-score (Delayed class): 0.97

### Regression Performance (MAE / RMSE)

* Carrier Delay: 173.16 / 394.94
* Weather Delay: 30.48 / 90.65
* NAS Delay: 93.25 / 279.31
* Security Delay: 0.92 / 4.40
* Late Aircraft Delay: 169.58 / 412.48

### Operational Adjustability Index (OAI)

* Mean OAI Score: 6.06
* Standard Deviation: 13.91

The results indicate that carrier-related and late-aircraft delays contribute most significantly to overall delay duration and offer higher operational adjustability.

---

## Repository Structure

```
├── README.md
├── code_22123007_flight.ipynb      # Jupyter Notebook (EDA, modeling, evaluation)
├── submission_22123007_flight.pdf  # Detailed project report
└── requirements.txt               # Python dependencies (optional)
```

---

## Requirements

* Python 3.8 or higher
* Jupyter Notebook / JupyterLab

### Python Libraries

```
pandas
numpy
scikit-learn
matplotlib
seaborn
shap
```

---

## How to Run

1. Clone the repository.
2. (Optional) Create and activate a virtual environment.
3. Install required dependencies using `requirements.txt`.
4. Launch Jupyter Notebook and open `code_22123007_flight.ipynb`.
5. Run all cells sequentially to reproduce the results and visualisations.

---

## Notes

* The dataset is highly imbalanced, with the majority of flights experiencing delays.
* Class balancing techniques were applied during model training.
* Regression results should be interpreted in conjunction with SHAP explanations and OAI scores rather than as exact delay predictions.

---

## Conclusion

This project demonstrates the application of machine learning techniques to a real-world aviation dataset, combining predictive modeling with explainable AI to derive actionable operational insights. The proposed OAI framework further bridges the gap between predictive analytics and decision-making, making the project relevant for both academic evaluation and practical understanding.

---

## License

MIT License
