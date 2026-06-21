# Stress Detection Using Keystroke Dynamics & Behavioral Telemetry

An end-to-end Machine Learning pipeline designed to detect human stress levels using non-intrusive behavioral data such as keystroke dynamics, mouse movements, and application usage patterns. This system eliminates the need for expensive, intrusive physiological sensors (like EDA/ECG) by leveraging everyday computer interaction datasets.

---

## Project Methodology & Workflow

[Get Raw Dataset]
↓
[Data Preprocessing & Cleansing] (Handled missing values & structured TSV format)
↓
[Feature Engineering] (Extracted key timing, mapping, and behavioral metrics)
↓
[Time Series Analysis]
↓
[Model Training & Comparative Analysis] (Tested Logistic Regression, Random Forest, XGBoost, etc.)
↓
[Feature Importance Evaluation] (Extracted common contributing features)
↓
[Extended Evaluation] (Validated on secondary datasets for lightweight generalization)


---

## 🛠️ Technical Stack & Features

* **Environment:** Google Colab / Python 3.10
* **Core Libraries:** `pandas`, `numpy`, `scikit-learn`, `xgboost`, `matplotlib`, `seaborn`

### Engineered Features Include:
* **Time-Based Metrics:** `Key_Duration_s` (key press-and-release intervals) and `Time_Between_Keystrokes_s`.
* **Key Classification Encodings:** Discrete mappings separating inputs into *Action*, *Modifier*, *Navigation*, and *Typing* domains.
* **Psychological Encodings:** Numerical mappings representing categorical user self-assessments (Fatigue, Energy Level, Pleasantness).

---

## Performance Analysis & Results

The input feature matrices ($X$) were evaluated using a 70/30 train-test split across multiple classification algorithms. Tree-based ensembles significantly outperformed linear models due to their capacity to isolate non-linear behavioral traits.

### Class-Wise Classification Metrics

| Model | Accuracy | Precision (Stressed) | Recall (Stressed) | F1-Score (Stressed) |
| :--- | :---: | :---: | :---: | :---: |
| **XGBoost** | **76.40%** | 0.83.3 | 0.88 | 0.84 |
| **Random Forest** | **74.50%** | 0.73 | 0.99 | 0.84 |
| **Linear Regression** | **67.60%** | 0.68 | 1.00 | 0.81 |
| **Gradient Boosting** | **32.00%** | 0.00 | 0.00 | 0.00 |
| **Logistic Regression**| **29.41%** | 0.20 | 0.01 | 0.03 |

### Key Insights & Feature Contributions
* **Multitasking Correlation:** Background application count (`bg_apps`) emerged as the single most critical feature across all classification thresholds, proving a direct statistical link between high multitasking behavior and increased user stress.
* **Consistency Metrics:** `Energy_Num`, sequence timing dynamics, and daylight contextual anchors demonstrated high, stable correlation weights across all tested architectures.

---

##  Future Scope
* Implement deep learning sequential architectures (LSTMs/GRUs) to analyze chronological keystroke streams.
* Construct an active, real-time localized dashboard for desktop application integration.
* Expand generalization capabilities using larger, multi-modal behavioral cohorts.

---

##  References
1. A. Acién et al., *"Detection of Mental Fatigue in the General Population: Feasibility Study of Keystroke Dynamics as a Real-world Biomarker,"* JMIR Biomedical Engineering, 2022.
2. A. Kolakowska, *"Towards Detecting Programmers’ Stress on the Basis of Keystroke Dynamics,"* Annals of Computer Science and Information Systems, 2016.
3. Chamindu Weerasinghe, *"Stress Detection by Keystroke, App and Mouse Changes,"* Dataset via Kaggle, 2021.
