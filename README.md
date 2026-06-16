# Predictive-Modeling-of-Obesity-Risk-for-AI-Assisted-Clinical-Decision-Support

## Overview

This project applied machine learning techniques to predict obesity risk using population-level health survey data from the Centers for Disease Control and Prevention (CDC) Behavioral Risk Factor Surveillance System's (BRFSS) 2024 dataset.

Obesity is a complex, multifactorial condition associated with numerous chronic diseases, including cardiovascular disease, type 2 diabetes, hypertension, and other adverse health outcomes. Early identification of individuals at elevated risk remains challenging due to the large number of behavioral, demographic, socioeconomic, and health-related factors that contribute to obesity.

The goal of this project was to develop and evaluate machine learning models capable of identifying obesity risk and to explore their potential use as a clinical decision support tool for healthcare professionals.

## Research Objective

This study investigated whether behavioral, demographic, socioeconomic, and health-related variables could effectively predict obesity status.

### Specific objectives included:
- Predicting obesity risk using CDC BRFSS 2024 survey data.
- Comparing the performance of multiple machine learning approaches.
- Evaluating the tradeoffs between model interpretability and predictive performance.
- Exploring the potential of machine learning models as clinical decision support systems.

## Dataset Source

CDC Behavioral Risk Factor Surveillance System (BRFSS) 2024

The BRFSS is one of the largest ongoing health-related survey systems in the world and contains responses from over 400,000 participants across the United States.

### Data Characteristics
- 400,000+ observations
- Nationally representative health survey data
- Behavioral variables
- Demographic variables
- Socioeconomic indicators
- Health status information
- Target Variable

## Obesity status was defined using Body Mass Index (BMI):

Obese = BMI ≥ 30
Non-Obese = BMI < 30

The prediction task was framed as a binary classification problem.

## Methodology
### Data Preprocessing

The raw BRFSS data was provided in fixed-width ASCII format and was converted into a structured dataset using CDC SAS labeling documentation.

### Preprocessing steps included:
- Variable selection based on obesity relevance
- Missing value imputation
- Median imputation for continuous variables
- Mode imputation for categorical variables
- One-hot encoding of nominal variables
- Preservation of ordinal variable rankings
- Feature engineering and cleaning
- Train-Test Split

The dataset was divided using an 80/20 stratified split to preserve class distributions across training and testing sets.

### Class Distribution

The final dataset exhibited class imbalance:
Class	Percentage
Non-Obese	69.3%
Obese	30.7%

### Models Evaluated
1. Dummy Classifier
A baseline model was used to establish minimum performance expectations.

2. Logistic Regression
An interpretable linear classification model was developed to evaluate relationships between predictors and obesity risk.

3. Gradient Boosting
An ensemble machine learning approach was implemented to capture nonlinear relationships and complex feature interactions.

### Models were evaluated using:
- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC

### Additional evaluation techniques included:
- Confusion Matrices
- ROC Curves

Because obesity prediction involved identifying at-risk individuals, particular emphasis was placed on Recall and F1 Score rather than Accuracy alone.

## Results

### Model Performance Comparison
| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|--------|----------|-----------|--------|----------|---------|
| Dummy Classifier | 0.693 | 0.000 | 0.000 | 0.000 | — |
| Logistic Regression | 0.625 | 0.423 | 0.607 | 0.498 | 0.665 |
| Gradient Boosting | 0.713 | 0.579 | 0.240 | 0.339 | 0.708 |

### Key Findings

#### Dummy Classifier
- Although the baseline model achieved 69.3% accuracy, it failed to identify any obese individuals. This demonstrated why accuracy alone can be misleading when working with imbalanced datasets.

#### Logistic Regression

Logistic Regression achieved:

Higher recall
Better F1 score
Greater interpretability

The model successfully identified a larger proportion of obese individuals, making it more useful for screening and early intervention scenarios.

#### Gradient Boosting

Gradient Boosting achieved:

Higher overall accuracy
Higher precision
Higher ROC-AUC

However, it demonstrated substantially lower recall, meaning many at-risk individuals were not identified.

## Discussion

The findings supported the hypothesis that behavioral, demographic, socioeconomic, and health-related variables contained meaningful predictive information related to obesity risk.

Both machine learning models outperformed the baseline classifier, confirming that obesity risk could be modeled using population-level survey data.

Contrary to the alternative hypothesis, Gradient Boosting did not outperform Logistic Regression in a clinically meaningful way. Although Gradient Boosting achieved superior accuracy and precision, its low recall reduced its usefulness for identifying individuals who may have benefited from early intervention.

These findings highlighted an important consideration in healthcare machine learning:

The best model was not necessarily the most accurate model.

For clinical screening applications, maximizing recall is often more important than maximizing accuracy because missing at-risk individuals could have significant health consequences.

Logistic Regression also provided transparency and explainability, making it easier for healthcare professionals to understand the factors contributing to predictions.

### Limitations

Several limitations were identified:
- Cross-sectional survey data prevented causal inference.
- BRFSS data relied on self-reported responses.
- Potential reporting bias may have affected data quality.
- Obesity was treated as a binary outcome, reducing granularity.
- External validation on independent datasets was not performed.

### Clinical Relevance

This project demonstrated how machine learning could support clinical decision-making by:
- Identifying individuals at elevated obesity risk
- Supporting earlier interventions
- Synthesizing large amounts of health information
- Providing consistent risk assessments

While the models were not intended to replace clinical judgment, they demonstrated potential value as decision support tools in healthcare settings.

### Technologies Used
- Python
- Pandas
- NumPy
- Scikit-Learn
- Matplotlib
- Seaborn
- Jupyter Notebook

###Future Work

Potential future improvements included:
- Longitudinal obesity prediction
- Fairness and bias evaluation across demographic groups
- Model calibration analysis
- SHAP-based explainability
- External validation on independent datasets
- Development of clinician-facing prediction tools
- Deployment as an interactive healthcare application

## Conclusion

These findings emphasized that machine learning models should be evaluated within the context of their intended application rather than relying solely on accuracy metrics. In healthcare settings, the ability to identify at-risk individuals and provide transparent explanations may have been more valuable than maximizing predictive performance alone.
