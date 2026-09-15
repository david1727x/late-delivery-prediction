# Late Delivery Prediction with Machine Learning

[Español](README_ES.md) | **English**

Machine Learning project focused on identifying production orders at risk of late delivery using operational data and interpretable linear classification models.

Built with **Python, Pandas, NumPy, Scikit-learn, Matplotlib, and Seaborn**.

> This project was developed as an academic Machine Learning case study in the Data Science program at Universidad de La Sabana. It is presented as a portfolio project to demonstrate data preprocessing, exploratory analysis, feature engineering, classification, model comparison, and interpretation skills.

## Business Problem

Late deliveries can affect customer satisfaction, production planning, and operational efficiency. The objective of this project is to analyze operational variables associated with delivery delays and build a classification workflow for identifying orders with higher late-delivery risk.

The target variable is `entrega_tardia`:

- `0`: order delivered on time
- `1`: order delivered late

## Dataset

The original academic case uses:

- A labeled training dataset with **1,800 production orders** and 22 columns including the target.
- An unlabeled dataset with **600 orders** and 21 predictor columns for final prediction.

The labeled target distribution is:

- **1,146 on-time orders (63.7%)**
- **654 late orders (36.3%)**

Because the classes are moderately imbalanced, the analysis considers Recall, F1-score, and Balanced Accuracy in addition to overall Accuracy.

> The original CSV files are not currently included in this public repository. The repository currently contains the project notebook and documentation.

## Project Workflow

The analysis covers:

1. Data loading and structural inspection
2. Data quality analysis
3. Missing-value treatment
4. Duplicate and outlier analysis
5. Exploratory Data Analysis
6. Categorical encoding and numerical scaling
7. Baseline model training
8. Feature Engineering
9. Model retraining and comparison
10. Confusion-matrix analysis
11. Logistic Regression coefficient interpretation
12. Final model selection
13. Prediction of the 600 unlabeled orders

## Feature Engineering

Six operational features were created to represent relationships not directly captured by the original variables:

- `carga_por_operario`
- `presion_cola_capacidad`
- `lote_por_operario`
- `indice_inestabilidad`
- `riesgo_externo`
- `degradacion_equipo`

These variables combine information related to workload, production capacity, personnel availability, instability, external risk, and equipment condition.

An important result of the experiment is that **Feature Engineering did not improve every model or metric**. The engineered features were therefore treated as an experimental modeling alternative rather than automatically assumed to improve predictive performance.

## Models Evaluated

Three linear classification approaches were compared:

- Logistic Regression
- Perceptron
- Adaline

Each model was analyzed with baseline features and after Feature Engineering.

## Reported Experimental Metrics

The notebook reports the following metrics for the baseline models:

| Model | Accuracy | Recall | F1-score | Balanced Accuracy |
|---|---:|---:|---:|---:|
| Logistic Regression | 69.39% | 69.27% | 62.18% | 69.36% |
| Perceptron | 66.50% | 48.01% | 51.02% | 62.53% |
| Adaline | 72.67% | 59.17% | 61.14% | 69.77% |

After Feature Engineering:

| Model | Accuracy | Recall | F1-score | Balanced Accuracy |
|---|---:|---:|---:|---:|
| Logistic Regression | 69.56% | 68.35% | 62.00% | 69.30% |
| Perceptron | 57.67% | 59.48% | 50.52% | 58.06% |
| Adaline | 73.11% | 59.79% | 61.77% | 70.25% |

### Evaluation limitation

These values are **training-set metrics reported by the current notebook**, not held-out validation or unseen-test performance. They are useful for documenting the academic experiment, but they should not be interpreted as estimates of generalization performance.

A stronger production-oriented version of this project would use a stratified train/validation split or cross-validation, fit preprocessing only on training folds, evaluate model selection on validation data, and then refit the selected pipeline on all labeled observations before predicting the 600 unlabeled orders.

## Feature Engineering Comparison

For Logistic Regression, Feature Engineering changed the reported training metrics only slightly:

| Metric | Baseline | Feature Engineering |
|---|---:|---:|
| Accuracy | 69.39% | 69.56% |
| Recall | 69.27% | 68.35% |
| F1-score | 62.18% | 62.00% |
| Balanced Accuracy | 69.36% | 69.30% |

This is a useful modeling lesson: additional features do not necessarily produce better results. Feature Engineering should be evaluated empirically rather than assumed to improve a model.

## Final Model in the Academic Experiment

The notebook selects **Logistic Regression with Feature Engineering** based on the project's intended balance of Recall, F1-score, stability, and interpretability.

This choice is not presented as the model with the highest value for every metric. For example, Adaline records higher training Accuracy and Balanced Accuracy in the reported experiment.

Logistic Regression was favored because its coefficients also provide a direct way to inspect how operational variables contribute to the classification decision.

## Predictions on Unlabeled Orders

After model selection, the academic workflow generates predictions for **600 unlabeled orders**:

- **330 predicted on time**
- **270 predicted late**
- **45.0% predicted late-delivery rate**

These are model predictions for records without known target labels and therefore are not an accuracy evaluation.

## Technologies

`Python` · `Pandas` · `NumPy` · `Scikit-learn` · `Matplotlib` · `Seaborn` · `Jupyter Notebook`

## Current Repository Structure

```text
late-delivery-prediction/
├── README.md
├── README_ES.md
└── Proyecto_corte2_corregido.ipynb
```

This structure reflects the repository as it currently exists. Future portfolio improvements can standardize the notebook filename and add environment/dependency documentation.

## How to Explore the Project

Clone the repository:

```bash
git clone https://github.com/david1727x/late-delivery-prediction.git
cd late-delivery-prediction
```

Open the notebook with Jupyter:

```bash
jupyter notebook Proyecto_corte2_corregido.ipynb
```

The original academic datasets are required to reproduce the complete execution and are not currently included in the public repository.

## Skills Demonstrated

`Machine Learning` · `Python` · `Data Analysis` · `Data Preprocessing` · `Feature Engineering` · `Logistic Regression` · `Classification` · `Model Interpretation` · `Data Visualization`

## Author

**David Santiago Cifuentes Grimaldo**  
Data Science Student  
Universidad de La Sabana
