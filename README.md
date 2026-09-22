# Predicting Aqueous Solubility with RDKit and Scikit-learn

A linear regression model predicting aqueous solubility from RDKit-derived molecular descriptors, trained on the Delaney (ESOL) dataset (J. S. Delaney,  *J. Chem. Inf. Comput. Sci.* 2004, 44, 1000–1005; data via [DeepChem](https://github.com/deepchem/deepchem/blob/master/datasets/delaney-processed.csv)).

## What this does

Six descriptors (molecular weight, LogP, TPSA, H-bond donors/acceptors, rotatable bonds) are calculated with RDKit and used to train a scikit-learn linear regression model against measured aqueous solubility, with an 80:20 train/test split.

## Results

- **R² = 0.74**, **RMSE = 1.11 log units**
- LogP is by far the dominant predictor (coefficient ≈ -0.93), consistent with the expected relationship between lipophilicity and solubility
- Prediction error shows only a weak overall correlation with LogP, but binning compounds by LogP shows the most lipophilic 20% have a distinctly higher median error than the rest of the set. This could be a limitation of a linear model at the extremes, but it could also reflect the inherent difficulty in measuring accurate solubilities on very poorly soluble compounds.

## Requirements

`pandas`, `rdkit`, `scikit-learn`, `seaborn`
