# Student Performance Prediction Model

## Overview

This project uses a machine learning model to predict student enrollment likelihood and need for support based on various factors, including demographics, academic performance, and extracurricular activities. The model aims to provide insights into which students are most likely to enroll in higher education and which might require additional support to succeed.

## Model Details

**Model Type:** RandomForestClassifier

**Target Variables:**
- Enrollment Likelihood: Binary classification (1: Likely to enroll, 0: Unlikely to enroll)
- Need for Support: Binary classification (1: Needs support, 0: Does not need support)

**Features:**
- Age
- Gender
- Ethnicity
- Parental Education
- Study Time (Weekly)
- Absences
- Tutoring (Yes/No)
- Parental Support (Low/Medium/High)
- Extracurricular Activities (Yes/No)
- Sports (Yes/No)
- Music (Yes/No)
- Volunteering (Yes/No)

## Data Preprocessing

Before training the model, the following preprocessing steps are applied to the student data:

1. **Handling Missing Values:**
   - Missing values in numerical features (Age, StudyTimeWeekly, Absences) are imputed using the mean value of the respective feature using `SimpleImputer`.

2. **Encoding Categorical Features:**
   - Categorical features (Gender, Ethnicity, Parental Education, etc.) are converted into numerical representations using Label Encoding (`LabelEncoder`). This assigns a unique numerical label to each category within a feature.

3. **Feature Scaling:**
   - Numerical features are scaled using Standard Scaling (`StandardScaler`) to ensure that all features have a similar range of values, preventing features with larger values from dominating the model's learning process. Standard Scaling transforms the features to have zero mean and unit variance.

## Prediction Criteria

**Enrollment Likelihood:**
- If a student's predicted GPA is 3.0 or higher, their Enrollment Likelihood is classified as 1 (likely to enroll).
- If their predicted GPA is below 3.0, it is classified as 0 (unlikely to enroll).

**Need for Support:**
- If a student's predicted GPA is below 2.5 OR their predicted Absences are greater than 5, their Need for Support is classified as 1 (needs support).
- Otherwise, it is classified as 0 (does not need support).

## Usage

To use the model for prediction, follow these steps:

1. **Load the model and preprocessing tools:** Use `joblib.load()` to load the trained model (`student_performance_model.pkl`), label encoders (`label_encoders.pkl`), and scaler (`scaler.pkl`).

2. **Provide new student data:** Create a Pandas DataFrame containing the features for the new students you want to make predictions for.

3. **Preprocess the new data:** Apply the same preprocessing steps used during training: impute missing values, encode categorical features using the loaded label encoders, and scale numerical features using the loaded scaler.

4. **Make predictions:** Use the loaded model's `predict()` method to generate predictions for the new data.

5. **Interpret predictions:** The predictions will be an array of two values for each student: the first value represents Enrollment Likelihood (0 or 1), and the second value represents Need for Support (0 or 1).

## Contributing

Contributions are welcome! Feel free to open issues or pull requests for improvements or bug fixes.

## License

This project is licensed under the [MIT License](LICENSE).
