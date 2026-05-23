Project Summary: Iris Species Classification Model
Objective
The primary goal of this project was to develop and compare machine learning models for classifying Iris flower species (Setosa, Versicolor, Virginica) based on their sepal length, sepal width, petal length, and petal width.

Data Source
The dataset used was IRIS[1].csv, containing 150 samples of Iris flowers with 4 features and one target variable ('species').

Exploratory Data Analysis (EDA)
Initial data exploration confirmed no missing values and appropriate data types. A seaborn.pairplot was generated to visualize the relationships between features and species separability, providing insights into the data distribution.

Data Preprocessing
Feature and Target Separation: Features (X) and target (y) were separated.
Target Encoding: The categorical 'species' target variable was numerically encoded using LabelEncoder.
Data Splitting: The dataset was split into 70% training and 30% testing sets using train_test_split with random_state=42 for reproducibility.
Model Training and Evaluation
Three classification models were trained and evaluated:

k-Nearest Neighbors (k-NN):

Configuration: KNeighborsClassifier(n_neighbors=5)
Performance: Achieved 100% accuracy on the test set, with perfect precision, recall, and F1-scores for all classes.
Logistic Regression:

Configuration: LogisticRegression(max_iter=200, random_state=42)
Performance: Also achieved 100% accuracy on the test set, with perfect precision, recall, and F1-scores.
Decision Tree:

Configuration: DecisionTreeClassifier(random_state=42)
Performance: Also achieved 100% accuracy on the test set, with perfect precision, recall, and F1-scores.
Model Comparison and Selection
All three models performed exceptionally well on this dataset, achieving 100% accuracy. This indicates that the Iris dataset is relatively linearly separable and straightforward for these algorithms to classify.

For the purpose of demonstration, the k-Nearest Neighbors (k-NN) model was selected as the 'best' model.

Saved Model
The chosen k-NN model was saved using joblib for future use. The saved model file is named best_iris_model.joblib.

Inference Example
The notebook includes example code demonstrating how to load the best_iris_model.joblib and use it to predict the species of new Iris flower measurements. The LabelEncoder (le) is also saved implicitly in the notebook's kernel state, allowing the conversion of numerical predictions back to human-readable species names.

Example Usage:

import joblib
import numpy as np

# Load the model
loaded_model = joblib.load('best_iris_model.joblib')

# Example new data (sepal_length, sepal_width, petal_length, petal_width)
new_flower_features = np.array([[5.1, 3.5, 1.4, 0.2]]) # Example Iris-setosa

# Make prediction
prediction_encoded = loaded_model.predict(new_flower_features)

# Decode prediction (assuming 'le' LabelEncoder is available from previous execution)
prediction_species = le.inverse_transform(prediction_encoded)

print(f"Predicted species: {prediction_species[0]}")
