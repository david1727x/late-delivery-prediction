# Late Delivery Prediction with Machine Learning

Machine Learning project focused on predicting late deliveries from operational production data using Python.

The project covers the complete workflow from exploratory data analysis and preprocessing to feature engineering, model comparison, interpretation, and prediction on unseen data.

## Business Problem

Late deliveries can affect customer satisfaction, operational efficiency, and production planning.

The objective of this project is to analyze operational variables associated with delivery delays and develop a classification model capable of identifying orders at risk of being delivered late.

The target variable is:

`entrega_tardia`

- `0`: Order delivered on time
- `1`: Order delivered late

## Dataset

The project uses two datasets:

- `datos_entrenamiento_proyecto.csv`: training dataset containing 1,800 orders and the target variable.
- `datos_testeo_estudiantes_sin_target.csv`: test dataset containing 600 orders without the target variable.

The training dataset contains operational information related to production conditions, workload, capacity, scheduling, product characteristics, and other variables associated with the delivery process.

### Target Distribution

The target variable is moderately imbalanced:

- 63.7% of orders were delivered on time.
- 36.3% of orders were delivered late.

Because of this imbalance, model evaluation does not rely exclusively on Accuracy.

Metrics such as Recall, F1-score, and Balanced Accuracy are also considered.

## Project Workflow

The analysis follows an end-to-end Machine Learning workflow:

1. Data loading and structural inspection
2. Data quality analysis
3. Missing value treatment
4. Duplicate analysis
5. Outlier treatment
6. Exploratory Data Analysis
7. Categorical variable encoding
8. Feature scaling
9. Baseline model training
10. Feature Engineering
11. Model retraining and comparison
12. Model interpretation
13. Final model selection
14. Prediction on unseen data

## Exploratory Data Analysis

Exploratory analysis was performed to understand how operational variables relate to late deliveries.

The analysis included:

- Target distribution
- Delay rate by operational categories
- Distribution of numerical variables by target
- Correlation analysis
- Operational workload analysis
- Production capacity analysis
- Scheduling and instability variables

The purpose of the EDA was not only to visualize the dataset, but also to identify variables that could contribute to predicting delivery risk.

## Data Preprocessing

The preprocessing pipeline includes:

- Missing value treatment
- Outlier handling
- Categorical encoding
- Numerical feature scaling
- Separation of predictors and target
- Preparation of training and test datasets

These transformations ensure that the data can be consistently used by the Machine Learning algorithms.

## Feature Engineering

Six additional operational features were created to capture relationships that were not directly represented by the original variables:

- `carga_por_operario`
- `presion_cola_capacidad`
- `lote_por_operario`
- `indice_inestabilidad`
- `riesgo_externo`
- `degradacion_equipo`

These variables represent relationships between workload, production capacity, personnel availability, operational instability, external risk, and equipment conditions.

The models were evaluated both before and after Feature Engineering to measure its impact.

## Machine Learning Models

Three classification algorithms were evaluated:

### Logistic Regression

Used as an interpretable linear classification model and as the final selected approach.

### Perceptron

Used to evaluate a basic linear classification strategy.

### Adaline

Used as an additional linear learning algorithm for comparison.

Each model was evaluated under two scenarios:

- Baseline features
- Features after Feature Engineering

## Evaluation Metrics

The models were compared using:

- Accuracy
- Precision
- Recall
- F1-score
- Balanced Accuracy

Recall was particularly relevant because failing to identify an order that will be delivered late can be operationally costly.

Balanced Accuracy was also considered because the target variable is not perfectly balanced.

## Model Comparison

The project compares the performance of the three algorithms before and after Feature Engineering.

This analysis showed that Feature Engineering did not improve every model equally.

Rather than selecting a model based on a single metric, the final decision considered:

- Recall
- F1-score
- Balanced Accuracy
- Stability
- Interpretability

## Final Model

Logistic Regression with Feature Engineering was selected as the final model because of its balance between predictive performance and interpretability.

Approximate performance:

| Metric | Result |
|---|---:|
| Recall | 68.35% |
| F1-score | 62.00% |
| Balanced Accuracy | 69.30% |

The project also analyzes the coefficients of the Logistic Regression model to understand which variables contribute most strongly to predictions.

This makes the solution useful not only for prediction, but also for understanding operational risk factors.

## Predictions

After selecting the final model, predictions were generated for the 600 unseen orders contained in:

`datos_testeo_estudiantes_sin_target.csv`

The resulting predictions are exported as:

`predicciones_test.csv`

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## Repository Structure

```text
late-delivery-prediction/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   └── late_delivery_prediction.ipynb
│
├── data/
│   ├── datos_entrenamiento_proyecto.csv
│   └── datos_testeo_estudiantes_sin_target.csv
│
└── images/
    ├── target_analysis.png
    ├── exploratory_analysis.png
    ├── model_comparison.png
    ├── feature_importance.png
    └── confusion_matrix.png
```

## How to Run

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/late-delivery-prediction.git
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Open Jupyter Notebook:

```bash
jupyter notebook
```

Then execute:

```text
notebooks/late_delivery_prediction.ipynb
```

## Key Takeaways

This project demonstrates an end-to-end Machine Learning workflow applied to an operational classification problem.

Beyond training models, the analysis focuses on understanding the data, creating meaningful operational features, comparing multiple algorithms, selecting appropriate evaluation metrics, and interpreting the final model.

The project highlights the importance of evaluating Machine Learning models according to the business problem rather than relying exclusively on overall Accuracy.

## Author

**David Santiago Cifuentes Grimaldo**

Data Science Student  
Universidad de La Sabana

Skills demonstrated in this project:

`Python` · `Machine Learning` · `Data Analysis` · `Data Preprocessing` · `Feature Engineering` · `Logistic Regression` · `Data Visualization`
