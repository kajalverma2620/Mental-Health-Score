# 🧠 Student Mental Health Score Prediction

A machine learning web application that predicts a **Student Mental Health Score (0–10)** based on social media usage, academic activity, lifestyle habits, and perceived stress level.

The project combines a **Scikit-learn machine learning pipeline**, **FastAPI backend**, **Pydantic validation**, and a **HTML/CSS/JavaScript frontend** to provide an interactive prediction experience.

> **Disclaimer:** This project is for educational and informational purposes only. It is not a clinical or medical assessment.

## 🚀 Project Overview

The goal of this project is to understand how different student habits and lifestyle factors can be used to predict a continuous mental health score.

The model uses information such as:

* Age
* Gender
* Country
* Academic Level
* Most-used Social Media Platform
* Primary Purpose of Social Media Use
* Average Daily Screen Time
* Daily Phone Unlocks
* Study Hours
* Physical Activity Hours
* Sleep Hours
* Stress Level

The frontend collects these inputs and sends them to the FastAPI `/predict` endpoint. The trained machine learning pipeline then generates the predicted mental health score.

## 🏗️ Project Architecture

```text
Student Input
     ↓
HTML / CSS / JavaScript Frontend
     ↓
FastAPI Backend
     ↓
Pydantic Input Validation
     ↓
Saved Scikit-learn Pipeline
     ↓
Mental Health Score Prediction
     ↓
Result displayed on Web UI
```

## 🤖 Machine Learning

The project treats mental health score prediction as a **regression problem** because the target is a continuous numerical value.

### Models Used

* Linear Regression — baseline model
* Random Forest Regressor
* Random Forest with hyperparameter tuning using `RandomizedSearchCV`

The project evaluates models using:

* R² Score
* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)

### Data Processing

The ML pipeline includes:

* Data cleaning
* Exploratory Data Analysis
* Handling invalid values
* Feature engineering
* Categorical encoding
* Numerical preprocessing
* Train/test split
* Model training
* Hyperparameter tuning
* Model evaluation

The `Country` feature contains many categories, so the project groups the most frequent countries and places the remaining countries into an `Other` category.

`Stress_Level` is treated as an ordinal feature because its categories have a natural order:

```text
Low → Medium → High → Very High
```

Other categorical features are handled using one-hot encoding.

The complete preprocessing and model pipeline is saved using `joblib`, allowing the API to directly make predictions from raw input data.

## 🛠️ Tech Stack

### Machine Learning

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
* Joblib

### Backend

* FastAPI
* Pydantic
* Uvicorn

### Frontend

* HTML
* CSS
* JavaScript
* Fetch API

### Development

* Jupyter Notebook
* Git
* GitHub

## 📂 Project Structure

```text
Student-Mental-Health-Prediction/
│
├── ML_Project.ipynb
├── main.py
├── Mental_Health_Model.pkl
├── index.html
├── style.css
├── script.js
├── requirements.txt
└── README.md
```

## ⚙️ FastAPI Backend

The backend loads the trained model when the application starts.

The API provides a `/predict` POST endpoint that accepts student information and returns the predicted mental health score.

Example response:

```json
{
  "predicted_mental_health_score": 6.78
}
```

The API uses Pydantic models to validate incoming data, including age, screen time, study hours, sleep hours, physical activity, and stress level.

## 💻 Frontend

The web interface provides input fields for student profile, academic and digital habits, lifestyle, and stress level.

After submitting the form, the predicted score is displayed on a visual score gauge. The interface also provides loading and error states.

## ▶️ How to Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
cd YOUR-REPOSITORY
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Start the FastAPI server

```bash
uvicorn main:app --reload
```

### 5. Open the application

Open the frontend in your browser or serve it through the FastAPI application, depending on your project configuration.

FastAPI documentation is available at:

```text
http://127.0.0.1:8000/docs
```

## 📊 Input Features

| Feature            | Description                                   |
| ------------------ | --------------------------------------------- |
| Age                | Student's age                                 |
| Gender             | Male/Female                                   |
| Country            | Student's country                             |
| Academic Level     | High School, Undergraduate, or Graduate       |
| Most-used Platform | Main social media platform                    |
| Purpose of Use     | Networking, Education, Entertainment, or News |
| Daily Usage        | Average social media usage per day            |
| Daily Unlocks      | Number of phone unlocks per day               |
| Study Hours        | Study time per day                            |
| Physical Activity  | Physical activity per day                     |
| Sleep Hours        | Average sleep per night                       |
| Stress Level       | Low, Medium, High, or Very High               |

## 🔑 Key Features

* Machine learning based regression prediction
* Random Forest model
* Feature engineering
* Data preprocessing pipeline
* Pydantic input validation
* FastAPI REST API
* Interactive web interface
* Real-time prediction through API
* Visual prediction score
* Input validation and error handling

## 📌 Important Note

The predicted score represents a machine learning output based on the provided dataset and should **not** be interpreted as a medical diagnosis or professional mental health assessment.

## 👩‍💻 Author

**Kajal Verma**

B.Tech – Information Technology

Interested in Machine Learning, Python, Web Development, and Data Analytics.
