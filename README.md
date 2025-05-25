# 🧠 Predict Schizophrenia from Brain Anatomy

This project aims to **predict schizophrenia** based on **grey matter (GM) brain anatomy** data. Schizophrenia is associated with a diffuse and complex pattern of brain atrophy. Our objective is to train a model that can **distinguish patients with schizophrenia from healthy controls** using quantitative measurements of grey matter.

---

## 📊 Dataset Overview

- **Training set**: 410 samples  
- **Test set**: 103 samples

### 🧠 Input Data Types

1. **Regions of Interest (ROIs) – `train_rois.csv`, `test_rois.csv`**  
   - 284 features per subject  
   - GM measurements scaled by Total Intracranial Volume (TIV)

2. **Voxel-Based Morphometry (VBM) 3D Maps – `train_vbm.npz`, `test_vbm.npz`**  
   - 3D brain images in MNI space: shape `(121, 145, 121)`  
   - Flattened using a brain mask → ~331,695 voxel features per participant

> By default, `problem.get_[train|test]_data()` returns **concatenated features**:  
> - ROIs (first 284 columns): `X[:, :284]`  
> - Voxel features (remaining columns): `X[:, 284:]`

---

## 🎯 Target Variable

The clinical target (schizophrenia vs. healthy control) can be found in the `train_participants.csv` and `test_participants.csv` files.  
> For regression tasks (e.g. predicting age), select the `age` column instead.

---

## 📈 Evaluation Metrics

The main evaluation metrics are:
- **ROC-AUC**: Area under the Receiver Operating Characteristic curve
- **RMSE**: Root Mean Squared Error (in regression cases)

These are computed using `sklearn.metrics`.

---

## 🔗 Useful Links

- [RAMP Studio](https://ramp.studio)
- [RAMP Workflow documentation](https://paris-saclay-cds.github.io/ramp-docs/)
- [RAMP Workflow GitHub](https://github.com/paris-saclay-cds/ramp-workflow)
- [RAMP Kits repository](https://github.com/ramp-kits)

---

## ⚙️ Installation Instructions

Clone the repository:
```bash
git clone https://github.com/salmabens/predict-schizophrenia-from-gray-matter.git
cd predict-schizophrenia-from-gray-matter