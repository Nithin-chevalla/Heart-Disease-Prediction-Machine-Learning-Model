# ❤️ Heart Disease Prediction App

A **Streamlit** web application that predicts a patient's risk of heart disease using a **K-Nearest Neighbors (KNN)** machine learning model trained on clinical health data.

---

## 📌 Overview

This app takes basic patient health details (age, blood pressure, cholesterol, ECG results, etc.) as input and predicts whether the patient is at **High Risk** or **Low Risk** of heart disease. It is built for quick, interactive risk screening and demonstrates a complete end-to-end ML deployment pipeline — from data preprocessing to a live prediction interface.

---

## 🚀 Demo

```
streamlit run app.py
```

The app opens in your browser at `http://localhost:8501`.

---

## 🧠 How It Works

1. The user enters patient details through Streamlit widgets (sliders and dropdowns).
2. Categorical inputs (Sex, Chest Pain Type, Resting ECG, Exercise Angina, ST Slope) are converted into **one-hot encoded** columns matching the training data format.
3. Missing dummy columns are filled with `0` and the input is reordered to match the exact column order used during training (`columns.pkl`).
4. The input is scaled using a pre-fitted `StandardScaler` (`scaler.pkl`).
5. The scaled input is passed to a trained `KNeighborsClassifier` (`KNN_heart.pkl`), which outputs a prediction:
   - **1** → ⚠️ High Risk of Heart Disease
   - **0** → ✅ Low Risk of Heart Disease

---

## 🗂️ Project Structure

```
├── app.py              # Streamlit application (UI + prediction logic)
├── KNN_heart.pkl        # Trained KNN classification model
├── scaler.pkl            # Fitted StandardScaler for feature scaling
├── columns.pkl           # Ordered list of feature columns used during training
└── README.md              # Project documentation
```

---

## 📋 Input Features

| Feature | Description | Type |
|---|---|---|
| Age | Patient's age | 18–100 |
| Sex | M / F | Categorical |
| Chest Pain Type | ATA, NAP, TA, ASY | Categorical |
| Resting Blood Pressure | mm Hg | 80–200 |
| Cholesterol | mg/dL | 100–600 |
| Fasting Blood Sugar > 120 mg/dL | 0 = No, 1 = Yes | Binary |
| Resting ECG | Normal, ST, LVH | Categorical |
| Max Heart Rate | bpm | 60–220 |
| Exercise-Induced Angina | Y / N | Categorical |
| Oldpeak (ST Depression) | 0.0–6.0 | Numeric |
| ST Slope | Up, Flat, Down | Categorical |

---

## ⚙️ Tech Stack

- **Python 3**
- **Streamlit** – web app framework
- **scikit-learn** – KNN model & StandardScaler
- **pandas** – data handling
- **joblib** – model serialization

---

## 🛠️ Installation & Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/heart-disease-prediction.git
   cd heart-disease-prediction
   ```

2. **Create a virtual environment (optional but recommended)**
   ```bash
   python -m venv venv
   source venv/bin/activate   # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install streamlit pandas scikit-learn joblib
   ```

4. **Run the app**
   ```bash
   streamlit run app.py
   ```

---

## 🤖 Model Details

- **Algorithm:** K-Nearest Neighbors Classifier (`n_neighbors=5`, Minkowski distance)
- **Preprocessing:** One-hot encoding for categorical variables + StandardScaler for numeric scaling
- **Feature count:** 15 engineered features (after one-hot encoding)
- **Artifacts:**
  - `KNN_heart.pkl` — trained model
  - `scaler.pkl` — fitted `StandardScaler`
  - `columns.pkl` — final ordered feature column list used at inference time

> ⚠️ Note: `scikit-learn` version used to train these artifacts may differ from your local install. If you see an `InconsistentVersionWarning`, consider re-training or matching the `scikit-learn` version.

---

## ⚠️ Disclaimer

This tool is built for **educational and demonstration purposes only**. It is **not a certified medical diagnostic tool** and should not be used as a substitute for professional medical advice, diagnosis, or treatment. Always consult a qualified healthcare provider for medical concerns.

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

## 🙋 Author

Built by **Nithin Chevalla**
