Computational Toxicology Pipeline (ClinTox)
Overview:

This project implements a safety-critical machine learning pipeline for predicting molecular toxicity using the ClinTox dataset.
Unlike standard classification workflows, this pipeline explicitly prioritizes safety, reliability, and interpretability over raw accuracy.

In toxicology, a highly accurate model can still be dangerous if it fails to detect toxic compounds. This project is designed to address that reality by combining rigorous data curation, explainable AI, failure mode analysis, and applicability domain assessment to determine when a model should and should not be trusted.


Who This Project Is For:
This repository is intended for researchers, ML engineers, and toxicologists interested in safety-critical machine learning for early-stage drug discovery, where false negatives carry severe ethical and financial risk.


Key Features:
Safety-First Modeling-
Prioritizes Recall (sensitivity) to minimize False Negatives (missed toxic molecules), using threshold optimization rather than metric gaming.

Rigorous Data Curation-
Canonicalization, deduplication, and label consistency checks performed using RDKit to ensure data reliability.

Explainable AI (XAI)-
SHAP (SHapley Additive exPlanations) used to identify global toxicity drivers and explain individual correct predictions and safety failures.

Failure-Aware Analysis-
Systematic investigation of False Negatives to understand where and why the model fails.

Applicability Domain & Trust Boundaries-
Defines regions of chemical space where predictions are Trusted, require Caution, or should be Rejected outright.

Metric Justification-
Demonstrates why Accuracy is misleading in toxicology and motivates the use of Precision-Recall metrics.


Pipeline Architecture:
The project is structured into clearly defined, sequential phases:

| Phase | Description                   | Key Output                                                 |
| ----- | ----------------------------- | ---------------------------------------------------------- |
| A     | Dataset Loading & Diagnostics | Raw dataset inspection, missing value analysis             |
| B     | Molecular Cleaning            | Canonical SMILES, removal of invalid & duplicate molecules |
| C     | Label Conflict Detection      | Identification of ambiguous toxicity labels                |
| D     | Class Imbalance Analysis      | Justification for Precision-Recall metrics                 |
| E     | Featurization                 | Morgan fingerprints (ECFP4, 2048 bits)                     |
| F     | Baseline Modeling             | Class-weighted Logistic Regression (safety-aware baseline) |
| G     | Threshold Optimization        | Selection of a Safety-First decision threshold             |
| I     | Model Interpretability (SHAP) | Global feature importance and local explanations           |
| J     | Failure Mode Analysis         | PCA-based failure clustering and signature analysis        |
| K     | Applicability Domain          | Trust, Caution, and Out-of-Domain regions                  |



The pipeline requires the following Python libraries:
Python 3.7+
rdkit
shap
scikit-learn
pandas, numpy
matplotlib, seaborn


Usage
The pipeline is designed to be executed sequentially, with each phase building on the outputs of the previous one.
Upload data
Ensure clintox.csv.gz is present in the working directory.

Run Phases A–E
Dataset diagnostics, cleaning, imbalance analysis, and featurization.

Run Phase F
Train the baseline toxicity model.

Run Phase G
Optimize the decision threshold for safety-critical screening.

Run Phases I–K
Perform explainability, failure analysis, and applicability domain assessment.


Key Results & Insights:
Naïve Accuracy Is Dangerous-
A model predicting “Non-Toxic” for all molecules achieves ~93% accuracy while missing all toxic compounds.

Recall–Precision Trade-off Is Necessary-
Lowering the decision threshold significantly reduces False Negatives at the cost of increased False Positives—an acceptable trade-off in early drug screening.

Trust Boundaries Matter-
Model confidence alone is insufficient. Predictions for molecules outside the training chemical space must be rejected regardless of probability.


Limitations & Future Work:
This study focuses on a single benchmark dataset (ClinTox) and a classical linear model to emphasize interpretability and safety analysis.
Future extensions may include:

External validation on independent toxicity datasets

Structure-based validation via docking or molecular dynamics

Graph Neural Networks with retained explainability constraints


Disclaimer:
This project is for computational research purposes only.
It does not constitute medical advice, regulatory approval, or experimental validation.
All predictions in the Caution or Out-of-Domain regions must be validated using appropriate in-vitro or in-vivo assays.


License:
MIT License
