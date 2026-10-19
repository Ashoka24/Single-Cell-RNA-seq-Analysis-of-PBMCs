# Single-cell RNA-seq analysis of PBMCs

This repository contains a Scanpy workflow for exploring the public 10x Genomics PBMC 3k dataset. It validates the downloaded matrix, performs basic filtering and normalisation, identifies clusters, and writes plots and summary tables.

## Dataset

The workflow downloads the PBMC 3k filtered gene-barcode matrix from the public 10x Genomics source at runtime. Raw data are not committed here. See [data/README.md](data/README.md) for provenance.

## Run locally

Python 3.11 is recommended.

```bash
python -m pip install -r requirements.txt
python scripts/download_data.py
python scripts/validate_inputs.py --input data/raw/filtered_gene_bc_matrices/hg19
python scripts/run_analysis.py --config config/analysis.json --input data/raw/filtered_gene_bc_matrices/hg19 --output results
```

The workflow writes results locally; generated matrices and plots are not committed by default.

## Automated checks

GitHub Actions runs syntax checks, validates the JSON configuration, and executes the validator unit tests. A separate job downloads the public dataset and runs the Scanpy analysis on pushes to `main`; outputs are uploaded as a workflow artifact when available.

## Interpretation

This is an exploratory PBMC dataset workflow. Clusters are computational groupings and should not be treated as definitive cell identities without marker review and appropriate biological context. The dataset is a public example, not a new clinical cohort.
