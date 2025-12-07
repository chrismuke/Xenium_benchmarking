# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains analysis code for reproducing **"Optimizing Xenium In Situ data utility by quality assessment and best practice analysis workflows"** by Marco Salas et al. 2024.

The project benchmarks the Xenium In Situ platform (10X Genomics) against other spatial transcriptomics technologies and evaluates computational tools for preprocessing, segmentation, domain identification, and spatial analysis.

**Documentation**: https://xenium-benchmarking-test.readthedocs.io/en/latest/index.html

## Environment Setup

### Primary Environment (Python 3.8)
```bash
conda env create --name xb --file=xenium_benchmarking.yml
conda activate xb
pip install -e .
```

### BANKSY Submodule
The `Banksy_py` directory is a git submodule with its own environment:
```bash
cd Banksy_py
conda env create --name banksy --file=environment.yml
conda activate banksy
```

### Additional Notebook Environments
Specific analysis notebooks require dedicated environments (found in notebook directories):
- `notebooks/7_domain_exploration/`: spagcn.yml, SPACEL.yml, stagate.yml
- `notebooks/8_SVF_identification/`: sinfonia.yml, somde.yml
- `notebooks/10_gene_imputation/`: Benchmarkingenvironment.yml

## Core Architecture

### Python Package (`xb/`)
- **formatting.py**: Xenium-to-AnnData conversion, Baysor data preparation
- **preprocessing.py**: Cell filtering, normalization, Leiden clustering pipelines
- **domain_identification.py**: BANKSY, NBD (neighbors-based), RBD (read-based) spatial domain methods
- **calculating.py**: Quality metrics calculation
- **plotting.py**: Spatial visualization
- **simulating.py**: Dataset simulation
- **neighborhood.py**: Cell neighborhood analysis via Squidpy
- **Spage_main.py**: SpaGE gene imputation
- **util.py**: Image processing and data conversion helpers

### Key Data Flow
1. Raw Xenium output → `format_xenium_adata()` → AnnData (.h5ad)
2. AnnData → `main_preprocessing()` → Filtered/normalized/clustered data
3. Processed AnnData → `domains_by_banksy()` → Spatial domain assignments

### End-to-End Pipelines
- **end-to-end_pipeline_optimized_single_tissue.ipynb**: Single tissue analysis
- **end-to-end_pipeline_optimized.ipynb**: Multi-tissue analysis

## Key API Usage

### Formatting Xenium Data
```python
from xb.formatting import format_to_adata
adata = format_to_adata(files=file_paths, output_path=output_dir,
                        max_nucleus_distance=10, min_quality=0)
```

### BANKSY Domain Identification
```python
from xb.domain_identification import domains_by_banksy
banksy_params = {
    'resolutions': [0.9], 'pca_dims': [20], 'lambda_list': [0.8],
    'k_geom': 15, 'max_m': 1,
    'nbr_weight_decay': 'scaled_gaussian', 'cluster_algorithm': 'leiden'
}
adata, adata_banksy = domains_by_banksy(adata, banksy_params=banksy_params)
```

### Baysor Cell Segmentation
```python
from xb.formatting import prep_xenium_data_for_baysor, format_baysor_output_to_adata
prep_xenium_data_for_baysor(xenium_path, output_path)
# Run via Docker: docker pull louisk92/txsim_baysor:v0.6.2bin
# See xb/run_baysor.sh for execution
adata = format_baysor_output_to_adata(baysor_path, output_path)
```

## Default Parameters

- **Spatial neighbors**: k_geom=15
- **Clustering resolutions**: [0.2, 0.5, 1.1]
- **Normalization target**: 100 counts/cell
- **Cell quality filters**: min_counts=40, min_genes=15
- **BANKSY lambda** for domain identification: ~0.8

## Data Paths

- `data/unprocessed_adata/`: Raw AnnData files
- `data/unprocessed_adata_nuclei/`: Nucleus-filtered data
- `data/formatted_for_R/`: R-compatible formats
- `figures/`: Generated visualizations

Pre-formatted datasets available on Zenodo (see README.md for links).

## Notes

- No test suite exists in this repository
- BANKSY_py submodule must be initialized: `git submodule update --init`
- Docker required for Baysor segmentation
