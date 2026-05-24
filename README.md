# A Data-Driven Comparison of Machine Learning Models for Predicting Employee Attrition Intention

## Author Information
**Name:** Durga Bhavani Visalakshi Joga  
**Programme:** MSc Computer Science 
**Institution:** Transport and Telecommunication Institute (TSI), Riga, Latvia  
**Supervisor:** Dr.Sc.ing., Associate Professor Samuel Moveh  

---

## Thesis Overview
Employee attrition intention is one of the critical issues faced by organisations in modern times. This research aims to predict employee attrition intention using six machine learning models trained on primary survey data collected directly from employees across various industries. SHAP (SHapley Additive Explanations) analysis is applied to identify and explain the key factors influencing employee attrition intention.

Unlike most existing studies that rely on publicly available synthetic HR datasets such as the IBM HR Analytics dataset, this study uses real survey data collected from 378 employees working in various industries. This provides more realistic and practical insights into employee attrition intention.

---

## Research Aim
To predict employee attrition intention using machine learning models and to identify the key factors influencing employees intention to leave the organisation using SHAP analysis.

---

## Research Questions
1. Which machine learning model performs best for predicting employee attrition intention using survey data?
2. What are the most important factors that influence employee attrition intention as identified through SHAP analysis?
3. How does survey data help in better understanding employee attrition intention compared to publicly available datasets?

---

## Research Hypothesis
The performance of machine learning classification models trained on the basis of survey data allows for an effective prediction of employees intentions to leave and the identification of the factors that have an impact on such behaviour with SHAP analysis.

---

## Dataset Description
| Attribute | Value |
|---|---|
| Total Responses | 378 |
| Total Variables | 24 |
| Missing Values | 0 |
| Target: Stay (0) | 199 (52.6%) |
| Target: Leave (1) | 179 (47.4%) |
| Mean Age | 31.97 years |
| Mean Work Experience | 8.26 years |
| Mean Years at Company | 4.05 years |

### Data Collection
- Collected via Google Forms
- Distributed through professional networks and online communities
- Respondents from various industries including Information Technology, Engineering, Sales and Marketing, Research and Development and Human Resource Management

### Variable Categories
| Category | Variables |
|---|---|
| Demographics | Age, Gender, Marital Status |
| Education and Role | Education Level, Education Field, Department, Job Role, Job Level |
| Work Conditions | Overtime, Daily Work Travel, Distance From Home |
| Satisfaction Measures | Work-Life Balance, Environment Satisfaction, Job Involvement, Colleague Relationship Satisfaction, Job Satisfaction |
| Experience and Tenure | Total Work Experience, Years at Company, Years in Current Role, Years Since Last Promotion, Training Programs Last Year |
| Compensation | Monthly Income, Percent Salary Hike |
| Target Variable | Attrition Intention (Stay = 0, Leave = 1) |

---

## Methodology
- **Research Design:** Quantitative positivist approach
- **Data Split:** 80% training (302 samples) / 20% testing (76 samples) with stratified sampling
- **Cross Validation:** 10-fold stratified cross-validation on training set
- **Random Seed:** 42 for reproducibility
- **Class Balancing:** Balanced class weights applied
- **Feature Scaling:** Applied for Logistic Regression and SVM
- **Interpretability:** SHAP TreeExplainer applied to CatBoost model

---

## Machine Learning Models
| Model | Key Hyperparameters |
|---|---|
| Logistic Regression | C=1.0, Balanced class weight, Max iterations=2000 |
| Decision Tree | Max depth=5, Min samples split=10, Min samples leaf=5 |
| Random Forest | 200 trees, Max depth=8, Min samples split=10, Min samples leaf=4, Balanced class weight |
| SVM | RBF kernel, C=10, Gamma=scale, Balanced class weight |
| XGBoost | 300 estimators, Max depth=5, Learning rate=0.1, Subsample=0.8 |
| CatBoost | 300 iterations, Depth=5, Learning rate=0.1, Auto balanced class weight |

---

## Results

### 10-Fold Cross-Validation Results
| Model | Mean CV Accuracy | Std Deviation | Mean CV F1 |
|---|---|---|---|
| CatBoost | 0.6956 | ±0.0709 | 0.6774 |
| Random Forest | 0.6858 | ±0.0785 | 0.6539 |
| XGBoost | 0.6657 | ±0.0536 | 0.6308 |
| Logistic Regression | 0.6525 | ±0.0767 | 0.6150 |
| SVM | 0.6524 | ±0.0774 | 0.6204 |
| Decision Tree | 0.6122 | ±0.0778 | 0.5702 |

### Test Set Results
| Model | Accuracy | Precision | Recall | F1-Score |
|---|---|---|---|---|
| CatBoost | 0.7763 | 0.7714 | 0.7500 | 0.7606 |
| SVM | 0.7632 | 0.7500 | 0.7500 | 0.7500 |
| Random Forest | 0.7500 | 0.7742 | 0.6667 | 0.7164 |
| XGBoost | 0.7105 | 0.7059 | 0.6667 | 0.6857 |
| Logistic Regression | 0.6842 | 0.6765 | 0.6389 | 0.6571 |
| Decision Tree | 0.6316 | 0.6429 | 0.5000 | 0.5625 |

### ROC AUC Results
| Model | AUC Score |
|---|---|
| SVM | 0.81 |
| XGBoost | 0.79 |
| CatBoost | 0.79 |
| Random Forest | 0.78 |
| Logistic Regression | 0.73 |
| Decision Tree | 0.66 |

### CatBoost Confusion Matrix
| | Predicted Stay (0) | Predicted Leave (1) |
|---|---|---|
| Actual Stay (0) | 32 (TN) | 8 (FP) |
| Actual Leave (1) | 9 (FN) | 27 (TP) |

---

## SHAP Analysis
SHAP TreeExplainer was applied to the CatBoost model - the best performing model.

### Top 10 Features by SHAP Importance
| Rank | Feature | SHAP Importance | Direction |
|---|---|---|---|
| 1 | Environment Satisfaction | 0.8638 | Low → Intention to Leave |
| 2 | Job Satisfaction | 0.6588 | Low → Intention to Leave |
| 3 | Age | 0.4241 | Young → Intention to Leave |
| 4 | Job Level | 0.4165 | Low → Intention to Leave |
| 5 | Work Life Balance | 0.3282 | Low → Intention to Leave |
| 6 | Daily Work Travel | 0.2978 | Mixed |
| 7 | Distance From Home | 0.2876 | High → Intention to Leave |
| 8 | Percent Salary Hike | 0.2450 | Low → Intention to Leave |
| 9 | Training Programs Last Year | 0.2386 | Fewer → Intention to Leave |
| 10 | Job Role | 0.2075 | Mixed |

---

## Key Findings
1. CatBoost achieved the best accuracy of 77.63% among the six models
2. Environment Satisfaction was the most influential predictor of attrition intention
3. Younger employees (18-35 years) showed significantly higher attrition intention
4. Low job satisfaction and poor work-life balance strongly predict attrition intention
5. Survey data yields more realistic accuracy compared to synthetic IBM HR datasets
6. SHAP analysis results align with Herzberg's Two-Factor Theory

---

## Repository Contents
```
├── README.md
├── Employee_Attrition_Intention_Survey_Responses.csv
├── Employee_Attrition_Intention_Thesis_Experiment.ipynb
└── Notebooks/
    ├── 01_Data_Cleaning_and_Preprocessing.ipynb
    ├── 02_Exploratory_Data_Analysis.ipynb
    ├── 03_Model_Training_and_Comparison.ipynb
    └── 04_SHAP_Interpretability_Analysis.ipynb
```

---

## Tools and Libraries
| Library | Purpose |
|---|---|
| pandas | Data loading, cleaning and manipulation |
| numpy | Numerical calculations |
| scikit-learn | Model training, evaluation, preprocessing, cross-validation |
| XGBoost | XGBoost model training |
| CatBoost | CatBoost model training |
| matplotlib | Data visualisation and chart generation |
| seaborn | Statistical visualisation and EDA plots |
| shap | SHAP based model interpretability (TreeExplainer) |

---

## How to Run
1. Clone this repository
2. Upload the CSV dataset file to Google Colab
3. Open the notebook in Google Colab
4. Run all cells in order

---
