# openadmet-cyp-challenge
Ensemble of LightGBM, XGBoost, and RandomForest regressors trained on RDKit descriptors, 2048-bit Morgan fingerprints, and 167-bit MACCS keys. Structure-aware train/val split via fingerprint clustering. TDI predictions use a direct-inhibition pIC50 > 4.5 heuristic as a baseline fallback.
