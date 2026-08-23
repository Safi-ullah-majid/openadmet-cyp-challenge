# OpenADMET CYP Inhibition Challenge — Baseline Submission

**Author:** [Your Name]  
**Date:** August 2026  
**Challenge:** OpenADMET CYP Inhibition Blind Challenge

---

## Data
- **Source:** `openadmet/cyp-challenge-train-test` (Hugging Face Datasets)
- **Training set:** 4,905 compounds with sparse direct inhibition pIC50 labels across 4 CYP isoforms
- **Test set:** 750 compounds (blinded)

## Feature Engineering
- **Physicochemical descriptors (13):** MolWt, MolLogP, NumHAcceptors, NumHDonors, NumRotatableBonds, NumAromaticRings, NumHeteroatoms, NumHalogens, TPSA, QED, FractionCsp3, HeavyAtomCount, RingCount
- **Morgan fingerprints:** 2,048-bit, radius=2
- **MACCS keys:** 167-bit

## Modeling
### Direct Inhibition (Regression)
- **Models:** LightGBM, XGBoost, RandomForest
- **Ensemble:** Simple average of all three models
- **Validation:** Structure-aware 80/20 split using MiniBatchKMeans clustering on Morgan fingerprints
- **Preprocessing:** StandardScaler on all features

### Time-Dependent Inhibition (Classification)
- **Approach:** Heuristic baseline — compounds with predicted direct pIC50 &gt; 4.5 labeled as TDI positive
- **Note:** Will be replaced with trained classifiers if TDI arm training data becomes available

## Validation Results (Structure-Aware Split)
| Isoform | ST-RAE | MAE |
|---------|--------|-----|
| CYP3A4  | 0.105  | 0.573 |
| CYP2D6  | 0.133  | 0.597 |
| CYP2C9  | 0.091  | 0.483 |
| CYP1A2  | 0.148  | 0.690 |

## Dependencies
- rdkit, lightgbm, xgboost, scikit-learn, pandas, numpy, datasets

## Code
[Link to your Colab notebook or GitHub repo]
