# Credit-Drishti: A Dual-Model Credit Scoring Engine

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) [![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://credit-drishti-app.streamlit.app/)

An intelligent, explainable AI-powered credit scoring application designed to promote financial inclusion by providing accurate and transparent risk assessments.

## 🚀 Live Application

**You can try the live application here: [CREDIT DRISHTI](https://credit-drishti-app.streamlit.app/)**

## 🎯 Project Motivation

Traditional credit scoring models often fail to assess *“thin-file”* applicants—individuals with limited or no formal credit history. This creates a significant barrier to financial inclusion. 

**Credit-Drishti** (from Sanskrit *drishti*, meaning “vision” or “insight”) aims to solve this problem by leveraging a sophisticated dual-model AI system. It combines a high-accuracy predictive model with a fully transparent and interpretable scorecard, providing not just a decision, but a clear explanation behind it.

## ✨ Key Features

- **Dual-Model Architecture:**  
  - **"Black-Box" (LightGBM):** A high-performance gradient boosting model that accurately predicts the probability of default by capturing complex, non-linear patterns in the data.  
  - **"Glass-Box" (WoE Scorecard):** A transparent logistic regression model that provides a simple, point-based scorecard, explaining how each applicant attribute contributes to the final score.  
- **Explainable AI (XAI):** Every prediction is accompanied by a detailed scorecard breakdown, making the decision-making process transparent to underwriters, auditors, and even the applicants themselves.  
- **REST API Backend:** The models are served via a robust Flask API that handles data preprocessing and prediction.  
- **Interactive Web UI:** A user-friendly web interface built with Streamlit allows for easy input of applicant data and clear visualization of the results.  
- **Production-Ready Code:** The application is built with best practices, including cross-validation, input validation, configuration management, and detailed logging.  

## 🏗️ System Architecture

The application operates with a simple, decoupled architecture:  

User -> Streamlit Frontend -> HTTP Request -> Flask Backend API -> AI Models -> JSON Response -> Streamlit Frontend -> Display Results  

## 🛠️ Technology Stack

- **Backend:** Python, Flask, Gunicorn  
- **Machine Learning:** Scikit-learn, LightGBM, Pandas, NumPy  
- **Frontend:** Streamlit  
- **Deployment:**  
  - API Backend hosted on **Render**  
  - Streamlit Frontend hosted on **Streamlit Community Cloud**  

## ⚙️ Running the Project Locally

To run this project on your own machine, follow these steps:

### Prerequisites

- Python 3.8+  
- Git  

### Setup

1. **Clone the Repository:**  
   ```bash
   git clone https://github.com/CEHCVKR/credit-drishti-app.git
   cd credit-drishti-app
   ```
2. **Install Dependencies:**  
   ```bash
   pip install -r requirements.txt
   ```
3. **Train the AI Models:**  
   ```bash
   python train_model.py
   ```
4. **Run the Backend API Server:**  
   ```bash
   flask --app api_server.py run
   ```
5. **Run the Frontend Application:**  
   ```bash
   streamlit run app.py
   ```

### 📂 Project File Structure

```text
├── artifacts/                # Stores trained models and other artifacts  
├── train_model.py            # Script to train both AI models  
├── api_server.py             # Flask backend API for predictions  
├── app.py                    # Streamlit frontend user interface  
├── requirements.txt          # List of Python dependencies  
├── credit_risk_dataset.csv   # The dataset used for training  
├── Procfile                  # Deployment configuration for Render  
└── README.md                 # You are here!  
```

## 🧠 Model Details

The system uses two models that serve different purposes:

- **Scorecard (Logistic Regression):**  
  - **Purpose:** Explainability and transparency.  
  - **Methodology:** Uses Weight of Evidence (WoE) transformation to create a linear, additive scorecard.  
  - **Performance:** Achieves a training AUC of ~0.86.  

- **Risk Model (LightGBM):**  
  - **Purpose:** Predictive accuracy.  
  - **Methodology:** A powerful gradient boosting machine trained with 5-fold cross-validation for robustness.  
  - **Performance:** Achieves a cross-validation AUC of ~0.95, making it highly effective at identifying risk.  

## 🚀 Future Improvements

This project provides a strong foundation. Future work could include:

- **Risk-Based Pricing:** Modify the application to suggest an interest rate based on the predicted risk score.  
- **Alternative Data Integration:** Connect to India’s Account Aggregator framework to incorporate real-time, consent-based financial data (bank statements, etc.).  
- **MLOps Pipeline:** Build a complete MLOps pipeline using tools like MLflow or DVC for experiment tracking, model versioning, and automated retraining.  

## 📜 License

This project is licensed under the MIT License.
