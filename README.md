# A Survey of Heterogeneous Graph Neural Networks for Cybersecurity Anomaly Detection

This repository contains the manuscript, reviewer rebuttals, and experimental scaffolding for the paper **"A Survey of Heterogeneous Graph Neural Networks for Cybersecurity Anomaly Detection."**

## Overview
As cybersecurity threats evolve in complexity, traditional static and homogeneous graph models often fail to capture the multi-typed relations and temporal dynamics of modern cyber-physical systems. This work provides a structured taxonomy of Heterogeneous Graph Neural Networks (HGNNs) categorized by anomaly granularity (node, edge, and subgraph) and graph dynamics. 

Beyond the survey, this repository includes a **reproducible empirical case study** that evaluates representative HGNN models (DOMINANT, TADDY, and StrGNN) under a unified evaluation pipeline.

## Key Contributions
- **Task-Driven Taxonomy:** A systematic classification of HGNN-based anomaly detection methods.
- **Cybersecurity Applications:** Detailed analysis of HGNNs in Insider Threat, Network Intrusion Detection (NID), Fraud Detection, and Advanced Persistent Threats (APTs).
- **Empirical Case Study:** Quantitative evaluation of three distinct HGNN paradigms on a normalized version of the UNSW-NB15 dataset.
- **Standardized Evaluation:** Concrete recommendations for temporal splits, imbalance-aware metrics (AUPRC), and analyst-centric metrics (Precision@K).

## Repository Structure
- `/experiments`: A unified pipeline for HGNN model evaluation.
  - `/src/jcs_experiments`: Core adapter and metric calculation logic.
  - `/scripts`: Scripts for data preparation, normalization, and orchestration.
  - `/configs`: YAML configurations for the case study.
  - `/data`: (Local only) Placeholder for raw and normalized cybersecurity datasets.
  - `/external`: Cloned repositories for core baseline models.
- `paper_markup.tex`: The revised manuscript with changes highlighted in blue.
- `rebuttal_v2.pdf`: Formal point-by-point response to Reviewer #1 and Reviewer #2.
- `figures/`: Source scripts and assets for paper figures.

## Getting Started

### 1. Requirements
The experimental pipeline requires Python 3.8+ and several scientific computing libraries:
```bash
pip install -r experiments/requirements.txt
```

### 2. Data Normalization
The pipeline assumes a normalized edge-event CSV schema (`source, destination, timestamp, label`). 
To prepare the dataset for the case study:
1. Download the public UNSW-NB15 or CICIDS2017 dataset.
2. Run the normalization script:
```bash
python experiments/scripts/prepare_dataset.py --dataset unsw_nb15 --raw-csv path/to/dataset.csv
```

### 3. Running the Case Study
To execute the unified evaluation pass across all supported models:
```bash
python experiments/scripts/run_case_study.py --config experiments/configs/case_study.yaml
```

## Experimental Results (Targeted Case Study)
The following results were observed under our unified local pipeline (UNSW-NB15 proxy graph):

| Model | Paradigm | Metric | Result |
| :--- | :--- | :--- | :--- |
| **DOMINANT** | Static Reconstruction | AUROC | ~0.365 |
| **TADDY** | Dynamic Transformer | Total AUC | ~0.639 |
| **StrGNN** | Structural-Temporal | AUROC | ~0.733 |

## Citation
If you find this survey or the experimental scaffolding useful for your research, please cite our work:

```bibtex
@article{jiang2026survey,
  title={A Survey of Heterogeneous Graph Neural Networks for Cybersecurity Anomaly Detection},
  author={Jiang, Shan},
  journal={Journal of Computer Security (Revision)},
  year={2026}
}
```
