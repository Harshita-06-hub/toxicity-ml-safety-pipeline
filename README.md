# Toxicity Prediction Pipeline: Safety-Critical ML
**Role:** Lead Developer & Computational Scientist  
**Focus:** Drug Safety, Explainable AI (XAI), & Predictive Modeling

---

### 🎯 The Problem
In drug discovery, **False Negatives are a liability.** A model that achieves high "accuracy" by predicting "Non-Toxic" for all compounds is useless—and dangerous. This project is an enterprise-grade pipeline designed for **Safety-First** toxicity screening, prioritizing clinical reliability and interpretability over naïve metrics.

### 🚀 Key Technical Highlights
* **Safety-First Modeling:** Implemented threshold optimization to minimize False Negatives, ensuring high-risk compounds are flagged for expert review.
* **Explainable AI (XAI):** Integrated **SHAP** to map global toxicity drivers. Every prediction comes with a "why," essential for auditing and regulatory compliance.
* **Applicability Domain (AD) Engineering:** Built "Trust Boundaries" to detect out-of-distribution molecules, automatically rejecting predictions where the model lacks statistical confidence.
* **Robust Data Engineering:** Built a modular pipeline for RDKit-based molecular canonicalization, deduplication, and label-conflict resolution.

### 📈 Pipeline Architecture
| Phase | Focus | Output |
| :--- | :--- | :--- |
| **A-C** | Data Integrity | Canonicalized, conflict-free dataset |
| **D-E** | Feature Engineering | ECFP4 Morgan Fingerprints (2048-bit) |
| **F-G** | Modeling & Thresholding | Safety-weighted Logistic Regression |
| **I-K** | Audit & Reliability | SHAP interpretability & Trust Boundaries |

### 🛠 Tech Stack
* **Core:** Python 3.7+
* **Bio-Informatics:** `RDKit`
* **ML/Data:** `scikit-learn`, `Pandas`, `NumPy`
* **Explainability:** `SHAP`
* **Visualization:** `Matplotlib`, `Seaborn`

### 📊 Performance & Insights
* **Metric Shift:** Moved from "Naïve Accuracy" (misleading) to **Precision-Recall optimization** (actionable).
* **Failure Analysis:** Systematic PCA-based investigation of False Negatives to identify chemical sub-spaces requiring further in-vitro validation.

---

### 📬 Contact
**Harshita Singh**  
[Email](mailto:harshitasinghms@gmail.com) | [LinkedIn](https://linkedin.com/in/harshita-singh-9663a9284) 

*Disclaimer: This project is for computational research. It does not replace clinical or regulatory-grade validation.*

---
