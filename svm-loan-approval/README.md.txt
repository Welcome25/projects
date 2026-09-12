Loan Approval Prediction using SVM

A machine learning classification project that uses a Support Vector Machine (SVM) to predict whether a loan application will be approved based on applicant demographic, financial, and credit information.

Project Overview

This project demonstrates an end-to-end machine learning classification workflow.

The project includes:

Loading the loan approval dataset
Data exploration
Handling missing values
Removing the unnecessary Loan_ID column
Encoding categorical variables
Scaling numerical variables
Train-test splitting
SVM classification
Model evaluation
Confusion matrix visualization
Example loan approval prediction
Dataset

The dataset contains information about loan applicants and whether their loan was approved.

Dataset Columns
Column	Description
Loan_ID	Unique loan application identifier
Gender	Applicant gender
Married	Whether the applicant is married
Dependents	Number of dependents
Education	Applicant education level
Self_Employed	Whether the applicant is self-employed
ApplicantIncome	Applicant income
CoapplicantIncome	Co-applicant income
LoanAmount	Requested loan amount
Loan_Amount_Term	Loan repayment term
Credit_History	Credit history indicator
Property_Area	Property location
Loan_Status	Loan approval status
Target Variable

The target variable is:

Loan_Status


The values are converted to:

Y / Approved → 1
N / Rejected → 0


Therefore:

1 → Loan Approved
0 → Loan Not Approved

Machine Learning Algorithm
Support Vector Machine

Support Vector Machine is a supervised machine learning algorithm used for classification and regression.

For classification, SVM attempts to find a decision boundary that separates different classes while maximizing the margin between them.

This project uses an RBF kernel:

kernel = "rbf"


The RBF kernel allows the model to learn nonlinear relationships between applicant features and loan approval.

Why SVM?

SVM can work well when:

The dataset contains multiple features
Classes can be separated using complex boundaries
Features are properly scaled
The dataset is relatively small or medium-sized

Because SVM is sensitive to feature scales, numerical features are standardized before training.

Preprocessing
1. Remove Loan ID

Loan_ID is an identifier rather than a useful predictive feature, so it is removed.

2. Missing Values

Numerical missing values are replaced using the median.

Categorical missing values are replaced using the most frequent category.

3. Categorical Encoding

Categorical variables are converted into numerical values using One-Hot Encoding.

Categorical features include:

Gender
Married
Dependents
Education
Self_Employed
Property_Area

4. Feature Scaling

Numerical features are standardized using StandardScaler.

Numerical features include:

ApplicantIncome
CoapplicantIncome
LoanAmount
Loan_Amount_Term
Credit_History


Scaling is especially important for SVM because the algorithm uses distances and margins when constructing the decision boundary.

Machine Learning Workflow
Loan Dataset
     ↓
Data Exploration
     ↓
Remove Loan_ID
     ↓
Handle Missing Values
     ↓
Encode Categorical Features
     ↓
Scale Numerical Features
     ↓
Train/Test Split
     ↓
SVM Classifier
     ↓
Predictions
     ↓
Model Evaluation

Model Configuration

The default SVM configuration is:

SVC(
    kernel="rbf",
    C=1.0,
    gamma="scale",
    probability=True
)

Kernel
RBF


The Radial Basis Function kernel can model nonlinear decision boundaries.

C

C controls the trade-off between a wider margin and classification errors.

Gamma

gamma controls how strongly individual training examples influence the decision boundary.

Train-Test Split

The dataset is divided into:

80% → Training
20% → Testing


A random state of 42 is used for reproducibility.

Stratification is also used to maintain a similar class distribution in the training and testing sets.

Evaluation Metrics

The model is evaluated using:

Accuracy

Percentage of correctly classified loan applications.

Precision

Measures how many applications predicted as a particular class actually belong to that class.

Recall

Measures how many actual applications belonging to a class were correctly identified.

F1 Score

The harmonic mean of precision and recall.

Confusion Matrix
                       Predicted
                   Not Approved  Approved

Actual
Not Approved          TN           FP

Approved              FN           TP

Results

Run the project to obtain the exact performance on your dataset.

The program displays:

Accuracy
Precision
Recall
F1-score
Confusion Matrix
Approval Probability

Example Prediction

The project includes an example applicant:

Gender: Male
Married: Yes
Dependents: 0
Education: Graduate
Self_Employed: No
ApplicantIncome: 5000
CoapplicantIncome: 1500
LoanAmount: 150
Loan_Amount_Term: 360
Credit_History: 1
Property_Area: Urban


The trained SVM model produces:

Loan Approved


or

Loan Not Approved


along with an estimated approval probability.

Installation

Clone the repository:

git clone https://github.com/YOUR_USERNAME/svm-loan-approval.git


Move into the project:

cd svm-loan-approval


Create a virtual environment:

python -m venv venv

Windows
venv\Scripts\activate

macOS/Linux
source venv/bin/activate


Install dependencies:

pip install -r requirements.txt

Dataset Setup

Place your CSV file at:

data/loan_approval.csv


The CSV should contain:

Loan_ID
Gender
Married
Dependents
Education
Self_Employed
ApplicantIncome
CoapplicantIncome
LoanAmount
Loan_Amount_Term
Credit_History
Property_Area
Loan_Status


If your target column already contains Approved and Rejected instead of Y and N, the included code handles both formats.

Run the Project

From the project root:

python src/train.py

Output

The project generates:

results/
├── confusion_matrix.png
└── predictions.csv

Example Repository Structure
svm-loan-approval/
│
├── data/
│   └── loan_approval.csv
│
├── notebooks/
│   └── svm_loan_approval.ipynb
│
├── src/
│   └── train.py
│
├── results/
│   ├── confusion_matrix.png
│   └── predictions.csv
│
├── requirements.txt
├── README.md
└── .gitignore

Future Improvements

Possible improvements include:

Hyperparameter tuning using GridSearchCV
Cross-validation
ROC-AUC analysis
Precision-recall analysis
Class imbalance handling
Comparison with Logistic Regression
Comparison with KNN
Comparison with Random Forest
Comparison with XGBoost
Feature importance analysis
Streamlit deployment
Interactive loan prediction application
Important Consideration

Loan approval is a high-impact decision. A model like this should be treated as an educational machine-learning example, not as a standalone system for making real lending decisions. Real-world lending models require careful validation, fairness analysis, regulatory compliance, and human oversight.

Technologies Used
Python
Pandas
NumPy
Scikit-learn
Matplotlib
Seaborn
Jupyter Notebook
License

This project is intended for educational and portfolio purposes.