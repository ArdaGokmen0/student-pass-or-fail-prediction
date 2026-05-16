# Student Pass/Fail Prediction

This project uses student performance data to predict whether a student will pass or fail a mathematics course.

The main goal is not only to build a classification model, but also to compare different models, evaluate them against a baseline, tune model parameters, and improve decision-making using threshold tuning.

## Project Objective

The objective of this project is to build an early pass/fail prediction model without relying on previous period grades `G1` and `G2`.

This makes the task harder, but more useful for early student risk detection.

## Dataset

The dataset contains student information from secondary education.

It includes:

- Demographic information
- Social factors
- School-related features
- Study habits
- Family background
- Absences
- Final grade `G3`

The target variable was created from `G3`:

- `Passed = 1` if `G3 >= 10`
- `Passed = 0` if `G3 < 10`

## Methodology

The project followed a step-by-step machine learning workflow:

1. Loaded and inspected the dataset
2. Created a pass/fail target variable
3. Encoded categorical variables
4. Built baseline models
5. Compared multiple machine learning models
6. Tuned model hyperparameters
7. Evaluated performance using multiple metrics
8. Optimized the classification threshold
9. Selected the final model

## Models Tested

The following models were tested:

- Majority class baseline
- Decision Tree
- Random Forest
- Logistic Regression
- Tuned Random Forest
- GridSearch Random Forest
- Extra Trees
- Gradient Boosting

## Final Model

The final selected model was:

- Model: GridSearch Random Forest
- Features: without `G1` and `G2`
- Threshold: `0.52`

The threshold was adjusted from the default `0.50` to `0.52` because it improved balanced accuracy while keeping the same overall accuracy.

## Final Results

Final model performance:

| Metric | Value |
|---|---:|
| Accuracy | 73.75% |
| Balanced Accuracy | 69.29% |
| Correctly identified failing students | 15 / 27 |
| Correctly identified passing students | 44 / 53 |

## Key Findings

Previous grades `G1` and `G2` are very strong predictors of final performance.

However, when `G1` and `G2` are removed, the problem becomes much harder. In that early prediction scenario, model tuning and threshold optimization became important.

The most important features in the early prediction model included:

- Previous failures
- Absences
- Going out frequency
- Age
- Health
- Parent education-related variables

## Why Baseline Matters

A majority-class baseline was used as a reference point.

Since most students passed, a simple model that always predicts "passed" already achieves a relatively high accuracy.

Therefore, the machine learning model was evaluated not only by accuracy, but also by:

- Balanced accuracy
- Confusion matrix
- Failing-student recall
- F1-score

## How to Run

1. Clone this repository:

```bash
git clone https://github.com/ArdaGokmen0/student-pass-fail-prediction.git
test