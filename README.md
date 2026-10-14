# Predicting Aqueous Solubility with RDKit and Scikit-learn

A linear regression model predicting aqueous solubility from RDKit-derived molecular descriptors, trained on the Delaney (ESOL) dataset (J. S. Delaney,  *J. Chem. Inf. Comput. Sci.* 2004, 44, 1000–1005; data via [DeepChem](https://github.com/deepchem/deepchem/blob/master/datasets/delaney-processed.csv)).

## What this does

Six descriptors (molecular weight, LogP, TPSA, H-bond donors/acceptors, rotatable bonds) are calculated with RDKit and used to train a scikit-learn linear regression model against measured aqueous solubility, with an 80:20 train/test split.

## Results

- **R² = 0.74**, **RMSE = 1.11 log units**
- LogP has a negative coefficient (≈ −0.93 log units per LogP unit), consistent with more lipophilic compounds being less soluble. The descriptors weren't standardised, so the coefficients can't be compared directly to rank their importance.
- Prediction error shows only a weak overall correlation with LogP, but binning compounds by LogP shows the most lipophilic 20% had a higher median error than the rest of the set in this train/test split. This could be a limitation of a linear model at the extremes, but it could also reflect the inherent difficulty in measuring accurate solubilities on very poorly soluble compounds.

## Next steps

- **Standardise the descriptors** so the coefficients can be compared directly, to show which descriptors contribute most to the prediction.
- **Compare against Delaney's ESOL model** on the same test set, to see how this model performs relative to the published equation.
- **Use cross-validation** instead of a single train/test split, to check whether the higher error for the most lipophilic compounds holds across different splits.

## Requirements

See requirements.txt
