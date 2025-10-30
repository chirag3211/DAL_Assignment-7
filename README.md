# DA5401: Assignment 7 — Landsat Multi-Class Classification

## 👤 Student Details
* **Name:** Chirag  
* **Roll Number:** DA25M008  

---

## 📌 Overview
This project applies and compares **supervised machine learning algorithms** on the **Landsat Satellite dataset** for multi-class land-cover classification.  
We evaluate models using both **threshold-dependent** (F1, Accuracy) and **threshold-independent** metrics (ROC-AUC, Precision-Recall AUC).

Additionally, **“Brownie Points” experiments** explore intentionally flawed models to test metric behavior and interpretability.

---

## ⚙️ Methodology

1. **Dataset:** `sat.trn`, `sat.tst` — pre-split Landsat spectral features (36 bands)  
2. **Target:** Land-cover class (6 categories)  
3. **Preprocessing:**  
   - Label encoding for classes  
   - StandardScaler normalization  
4. **Models Evaluated:**
   - Logistic Regression  
   - SVC (RBF kernel)  
   - KNN  
   - Decision Tree  
   - Random Forest  
   - GaussianNB  
   - XGBClassifier  
   - Dummy (stratified baseline)  
   - Brownie models (Inverted Logistic, Shuffled Logistic)  
5. **Metrics:**  
   - Accuracy, Weighted F1  
   - Macro / Weighted / Micro ROC-AUC  
   - Macro / Weighted / Micro Average Precision (PRC)  

---

## 📊 Results Summary

| Rank | Model | Accuracy | Weighted F1 | Macro ROC-AUC | Macro AP |
| :---: | :---- | :-------: | :----------: | :------------: | :-------: |
| 🥇 1 | **Random Forest** | **0.9115** | **0.9094** | **0.9901** | **0.9517** |
| 🥈 2 | **XGBClassifier** | 0.9050 | 0.9030 | 0.9900 | 0.9509 |
| 3 | **KNN** | 0.9045 | 0.9037 | 0.9786 | 0.9217 |
| 4 | **SVC** | 0.8955 | 0.8925 | 0.9850 | 0.9177 |
| 5 | **Decision Tree** | 0.8505 | 0.8509 | 0.9002 | 0.7366 |
| 6 | **Logistic Regression** | 0.8210 | 0.7935 | 0.9540 | 0.8116 |
| 7 | **Gaussian NB** | 0.7965 | 0.8036 | 0.9551 | 0.8105 |
| 8 | **Dummy (Baseline)** | 0.2305 | 0.0864 | 0.5000 | 0.1667 |

**Brownie Models:**

| Model | Accuracy | Weighted F1 | Macro ROC-AUC | Macro AP |
| :---- | :-------: | :----------: | :------------: | :-------: |
| Inverted Logistic | 0.0005 | 0.0002 | 0.0460 | 0.0909 |
| Shuffled Logistic | 0.1000 | 0.0820 | 0.4113 | 0.1435 |

---

## 🔍 Insights

* **Random Forest** achieved the best overall performance across all metrics.  
* **XGBClassifier** closely followed, showing consistent results across AUC and AP.  
* **SVC** and **KNN** delivered strong, balanced metrics, confirming robustness across linear/non-linear models.  
* **Brownie models** validated the interpretation of ROC and PRC metrics — intentionally degraded to show metric boundaries.  

---

## 🧠 Key Learnings

* Threshold-independent metrics (ROC-AUC, PRC-AUC) reveal more about ranking quality than accuracy alone.  
* PRC analysis is crucial for class imbalance in multi-class datasets.  
* “Brownie Points” models are a powerful pedagogical tool for testing metric understanding.  

---

## 🧱 Reproducibility

* **Python:** 3.13  
* **Libraries:** `numpy`, `pandas`, `scikit-learn`, `plotly`, `matplotlib`, `xgboost`  
* **Random Seed:** 42  
* **Run Order:** Sequential — all outputs deterministic  
* **Outputs:** Interactive ROC/PRC (Plotly) and comparison tables  

---

## ✅ Conclusion
This assignment demonstrates a complete end-to-end workflow for **multi-class evaluation and visualization**, balancing interpretability with experimental rigor.  
**Random Forest** emerged as the top performer, but **XGBoost** offered nearly identical results with better scalability.

> **Final takeaway:** Evaluate beyond accuracy — macro-averaged ROC-AUC and PRC metrics best capture multi-class model quality.
