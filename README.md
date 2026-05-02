# 🔐 AI-Based Malicious URL Detection

## 📌 Overview

This project presents a machine learning-based system for detecting malicious URLs using the **ISCX-URL2016 dataset**. The task is formulated as a **multi-class classification problem**, where URLs are categorized into:

* Benign
* Phishing
* Malware
* Defacement
* Spam

Unlike traditional approaches that rely on raw text, this project uses **pre-engineered numerical features** (≈70–80 features) describing structural and statistical properties of URLs.

---

## 🎯 Objectives

* Build an AI model to detect malicious URLs
* Achieve high classification accuracy
* Minimize False Positive Rate (FPR)
* Analyze feature importance and interpret model behavior

---

## 📊 Dataset

* **Source:** ISCX-URL2016
* **Samples:** ~26,953
* **Features:** 72 numerical features
* **Target:** `URL_Type_obf_Type`

The dataset contains engineered features such as:

* Entropy measures
* URL length
* Token counts
* Structural characteristics

---

## ⚙️ Methodology

### 🔹 1. Data Preprocessing

* Handling missing values (`NaN`)
* Removing infinite values (`inf`)
* Clipping extreme values
* Removing low-variance features (VarianceThreshold)

---

### 🔹 2. Feature Selection

* Based on **XGBoost feature importance**
* Optimal subset: **Top-40 features**

---

### 🔹 3. Models Used

* Logistic Regression (baseline)
* Random Forest
* **XGBoost (best performing model)**

---

### 🔹 4. Training Strategy

* Stratified train/test split
* Hyperparameter tuning using **RandomizedSearchCV**
* Evaluation using:

  * Accuracy
  * Precision
  * Recall
  * F1-score
  * ROC-AUC
  * False Positive Rate (FPR)

---

## 📈 Results

| Metric              | Value      |
| ------------------- | ---------- |
| Accuracy            | **97.18%** |
| F1-score (weighted) | **97.16%** |
| ROC-AUC             | **0.9983** |
| Mean FPR            | **0.75%**  |

### 🔍 Key Observations

* Excellent overall performance
* Very low false positive rate
* Slight weakness in **malware recall (~70%)**

---

## 🧠 Feature Importance

* Entropy-based features are highly influential
* Structural complexity is a strong indicator of malicious URLs
* XGBoost provides better feature discrimination than Random Forest

---

## 📊 Visualizations

The project includes:

* Confusion Matrix
* Feature Importance (XGBoost)
* Model Comparison (RF vs XGBoost)
* Feature Profile Heatmap

---

## 🚀 How to Run

### 1. Install dependencies

```bash
pip install pandas numpy scikit-learn xgboost matplotlib seaborn joblib
```

### 2. Run notebook

```bash
jupyter notebook malicious_url_detection.ipynb
```

---

## ⚠️ Important Notes

* This project uses **tabular data**, not raw URLs
* Deep learning was not used because:

  * The dataset is already feature-engineered
  * Tree-based models perform better on structured data

---

## 🧩 Limitations

* Lower recall for malware detection
* Model cannot directly process raw URLs without feature extraction

---

## 🔮 Future Work

* Improve malware detection using class balancing techniques
* Implement full URL feature extraction pipeline
* Explore deep learning on raw URL text

---

## 👨‍💻 Author

* Mini-project (2025–2026)

---

## 📜 License

This project is for academic purposes.
