Breast Cancer Classification using Logistic Regression

A machine learning project that uses Logistic Regression to classify breast cancer tumors as malignant or benign using the Wisconsin Breast Cancer dataset.

Project Overview

This project demonstrates a complete machine learning workflow:

Loading the breast cancer dataset
Exploratory data inspection
Splitting data into training and testing sets
Feature standardization
Training a Logistic Regression classifier
Making predictions
Evaluating model performance
Generating a confusion matrix
Examining model coefficients
Dataset

The project uses the Breast Cancer Wisconsin (Diagnostic) dataset available through scikit-learn.

The dataset contains numerical measurements computed from digitized images of breast mass samples.

The target classes are:

0 — malignant
1 — benign

There are 30 numerical input features describing characteristics such as radius, texture, perimeter, area, smoothness, and concavity.

Machine Learning Algorithm
Logistic Regression

Logistic Regression is a supervised classification algorithm used to predict the probability of an observation belonging to a particular class.

The model produces a probability between 0 and 1 and uses a classification threshold to convert that probability into a class prediction.

Workflow
Dataset
   ↓
Train/Test Split
   ↓
Feature Scaling
   ↓
Logistic Regression
   ↓
Predictions
   ↓
Evaluation
   ├── Accuracy
   ├── Precision
   ├── Recall
   ├── F1-score
   ├── ROC-AUC
   └── Confusion Matrix

Installation

Clone the repository:

git clone https://github.com/YOUR_USERNAME/breast-cancer-logistic-regression.git
cd breast-cancer-logistic-regression


Create a virtual environment:

python -m venv venv


Activate it on Windows:

venv\Scripts\activate


Activate it on macOS/Linux:

source venv/bin/activate


Install dependencies:

pip install -r requirements.txt

Run the Project
python src/train.py


The program will:

Load the dataset.
Split the data into training and testing sets.
Standardize the features.
Train the Logistic Regression model.
Generate predictions.
Display evaluation metrics.
Generate a confusion matrix.
Display the most influential model features.
Evaluation Metrics

The model is evaluated using:

Accuracy

Measures the percentage of correctly classified samples.

Precision

Measures how many predicted positive cases were actually positive.

Recall

Measures how many actual positive cases were correctly identified.

F1 Score

Provides a balance between precision and recall.

ROC-AUC

Measures the model's ability to distinguish between the two classes across different classification thresholds.

Confusion Matrix

The confusion matrix shows:

                 Predicted
                 Negative Positive

Actual Negative    TN       FP

Actual Positive    FN       TP


For medical classification problems, recall is particularly important to examine, because failing to identify a malignant tumor can have serious consequences.

Results

Run the training script to generate the exact metrics for the current implementation.

The output includes:

Accuracy
ROC-AUC
Precision
Recall
F1-score
Confusion Matrix
Top Feature Coefficients

Technologies Used
Python
Pandas
NumPy
Scikit-learn
Matplotlib
Seaborn
Jupyter Notebook
Future Improvements

Possible improvements include:

Hyperparameter tuning
Cross-validation
ROC curve visualization
Precision-recall curve
Comparison with Random Forest
Comparison with Support Vector Machine
Feature selection
Model interpretability
Deployment using Streamlit
Disclaimer

This project is for educational and demonstration purposes only. It is not intended for medical diagnosis or clinical decision-making.