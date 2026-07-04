# UAV Sybil Detection

Leakage-safe zero-day detection of Sybil attacks in UAV networks: a source-rate representation scored against a benign anchor, with a hyperparameter-free Mahalanobis detector and an attention autoencoder, evaluated under a source-disjoint leave-one-attack-class-out (LOACO) protocol.

## Status

This repository accompanies a manuscript currently under review. The code that reproduces all experiments will be released here upon acceptance.

## Contents (to be released)

- `identity_leakage_analysis.ipynb` — identity-field availability and   leakage diagnostics
- `baselines_and_controls.ipynb` — per-attack motivation, baseline detectors, and the control experiments (artifact, source-disjoint,   split-ratio, confidence-gate)
- `attention_autoencoder.ipynb` — the attention-autoencoder detector and   its interpretability analysis

## Data

Experiments use two publicly described datasets, obtained from their respective authors:

- UAVIDS-2025 (flow-level UAV intrusion dataset)
- A cyber-physical UAV intrusion dataset (packet-level)

See the manuscript for dataset references and access details.
