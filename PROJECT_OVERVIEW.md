# Xenium Benchmarking Project - Complete Overview

## Study Information
**Title**: "Optimizing Xenium In Situ data utility by quality assessment and best practice analysis workflows"  
**Authors**: Marco Salas et al.  
**Publication**: Nature Methods (2024)  
**DOI**: [Link to Nature Methods paper](https://www.nature.com/articles/s41592-025-02617-2)  

## Abstract Summary
The Xenium In Situ platform by 10X Genomics provides subcellular resolution spatial transcriptomics mapping hundreds of genes. This study represents the first independent comprehensive evaluation of the Xenium platform, analyzing 25+ datasets across multiple tissues and species. It benchmarks the platform against eight other spatial transcriptomics technologies and evaluates computational tools for preprocessing, segmentation, domain identification, and spatial analysis.

## Project Architecture

### Repository Structure
```
Xenium_benchmarking/
├── xb/                                    # Core Python package
├── notebooks/                             # Analysis notebooks (organized by task)
├── data/                                 # Data storage directories
├── figures/                              # Generated visualizations
├── Banksy_py/                           # BANKSY submodule for domain identification
├── end-to-end_pipeline_optimized*.ipynb # Main analysis pipelines
├── xenium_benchmarking.yml              # Main conda environment
└── CLAUDE.md                            # Project instructions
```

## Core Python Package (`xb/`)

### Main Modules

#### 1. **formatting.py** (1,000+ lines)
**Purpose**: Data conversion and preprocessing from Xenium machine output to standardized formats
**Key Functions**:
- `format_xenium_adata()` - Original pre-release format converter
- `format_xenium_adata_2023()` - Early 2023 format converter  
- `format_xenium_adata_mid_2023()` - Mid-2023+ format converter
- `format_to_adata()` - Latest 2024 format converter (most comprehensive)
- `prep_xenium_data_for_baysor()` - Baysor cell segmentation preprocessing
- `format_baysor_output_to_adata()` - Baysor output formatting

**Data Evolution**: Handles 4 different Xenium output format versions across 2022-2024

#### 2. **preprocessing.py** (~200 lines)
**Purpose**: Standardized cell filtering, normalization, and clustering workflows
**Key Functions**:
- `main_preprocessing()` - Main preprocessing pipeline
- Cell quality filtering (min_counts, min_genes thresholds)
- Library size normalization (target sum = 100 counts/cell)
- Log transformation and scaling options
- PCA and neighborhood graph construction
- Leiden/Louvain clustering with multiple resolutions

#### 3. **domain_identification.py** (~400 lines)
**Purpose**: Spatial domain identification using multiple methods
**Key Methods**:
- `domains_by_banksy()` - BANKSY spatial domain identification
- `domains_by_nbd()` - Neighbors-based domain (NBD) method
- `domains_by_rbd()` - Read-based domain (RBD) method
- Multi-sample processing capabilities
- Parameter optimization workflows

**BANKSY Integration**: Interfaces with Banksy_py submodule for spatial neighborhood-aware clustering

#### 4. **calculating.py** (~400 lines)
**Purpose**: Quality metrics and benchmarking calculations
**Key Functions**:
- Dataset quality assessment metrics
- Cross-platform comparison calculations
- Statistical analysis utilities
- Performance benchmarking functions

#### 5. **plotting.py** (~150 lines)
**Purpose**: Specialized spatial visualization functions
**Key Functions**:
- Spatial scatter plots with cell type annotations
- Domain visualization
- Quality control plots
- Multi-sample visualization utilities

#### 6. **simulating.py** (~500 lines)
**Purpose**: Dataset simulation for method validation
**Key Functions**:
- Simulated dataset generation
- Parameter sensitivity testing
- Validation dataset creation

#### 7. **neighborhood.py** (~100 lines)
**Purpose**: Cell neighborhood analysis
**Dependencies**: Squidpy for spatial statistics
**Functions**: Spatial neighbor detection and analysis

#### 8. **Spage_main.py** (~400 lines)
**Purpose**: Gene expression imputation using SpaGE method
**Functionality**: Single-cell reference-based gene imputation

#### 9. **util.py** (~150 lines)
**Purpose**: Utility functions for image processing and data conversion
**Functions**: Image handling, coordinate transformations, data format utilities

## Analysis Workflow Structure

### Notebook Organization (10 main categories)

#### **0_formatting/** - Data Conversion
- **0_0**: Xenium to AnnData formatting
- **0_1**: Batch processing for R format conversion
- **0_2**: Simulated dataset formatting
- **0_3**: Nuclear read filtering

#### **1_datasets_exploration/** - Dataset Characterization
- Comprehensive analysis of all 25+ datasets
- Quality metrics across tissues and species
- Platform comparison preparation

#### **2_segmentation_free_analysis/** - Points-to-Regions Analysis
- Distance-based transcript assignment
- Subcellular localization analysis
- SSAM (Segmentation and Spatial Assignment of Molecules) implementation
- Brain-specific cell overlap studies

#### **3_techniques_comparison/** - Cross-Platform Benchmarking
- Comparison with 8 other spatial transcriptomics platforms
- Resegmentation analysis (3_1_resegmentation_notebooks/)
- Cell-to-domain assignment evaluation (3_2_cell_to_domain_assignment_notebooks/)

#### **4_optimal_expansion/** - Parameter Optimization
- Spatial expansion parameter tuning
- Multi-section analysis optimization

#### **5_segmentation_benchmark/** - Cell Segmentation Evaluation
- Baysor segmentation benchmarking
- Segmentation quality assessment
- Method comparison

#### **6_simulating_preprocessing/** - Simulation Studies
- Preprocessing strategy evaluation through simulation
- Parameter sensitivity analysis
- Method validation

#### **7_domain_exploration/** - Spatial Domain Methods
- BANKSY domain identification
- NBD and RBD method comparison
- Spatial architecture analysis

#### **8_SVF_identification/** - Spatially Variable Features
- Gene selection for spatial analysis
- Feature importance ranking
- Spatial variability quantification

#### **9_spatial_domain_annotation/** - Domain Annotation
- Cell type annotation workflows
- Spatial domain characterization
- Allen Brain Atlas integration

#### **10_gene_imputation/** - Expression Imputation
- SpaGE-based gene imputation
- Reference dataset integration
- Imputation quality assessment

### End-to-End Pipelines

#### **end-to-end_pipeline_optimized_single_tissue.ipynb**
Complete analysis workflow for single tissue samples including:
1. Data formatting and quality control
2. Preprocessing optimization
3. Domain identification
4. Spatial analysis
5. Visualization and interpretation

#### **end-to-end_pipeline_optimized.ipynb**
Multi-tissue analysis pipeline with batch processing capabilities

## External Dependencies and Tools

### Software Integration
- **Docker**: Required for Baysor cell segmentation (`louisk92/txsim_baysor:v0.6.2bin`)
- **BANKSY**: Spatial domain identification (Banksy_py submodule)
- **Scanpy**: Single-cell analysis framework
- **Squidpy**: Spatial transcriptomics analysis
- **SpaGE**: Gene expression imputation

### Key Python Dependencies
- **Core**: numpy, pandas, scipy, matplotlib, seaborn
- **Single-cell**: scanpy, anndata
- **Spatial**: squidpy, alphashape
- **Image**: tifffile, scikit-image
- **ML/Stats**: scikit-learn, statsmodels
- **Visualization**: bokeh, holoviews

## Data Processing Workflows

### Standard Processing Pipeline
1. **Format Detection**: Automatically detect Xenium output version
2. **Data Import**: Convert to AnnData format with spatial coordinates
3. **Quality Control**: Filter by transcript quality (QV > 20) and distance to nuclei
4. **Cell Filtering**: Remove cells with insufficient counts/genes (min_counts=40, min_genes=15)
5. **Normalization**: Library size normalization (target=100 counts/cell)
6. **Dimensionality Reduction**: PCA followed by UMAP
7. **Clustering**: Multi-resolution Leiden clustering [0.2, 0.5, 1.1]
8. **Spatial Analysis**: Neighborhood detection and domain identification

### Specialized Workflows

#### Cell Segmentation with Baysor
1. Export Xenium data to Baysor format
2. Run Baysor via Docker container
3. Import segmentation results back to AnnData
4. Quality assessment and comparison

#### Domain Identification Methods
1. **BANKSY**: Spatial neighborhood-aware clustering (λ ≈ 0.8 for domains)
2. **NBD**: Cell neighborhood composition-based domains
3. **RBD**: Transcript spatial distribution-based domains

## File System Organization

### Data Directories
- **data/unprocessed_adata/**: Raw AnnData files from Zenodo
- **data/unprocessed_adata_nuclei/**: Nuclear-filtered datasets
- **data/formatted_for_R/**: R-compatible data formats
- **figures/**: Generated plots organized by analysis section

### Environment Management
- **Main environment**: `xenium_benchmarking.yml` (Python 3.8 + spatial biology stack)
- **BANKSY environment**: `Banksy_py/environment.yml` (specialized for domain identification)

## Key Analysis Parameters

### Standard Settings
- **Spatial neighbors**: k_geom=15
- **Clustering resolutions**: [0.2, 0.5, 1.1] 
- **Normalization target**: 100 counts per cell
- **Quality filters**: min_counts=40, min_genes=15, QV > 20
- **BANKSY parameters**: λ=0.8, k_geom=15, max_m=1

### Optimization Ranges
- **Library normalization**: [10, 100, 1000, 10000] target sums
- **Neighbor counts**: [5, 15, 30, 50] neighbors
- **Clustering resolutions**: [0.1, 0.2, 0.5, 1.0, 1.5, 2.0]

## Research Contributions

### Methodological Advances
1. **First independent Xenium evaluation**: Comprehensive benchmarking vs. 8 other platforms
2. **Multi-format support**: Handles evolving Xenium output formats (2022-2024)
3. **Integrated domain identification**: Three complementary spatial domain methods
4. **Best practices establishment**: Evidence-based parameter recommendations
5. **Scalability assessment**: Analysis across 25+ datasets spanning multiple tissues/species

### Technical Innovations
1. **Flexible preprocessing framework**: Parameterizable workflows for different use cases
2. **Multi-sample processing**: Batch processing capabilities for large studies
3. **Quality-aware analysis**: Integration of transcript quality scores in analysis
4. **Cross-platform compatibility**: Standardized interfaces for multiple spatial methods

## Usage Documentation

### Getting Started
```bash
# Setup main environment
git clone https://github.com/Moldia/Xenium_benchmarking.git
cd Xenium_benchmarking
conda env create --name xb --file=xenium_benchmarking.yml
conda activate xb
pip install -e .

# Setup BANKSY environment  
cd Banksy_py
conda env create --name banksy --file=environment.yml
conda activate banksy
```

### Basic Usage Examples
```python
# Format Xenium data
from xb.formatting import format_to_adata
adata = format_to_adata(files=file_paths, output_path=output_dir)

# Standard preprocessing
from xb.preprocessing import main_preprocessing
adata = main_preprocessing(adata, target_sum=100, mincounts=40, mingenes=15)

# Domain identification
from xb.domain_identification import domains_by_banksy
adata, adata_banksy = domains_by_banksy(adata, banksy_params=params)
```

## Documentation and Support
- **Extended Documentation**: https://xenium-benchmarking-test.readthedocs.io/en/latest/index.html
- **GitHub Repository**: https://github.com/Moldia/Xenium_benchmarking
- **Example Dataset**: Human spinal cord sample available at https://doi.org/10.5281/zenodo.11120922

## Citation
When using this codebase, please cite:
Marco Salas et al. "Optimizing Xenium In Situ data utility by quality assessment and best practice analysis workflows", Nature Methods (2024).

## License and Availability
The codebase is publicly available with comprehensive documentation and example datasets to facilitate reproducible spatial transcriptomics analysis workflows.