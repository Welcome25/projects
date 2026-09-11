CNN Image Classification using CIFAR-10

A deep learning project that uses a Convolutional Neural Network (CNN) to classify images from the CIFAR-10 dataset into 10 different categories.

Project Overview

This project demonstrates an end-to-end image classification pipeline using TensorFlow and Keras.

The workflow includes:

Loading the CIFAR-10 dataset
Image normalization
Data augmentation
CNN architecture design
Batch normalization
Dropout regularization
Model training
Early stopping
Learning-rate reduction
Model checkpointing
Evaluation on the test dataset
Training/validation visualization
Sample predictions
Dataset

CIFAR-10 contains 60,000 color images of size 32 × 32 × 3.

The dataset contains:

50,000 training images
10,000 test images
10 classes
Classes
Class	Description
0	Airplane
1	Automobile
2	Bird
3	Cat
4	Deer
5	Dog
6	Frog
7	Horse
8	Ship
9	Truck
CNN Architecture

The model uses multiple convolutional blocks.

Input Image
    ↓
Data Augmentation
    ↓
Conv2D (32)
    ↓
Batch Normalization
    ↓
Conv2D (32)
    ↓
Max Pooling
    ↓
Dropout
    ↓
Conv2D (64)
    ↓
Batch Normalization
    ↓
Conv2D (64)
    ↓
Max Pooling
    ↓
Dropout
    ↓
Conv2D (128)
    ↓
Batch Normalization
    ↓
Conv2D (128)
    ↓
Max Pooling
    ↓
Dropout
    ↓
Flatten
    ↓
Dense (128)
    ↓
Dropout
    ↓
Dense (10)
    ↓
Softmax

Why CNN?

Convolutional Neural Networks are particularly effective for image classification because convolutional layers can learn spatial patterns such as:

Edges
Textures
Shapes
Object parts
Higher-level visual features

The deeper layers combine these features to recognize complete objects.

Data Preprocessing

Pixel values originally range from 0 to 255.

They are normalized to the range:

0 → 0.0
255 → 1.0


This helps neural-network training converge more effectively.

Data Augmentation

The project applies random transformations during training:

Horizontal flipping
Small rotations
Random zooming

Data augmentation helps the model generalize better to images it has not seen during training.

Regularization

The model uses:

Dropout

Dropout randomly disables a fraction of neurons during training to reduce overfitting.

Batch Normalization

Batch normalization helps stabilize and accelerate training.

Data Augmentation

Augmentation exposes the model to slightly different versions of training images.

Training

The model uses:

Optimizer: Adam
Loss: Categorical Crossentropy
Metric: Accuracy
Batch size: 64
Maximum epochs: 20

The training process also uses:

Early stopping
ReduceLROnPlateau
Model checkpointing
Installation

Clone the repository:

git clone https://github.com/YOUR_USERNAME/cnn-cifar10-classification.git
cd cnn-cifar10-classification


Create a virtual environment:

python -m venv venv

Windows
venv\Scripts\activate

macOS/Linux
source venv/bin/activate


Install dependencies:

pip install -r requirements.txt

Run the Project
python src/train.py


The CIFAR-10 dataset will automatically be downloaded by TensorFlow the first time the program runs.

Output

After training, the project produces:

models/
└── cifar10_cnn.keras

results/
└── training_history.png


The program also displays:

Training accuracy
Validation accuracy
Training loss
Validation loss
Test accuracy
Test loss
Sample predictions
Example Prediction
Sample Predictions:

Image 1: Actual = cat, Predicted = cat
Image 2: Actual = ship, Predicted = ship
Image 3: Actual = airplane, Predicted = airplane
...


Actual results will vary depending on training configuration and hardware.

Model Evaluation

The primary evaluation metric is test accuracy.

For a more complete evaluation, future versions can include:

Confusion matrix
Classification report
Precision
Recall
F1-score
ROC curves
Future Improvements

Possible improvements include:

Transfer learning with ResNet
Transfer learning with MobileNet
Hyperparameter tuning
Learning-rate scheduling
Confusion matrix visualization
TensorBoard integration
Streamlit deployment
Image upload prediction interface
Comparison between CNN architectures
Technologies
Python
TensorFlow
Keras
NumPy
Matplotlib
Scikit-learn
Jupyter Notebook
Disclaimer

This project is intended for educational and portfolio purposes.