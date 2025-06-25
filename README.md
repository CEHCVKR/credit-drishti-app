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
  - **"Black-Box" (LightGBM):** A high-performance gradient boosting model that accurately predicts the probability of default.
  - **"Glass-Box" (WoE Scorecard):** A transparent logistic regression model providing an interpretable scorecard.
- **Explainable AI (XAI)**
- **REST API Backend (Flask)**
- **Interactive Streamlit UI**
- **Production-Ready Codebase**

## 📊 Core Formulas Behind the Scorecard Model

### 1. Weight of Evidence (WoE)

**Formula:**
```
WoE = ln(% of Good Customers / % of Bad Customers)
```

- **Good Customers**: Non-defaulters in the category.
- **Bad Customers**: Defaulters in the category.

**Interpretation:**
- Positive WoE = Lower risk
- Negative WoE = Higher risk

---

### 2. Information Value (IV)

**Formula:**
```
IV = Σ [ (% of Good - % of Bad) × WoE ]
```

**IV Guidelines:**
- < 0.02: Useless
- 0.02–0.1: Weak
- 0.1–0.3: Medium
- > 0.3: Strong

---

### 3. Scorecard Point Calculation

#### Step 1: Scaling Factor & Offset
```
Factor = PDO / ln(2)
Offset = Base Score - (Factor × ln(Base Odds))
```

- PDO: Points to Double Odds (e.g., 40)
- Base Score: e.g., 700
- Base Odds: e.g., 50:1

#### Step 2: Points Per Attribute
```
Points = - (WoE × β) × Factor
```

#### Step 3: Final Score
```
Final Score = Offset + Σ(Points)
```

---

## 🏗️ System Architecture

```
User → Streamlit Frontend → Flask API → AI Models → JSON Response → Streamlit Display
```

## 🛠️ Technology Stack

- **Backend:** Flask, Gunicorn
- **ML:** Scikit-learn, LightGBM, Pandas, NumPy
- **Frontend:** Streamlit
- **Deployment:** Render, Streamlit Community Cloud

## ⚙️ Running the Project Locally

### Prerequisites

- Python 3.8+
- Git

### Setup

```bash
git clone https://github.com/CEHCVKR/credit-drishti-app.git
cd credit-drishti-app
pip install -r requirements.txt
```

### Train Models

```bash
python train_model.py
```

### Start Flask API

```bash
flask --app api_server.py run
```

### Start Streamlit App

```bash
streamlit run app.py
```

## 📁 Project Structure

```
├── artifacts/                # Trained models
├── train_model.py            # Model training script
├── api_server.py             # Flask backend
├── app.py                    # Streamlit frontend
├── requirements.txt
├── credit_risk_dataset.csv
├── Procfile
└── README.md
```

## 🧠 Model Details

- **Scorecard (Logistic Regression)**: AUC ~0.86  
- **LightGBM Model**: AUC ~0.95

## 🔮 Future Improvements

- Risk-based pricing
- Integration with Account Aggregator
- Full MLOps pipeline

## 📜 License

Licensed under the MIT License.
