# Leakage-Safe Zero-Day Sybil Detection in UAV Networks

Code for the paper:

> **Source-rate representations and attention autoencoders for leakage-safe zero-day Sybil detection in UAV networks**
> İzel Ece Aksu Demir and Fatma Gümüş, *Electronics* (MDPI), 2026.
> DOI: [to be added on publication]

This repository contains the annotated notebooks that reproduce the identity-leakage analysis, the source-rate representation, and the benign-anchored Mahalanobis and attention-autoencoder detectors, together with the ablation, cross-domain, and robustness studies, all evaluated under a source-disjoint leave-one-attack-class-out (LOACO) protocol.

## Overview

Point-wise novelty detectors fail on identity-based zero-day attacks such as Sybil, because a single Sybil flow lies inside the region occupied by known attacks. We show that the difficulty is **representational, not a matter of model capacity**: a leakage-safe representation of per-source behavioral rates, scored against a benign anchor, recovers unseen-source Sybil where per-flow detectors do not. The same representation supports a hyperparameter-free Mahalanobis detector, a one-class SVM, and an attention autoencoder.

## Repository structure

```
uavsybildetection/
├── README.md
├── requirements.txt
├── LICENSE
└── notebooks/
    ├── 0_identity_leakage.ipynb        # Section 2   — identity-leakage and collection-artifact analysis
    ├── 1_baselines_controls.ipynb      # Sections 3-4 — source-rate representation, benign-anchored detectors, controls
    ├── 2_attention_autoencoder.ipynb   # Section 4   — attention autoencoder (per-flow vs. source-rate)
    ├── 3_feature_ablation.ipynb        # Section 5.1 — leave-one-feature-out, reciprocal, permutation importance
    ├── 4_model_ablation.ipynb          # Section 5.2 — attention vs. plain autoencoder, latent sweep
    ├── 5_lightweight_baselines.ipynb   # Section 5.3 — Isolation Forest and one-class SVM
    ├── 6_veremi_crossdomain.ipynb      # Section 5.4 — cross-domain generalization on VeReMi Extension
    └── 7_complexity_robustness.ipynb   # Section 5.5 — training/inference cost, noise and imbalance robustness
```

## Requirements

```
Python 3.13
torch==2.11.0
scikit-learn==1.6.1
numpy==2.1.3
pandas==2.2.3
```

Install with:

```bash
pip install -r requirements.txt
```

The experiments run on CPU; no GPU is required. The complexity measurements in the paper (Section 5.5) were made on a single CPU core.

## Datasets

The datasets are not redistributed here. Download them from their original sources and place them in a `data/` directory (each notebook reads from `/data/`):

| Dataset | Role | Source | Expected file |
|---------|------|--------|---------------|
| UAVIDS-2025 | Primary | Authors of the dataset paper (IEEE CNS 2025); IEEE DataPort DOI 10.21227/j5p4-zt27 | `data/UAVIDS-2025.csv` |
| Cyber-physical UAV | Secondary (limitation case) | github.com/uamughal/UAVs-Dataset-Under-Normal-and-Cyberattacks | (see notebook 0) |
| VeReMi Extension | Cross-domain | kaggle.com/datasets/ivarprudnikov/veremi-extension-data-1-21-gb | `data/mixalldata_clean.csv` |

If you run the notebooks in Google Colab, adjust the `DATA` path at the top of each notebook (e.g. to `/content/data/`).

## Reproducing the results

Each notebook is self-contained and annotated with the corresponding section of the paper. Suggested order:

1. **`0_identity_leakage.ipynb`** — leakage and artifact analysis: row-index and flow-identifier leakage, degenerate identity fields, and the contrast with UAVIDS-2025 (Tables 1-2).
2. **`1_baselines_controls.ipynb`** — source-rate representation and the benign-anchored Mahalanobis detector under the LOACO source-disjoint protocol, with the learned-direction and other controls (Sections 3-4).
3. **`2_attention_autoencoder.ipynb`** — attention autoencoder, comparing the per-flow and source-rate representations (Section 4).
4. **`3_feature_ablation.ipynb`** — leave-one-feature-out, the reciprocal fan-out/concentration test, and permutation importance (Section 5.1).
5. **`4_model_ablation.ipynb`** — attention vs. plain autoencoder and the latent-dimension sweep (Section 5.2).
6. **`5_lightweight_baselines.ipynb`** — Isolation Forest and one-class SVM on the same representation (Section 5.3).
7. **`6_veremi_crossdomain.ipynb`** — cross-domain generalization on the VeReMi Extension VANET benchmark (Section 5.4).
8. **`7_complexity_robustness.ipynb`** — edge-realistic training/inference cost, and robustness to feature noise and class imbalance (Section 5.5).

All experiments use five random seeds (42, 1, 2, 3, 4) and report the mean and standard deviation.

## Citation

```bibtex
@article{aksudemir2026sourcerate,
  title     = {Source-rate representations and attention autoencoders for leakage-safe zero-day Sybil detection in UAV networks},
  author    = {Aksu Demir, {\.I}zel Ece and G{\"u}m{\"u}{\c s}, Fatma},
  journal   = {Electronics},
  year      = {2026},
  publisher = {MDPI},
  doi       = {}
}
```

## License

Released under the MIT License. See [LICENSE](LICENSE).
