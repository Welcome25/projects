Diabetes Prediction using K-Nearest Neighbors

A machine learning classification project that uses the K-Nearest Neighbors (KNN) algorithm to predict whether a person is likely to have diabetes based on diagnostic measurements.

Project Overview

This project demonstrates a complete machine learning workflow:

Loading the diabetes dataset
Exploring the dataset
Separating features and target
Splitting data into training and testing sets
Standardizing numerical features
Training a KNN classifier
Evaluating model performance
Generating a confusion matrix
Testing different values of K
Selecting an appropriate K value
Making an example prediction
Dataset

The project uses the Pima Indians Diabetes Dataset.

The dataset contains medical diagnostic measurements and a binary target variable called Outcome.

Target
Outcome = 0 → No Diabetes
Outcome = 1 → Diabetes

Features
Feature	Description
Pregnancies	Number of pregnancies
Glucose	Plasma glucose concentration
BloodPressure	Diastolic blood pressure
SkinThickness	Triceps skin fold thickness
Insulin	2-hour serum insulin
BMI	Body mass index
DiabetesPedigreeFunction	Diabetes pedigree function
Age	Age in years
Outcome	Diabetes classification
Machine Learning Algorithm
K-Nearest Neighbors

KNN is a supervised machine learning algorithm that classifies a data point based on the classes of its nearest neighboring observations.

For a new observation:

New Data Point
      ↓
Find K nearest points
      ↓
Check their classes
      ↓
Majority voting
      ↓
Predicted Class


In this project, the default model uses:

K = 5
Distance Metric = Euclidean

Why Feature Scaling?

KNN is distance-based.

If one feature has a much larger numerical range than another feature, it can dominate the distance calculation.

Therefore, StandardScaler is used before training the KNN model.

The features are transformed so that they have approximately:

Mean = 0
Standard Deviation = 1

Project Workflow
Diabetes Dataset
       ↓
Data Exploration
       ↓
Train/Test Split
       ↓
Feature Scaling
       ↓
KNN Classifier
       ↓
Predictions
       ↓
Model Evaluation
       ↓
Confusion Matrix
       ↓
K Value Analysis

Installation

Clone the repository:

git clone https://github.com/YOUR_USERNAME/knn-diabetes-classification.git


Move into the project directory:

cd knn-diabetes-classification


Create a virtual environment:

python -m venv venv

Windows
venv\Scripts\activate

macOS/Linux
source venv/bin/activate


Install the dependencies:

pip install -r requirements.txt

Dataset Setup

Place the dataset inside:

data/diabetes.csv


The CSV file should contain the following columns:

Pregnancies
Glucose
BloodPressure
SkinThickness
Insulin
BMI
DiabetesPedigreeFunction
Age
Outcome

Run the Project

From the project root:

python src/train.py


The program will:

Load the dataset.
Display basic dataset information.
Split the dataset.
Standardize the features.
Train the KNN model.
Calculate accuracy.
Display the classification report.
Generate a confusion matrix.
Test K values from 1 to 20.
Display the best K value.
Make an example prediction.
Evaluation Metrics

The model uses:

Accuracy

The percentage of correctly classified observations.

Precision

Measures how many observations predicted as a class actually belong to that class.

Recall

Measures how many observations belonging to a class were correctly identified.

F1 Score

The harmonic mean of precision and recall.

Confusion Matrix
                    Predicted
                 No Diabetes  Diabetes

Actual
No Diabetes          TN          FP

Diabetes             FN          TP


For a diabetes-screening model, recall for the diabetes class is especially important to examine because false negatives represent diabetic cases that the model fails to identify.

K Value Selection

KNN performance depends strongly on the value of K.

This project tests:

K = 1, 2, 3, ..., 20


The generated graph:

results/k_vs_accuracy.png


shows how test accuracy changes as K changes.

A very small K can make the model sensitive to noise, while a very large K can make the model too generalized.

Results

The script generates:

results/
├── confusion_matrix.png
└── k_vs_accuracy.png


It also prints:

Accuracy
Precision
Recall
F1-score
Confusion Matrix
Best K
Example Prediction
Diabetes Probability


Exact performance can vary depending on the dataset version and preprocessing.

Example Output
KNN MODEL RESULTS

Accuracy: 0.74

Classification Report:

              precision    recall    f1-score

No Diabetes      ...
Diabetes         ...

Best K: 7
Best Accuracy: ...


The numbers above are illustrative. Run the project to obtain the actual results.

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
ROC-AUC analysis
Precision-recall curve
Handling zero values in medical measurements
Feature selection
Comparison with Logistic Regression
Comparison with Random Forest
Comparison with SVM
Streamlit deployment
Model explainability
Disclaimer

This project is intended for educational and machine-learning demonstration purposes only.

It should not be used to diagnose diabetes or make medical decisions.