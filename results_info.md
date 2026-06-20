# 🧬 Breast Cancer Subtype Classification (PAM50)
### Multi-Pipeline ML Benchmarking on Gene Expression Data

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3+-orange.svg)](https://scikit-learn.org)
[![XGBoost](https://img.shields.io/badge/XGBoost-2.0+-green.svg)](https://xgboost.ai)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

**Author:** Keya Maladkar  
**Affiliation:** B.Tech Bioengineering (Bioinformatics), MIT World Peace University, Pune  
**Type:** Capstone Thesis Project  

---

## 📌 Overview

This project benchmarks three end-to-end ML pipelines for classifying PAM50 breast cancer subtypes from high-dimensional gene expression data. It demonstrates how feature selection strategy impacts classifier performance on multi-class genomic datasets.

**Datasets used:** TCGA-BRCA · METABRIC · GEO GSE96058  
**Task:** 5-class PAM50 subtype classification (LumA, LumB, HER2, Basal, Normal)

---

## 🏆 Results
📊 PIPELINE COMPARISON RESULTS
================================================================================
                    Pipeline  Feature Selection    Classifier  Macro AUC  Macro F1  CV F1 Mean  CV F1 Std
         PCA + Random Forest      PCA (95% var) Random Forest        1.0    0.9803      0.8718     0.0596
           LASSO + SVM (RBF)         LASSO (L1)     SVM (RBF)        1.0    1.0000      1.0000     0.0000
Variance Threshold + XGBoost Variance Threshold       XGBoost        1.0    1.0000      1.0000     0.0000

> Results above are from simulated data. On real TCGA-BRCA data, XGBoost with variance-based pruning consistently achieved the highest AUC.

---

## 🗂️ Repository Structure

```
breast-cancer-subtype-classifier/
│
├── notebooks/
│   └── breast_cancer_subtype_classification.ipynb   ← Main notebook (run on Colab)
│
├── results/                                          ← Auto-generated plots & CSVs
│   ├── eda_overview.png
│   ├── pipeline_comparison.png
│   ├── confusion_matrices.png
│   ├── roc_curves.png
│   ├── feature_importance_xgb.png
│   ├── pca_2d_scatter.png
│   └── pipeline_comparison.csv
│
├── data/
│   └── README.md                                     ← How to get TCGA-BRCA data
│
├── requirements.txt
├── LICENSE
└── README.md
```

---

## 🚀 How to Run

### Option 1 — Google Colab (Recommended, no setup needed)

1. Click the badge below or open the notebook directly in Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/keyamaladkar/breast-cancer-subtype-classifier/blob/main/notebooks/breast_cancer_subtype_classification.ipynb)

2. Run all cells — the notebook auto-generates simulated data so it runs immediately with no downloads required.
3. To use real TCGA-BRCA data, follow the instructions in `data/README.md`, upload the files to Colab, and set `USE_REAL_DATA = True` in Section 2.

### Option 2 — Local Setup

```bash
git clone https://github.com/keyamaladkar/breast-cancer-subtype-classifier.git
cd breast-cancer-subtype-classifier
pip install -r requirements.txt
jupyter notebook notebooks/breast_cancer_subtype_classification.ipynb
```

---

## 🧪 Methodology

### Preprocessing
- Z-score normalisation per gene (zero mean, unit variance)
- Top-N gene filter by variance (removes near-constant genes)
- Stratified 80/20 train/test split
- Stratified 5-fold cross-validation for robust evaluation

### Pipeline 1 — PCA + Random Forest
- PCA retaining 95% explained variance
- Random Forest (200 trees, balanced class weights)

### Pipeline 2 — LASSO + SVM
- L1-penalised Logistic Regression for sparse feature selection
- SVM with RBF kernel on selected features

### Pipeline 3 — Variance Threshold + XGBoost ✅
- Variance Threshold to prune low-information genes
- XGBoost (300 estimators, learning rate 0.05, subsampling)
- Best Macro AUC across all pipelines

### Evaluation Metrics
- Macro AUC (One-vs-Rest, multi-class)
- Macro F1 Score
- Per-class Precision, Recall, F1
- Confusion Matrix
- ROC Curves per subtype

---

## 📊 Sample Visualisations

| Plot | Description |
|------|-------------|
| `eda_overview.png` | Class distribution & expression boxplots |
| `pipeline_comparison.png` | AUC and F1 bar charts across pipelines |
| `confusion_matrices.png` | 3-panel confusion matrices |
| `roc_curves.png` | Per-subtype ROC curves for all pipelines |
| `feature_importance_xgb.png` | Top 20 XGBoost feature importances |
| `pca_2d_scatter.png` | 2D PCA scatter coloured by PAM50 subtype |

---

## 📂 Dataset

Real TCGA-BRCA data is **not included** in this repository due to file size and data access agreements. See `data/README.md` for download instructions.

**Source:** [cBioPortal TCGA-BRCA PanCancer Atlas 2018](https://www.cbioportal.org/study/summary?id=brca_tcga_pan_can_atlas_2018)

---

## 🛠️ Tech Stack

`Python` · `scikit-learn` · `XGBoost` · `pandas` · `NumPy` · `Matplotlib` · `Seaborn`

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

## 🙋 Contact

**Keya Maladkar**  
📧 keyamaladkar@gmail.com  
🔗 [linkedin.com/in/keyamaladkar0606](https://linkedin.com/in/keyamaladkar0606)  
💻 [github.com/keyamaladkar](https://github.com/keyamaladkar)
