# Predicting Patient Dropout from Long-Term Health Treatment Programs

## Overview

This project aims to predict patient dropout from long-term health treatment programs using logistic regression and various data analysis techniques.  The goal is to identify key factors contributing to patient dropout, enabling healthcare providers to improve patient retention and treatment effectiveness. This project fulfills the requirements for CS 471 Machine Learning course in Fall 2024 at the National University of Sciences and Technology.

## Table of Contents

1.  [Overview](#overview)
2.  [Table of Contents](#table-of-contents)
3.  [Setup](#setup)
4.  [Data](#data)
    *   [Original Dataset](#original-dataset)
    *   [Updated Dataset](#updated-dataset)
5.  [Data Exploration and Preprocessing](#data-exploration-and-preprocessing)
6.  [Feature Engineering](#feature-engineering)
7.  [Multicollinearity Handling](#multicollinearity-handling)
8.  [Model Building](#model-building)
9.  [Model Evaluation](#model-evaluation)
10. [Results](#results)
11. [License](#license)

## Setup

1.  **Clone the repository:**

    ```bash
    git clone [repository URL]
    cd [repository name]
    ```

2.  **Create a virtual environment (recommended):**

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Linux/macOS
    venv\Scripts\activate  # On Windows
    ```

3.  **Install the required packages:**

    ```bash
    pip install pandas scikit-learn matplotlib seaborn
    # Add any other libraries used
    ```

4.  **Jupyter Notebook:**
    The main analysis is performed in `code.ipynb`. Ensure Jupyter is installed:
    ```bash
    pip install notebook
    ```

## Data

### Original Dataset

*   The original dataset contains anonymized information about patients enrolled in a long-term health treatment program.
*   It includes features related to patient activities, goals, progress reviews, and online interactions with the healthcare system.
*   The dataset is used to build a logistic regression model for predicting patient dropout.
*   The original data is not included in this repository due to privacy restrictions.

<img width="1382" height="332" alt="image" src="https://github.com/user-attachments/assets/5c30f937-8d35-4cc9-be1e-6888045464f3" />


### Updated Dataset

*   `updated_data.csv`: This file contains the cleaned, processed, and transformed dataset used for model training. It includes the features engineered and preprocessed as part of this project.
*   The data has been prepared to address missing values, scale features, encode categorical variables, and handle outliers.

<img width="1382" height="312" alt="image" src="https://github.com/user-attachments/assets/3573f5cc-d917-4596-919f-3b0d00bea959" />


## Data Exploration and Preprocessing

The data exploration and preprocessing steps include:

*   **Handling Missing Data:** Identified and addressed missing values by removing rows with excessive gaps and imputing remaining values using the median.  
*   **Feature Scaling:** Applied Min–Max scaling to normalize numeric features, ensuring they are on the same scale for logistic regression.  
*   **Encoding Categorical Variables:** Converted categorical variables into numerical representations using one-hot encoding.  
*   **Outlier Detection:** Detected and capped outliers using methods such as histograms, boxplots, and the Interquartile Range (IQR).  

  <img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/b48f948c-920a-41ba-a3fb-4dab271ae900" />

  <img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/4413fb1e-2643-4ff8-a797-502b777f1bcc" />


## Feature Engineering

Feature engineering involved transforming raw data into meaningful features to improve model performance. Key steps included:

*   **Ratio Features:** Created new ratios such as *Attendance per Goal* (sessions attended per goal set) and *Resources per Session* (educational resources viewed per session) to capture patient engagement more effectively.  
*   **Interaction Features:** Added multiplicative terms like *Session into Goal* to model relationships between treatment sessions and goals.  
*   **Polynomial Features:** Applied second-degree polynomial feature expansion to capture non-linear relationships between variables.  
*   **Dimensionality Reduction:** Dropped redundant columns (*Number of Treatment Sessions Attended*, *Number of Treatment Goals Set*, *Number of Educational Resources Viewed*) after creating derived features.  


## Multicollinearity Handling

Multicollinearity was addressed through the following steps:

*   **Correlation Analysis:** Examined pairwise feature correlations using a heatmap to detect highly correlated variables.  
*   **Variance Inflation Factor (VIF):** Calculated VIF scores to quantify multicollinearity. Features with infinite or excessively high VIF values were flagged.  
*   **Feature Removal:** Dropped problematic features (e.g., `Initial Consultation Attended_No`) with high VIF to improve model stability and interpretability.  
*   **Re-Evaluation:** Recomputed correlation matrices and VIF scores after feature removal to ensure multicollinearity was adequately resolved.  

  <img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/b57499c3-ee0f-4692-a77c-d4325ad33edf" />
  
  <img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/987a07c6-4cef-4d87-b995-7fa6d0a8b6e6" />


## Model Building

*   Implemented a **Logistic Regression** model to predict patient dropout.  
*   Trained the model on the dataset and analyzed coefficients to identify significant factors influencing dropout.  
*   Applied **Recursive Feature Elimination (RFE)** to select the most relevant predictors.  
*   Performed a **Train-Test Split** to assess the model’s ability to generalize to unseen data.

<img width="400" height="50" alt="image" src="https://github.com/user-attachments/assets/d418e9c9-6e35-4424-a1de-a1750e84d672" />


## Model Evaluation

*   Assessed model performance on the test set using **Accuracy, Precision, Recall, F1-Score, ROC-AUC**, and **Log Loss**.  
*   Visualized the **Confusion Matrix** with a heatmap to analyze prediction errors.  
*   Used **K-Fold Cross Validation** for a more reliable estimate of model performance.

<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/4f7fd1c5-bbdf-4220-ae8b-142f2362d487" />


## Results

* Log Loss: 0.0594
* Accuracy: 0.9844
* Precision: 1.0000
* Recall: 0.9816
* F1 Score: 0.9907
* ROC AUC: 0.9942
  


## License

[Choose a license, e.g., MIT License](https://opensource.org/licenses/MIT)
