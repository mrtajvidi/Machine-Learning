# Practical Application III: Comparing Classifiers

## 📋 Project Overview

This project compares the performance of four machine learning classifiers (K-Nearest Neighbors, Logistic Regression, Decision Trees, and Support Vector Machines) on a Portuguese bank marketing dataset to predict term deposit subscriptions.

## 🎯 Business Objective

**Goal**: Predict whether a bank client will subscribe to a term deposit based on demographic information and previous campaign data.

**Business Impact**: Help the bank optimize marketing campaigns by identifying customers most likely to subscribe, improving resource allocation and conversion rates.

## 📊 Dataset Information

- **Source**: UCI Machine Learning Repository - Bank Marketing Dataset
- **Size**: 41,188 samples with 21 features
- **Target**: Binary classification (yes/no term deposit subscription)
- **Challenge**: Highly imbalanced dataset (88.7% "no", 11.3% "yes")

## 🔍 Key Findings

### Model Performance Summary

| Model | Accuracy | F1-Score | Precision (Yes) | Recall (Yes) | Business Value |
|-------|----------|----------|-----------------|--------------|----------------|
| **Random Forest** | 64.7% | **0.261** | 17% | **55%** | **Best Overall** |
| **Tuned Decision Tree** | 67.4% | 0.260 | 17% | 51% | Good Alternative |
| **Balanced Logistic Regression** | 22.6% | 0.218 | 12% | **96%** | Highest Recall |
| **Default Models** | ~88% | 0.000 | 0% | 0% | Useless for Business |

### Key Insights

1. **Class Imbalance Challenge**: Default models achieved high accuracy (88.7%) but failed to identify any positive cases, making them useless for business purposes.

2. **Feature Importance**: Age, default status, job type (student, retired), and education level are the most predictive features.

3. **Model Trade-offs**:
   - **High Recall**: Balanced Logistic Regression finds 96% of potential customers but with many false positives
   - **Balanced Performance**: Random Forest and Decision Tree offer good precision-recall balance
   - **Training Speed**: KNN fastest (0.006s), SVM slowest (41.7s)

## 🛠️ Methodology

### Data Processing
- **Feature Selection**: Used bank client information only (age, job, marital status, education, default, housing, loan)
- **Encoding**: One-hot encoding for categorical variables (28 features total)
- **Scaling**: StandardScaler for distance-based algorithms (KNN, SVM)
- **Split**: 80/20 train-test split with stratification

### Model Development
1. **Baseline Model**: Dummy classifier (always predict majority class)
2. **Default Models**: Trained 4 classifiers with default parameters
3. **Model Improvement**: 
   - Hyperparameter tuning with GridSearchCV
   - Class balancing techniques
   - Threshold optimization
   - Ensemble methods (Random Forest)

### Evaluation Metrics
- **Primary**: F1-Score (balanced precision and recall for imbalanced data)
- **Secondary**: Precision, Recall, Accuracy, AUC-ROC
- **Business**: Focus on recall (minimize missed opportunities) while maintaining reasonable precision

## 📈 Business Recommendations

### Recommended Model: Random Forest
- **Performance**: 26.1% F1-score, 55% recall, 17% precision
- **Business Benefit**: Identifies ~55% of potential customers with reasonable precision
- **Cost-Effectiveness**: Balances marketing efficiency with customer acquisition

### Implementation Strategy
1. **Production Deployment**: Use Random Forest or Tuned Decision Tree for regular campaigns
2. **Exploration Campaigns**: Use high-recall Balanced Logistic Regression to discover new customer segments
3. **A/B Testing**: Test different probability thresholds based on campaign budget and goals

## 📚 Technical Details

### Libraries Used
- **Data Processing**: pandas, numpy
- **Machine Learning**: scikit-learn
- **Visualization**: matplotlib, seaborn
- **Model Selection**: GridSearchCV, cross-validation

### Models Implemented
- **Logistic Regression** (with class balancing)
- **K-Nearest Neighbors** (hyperparameter tuned)
- **Decision Tree** (pruned and balanced)
- **Support Vector Machine** (default parameters)
- **Random Forest** (ensemble method)

### Evaluation Framework
- Cross-validation with F1-score optimization
- Comprehensive metrics reporting
- Business-focused interpretation
- Visualization of model performance trade-offs

---

**Author**: Reza Tajvidi
**Course**: UC Berkeley AI/ML Professional Certificate - Module 17  
**Date**: November 2025  

For questions or feedback, please refer to the detailed analysis in the [Jupyter notebook](./prompt_III.ipynb).