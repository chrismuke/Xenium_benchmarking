# Xenium Benchmarking Datasets - Complete Catalog

## Overview
This document catalogs all 26+ datasets used in the study "Optimizing Xenium In Situ data utility by quality assessment and best practice analysis workflows" by Marco Salas et al. (Nature Methods, 2024). The datasets span multiple species, tissues, disease states, and Xenium platform versions, representing one of the most comprehensive spatial transcriptomics benchmarking efforts to date.

## Data Availability and Downloads

### Primary Data Sources

#### 1. **10X Genomics Public Datasets**
**Source**: https://www.10xgenomics.com/datasets  
**Access Date**: May 3, 2024  
**Description**: Majority of datasets were publicly available from 10X Genomics  
**Format**: Original Xenium machine output files  

#### 2. **Freshly Generated Datasets** 
**Zenodo DOI**: https://doi.org/10.5281/zenodo.10566172  
**Content**: 4 mouse brain sections (labeled "hm1-hm4")  
**Description**: Custom datasets generated specifically for this benchmarking study  
**Species**: Mouse  
**Tissue**: Brain  

#### 3. **Published Datasets**
**Source**: Kukanja, Langseth et al. (Cell, 2024)  
**DOI**: https://doi.org/10.1016/j.cell.2024.02.030  
**Content**: Human spinal cord datasets  
**Description**: Active and inactive disease regions  

### Pre-formatted AnnData Files

#### Main Zenodo Repositories
1. **Repository 1**: https://doi.org/10.5281/zenodo.11124988
2. **Repository 2**: https://doi.org/10.5281/zenodo.11121221  
3. **Repository 3**: https://doi.org/10.5281/zenodo.11120307

#### Example Dataset for End-to-End Pipeline
**Zenodo DOI**: https://doi.org/10.5281/zenodo.11120922  
**Content**: Human spinal cord sample  
**Purpose**: Tutorial and testing dataset  
**Size**: Single tissue section with complete processing pipeline  

#### End-to-End Pipeline Example
**Zenodo DOI**: https://doi.org/10.5281/zenodo.11612060  
**Content**: Complete pipeline demonstration  
**Description**: Full workflow example from raw data to analysis results  

## Complete Dataset Inventory

### Mouse Brain Datasets (11 total)

#### **10X Genomics Mouse Brain Collection (8 datasets)**

| Dataset ID | Filename | Description | Format Version | Section Type |
|------------|----------|-------------|----------------|--------------|
| ms_brain_rep1 | ms_brain_rep1.h5ad | Mouse brain replicate 1 | 2022 | Coronal |
| ms_brain_rep2 | ms_brain_rep2.h5ad | Mouse brain replicate 2 | 2022 | Coronal |
| ms_brain_rep3 | ms_brain_rep3.h5ad | Mouse brain replicate 3 | 2022 | Coronal |
| ms_brain_fullcoronal | ms_brain_fullcoronal.h5ad | Mouse brain full coronal | 2022 | Full coronal |
| ms_brain_partialcoronal | ms_brain_partialcoronal.h5ad | Mouse brain partial coronal | 2022 | Partial coronal |
| ms_brain_multisection1 | ms_brain_multisection1.h5ad | Mouse brain multi-section 1 | Early 2023 | Multi-section |
| ms_brain_multisection2 | ms_brain_multisection2.h5ad | Mouse brain multi-section 2 | Early 2023 | Multi-section |
| ms_brain_multisection3 | ms_brain_multisection3.h5ad | Mouse brain multi-section 3 | Early 2023 | Multi-section |

**Cell Types Present**: Neurons (various subtypes), oligodendrocytes, astrocytes, microglia, ependymal cells, endothelial cells  
**Genes**: ~200-400 genes depending on panel version  
**Tissue Regions**: Cortex, hippocampus, striatum, corpus callosum, ventricles  

#### **Freshly Generated Mouse Brain Collection (4 datasets)**

| Dataset ID | Filename | Description | Zenodo Link | Characteristics |
|------------|----------|-------------|-------------|-----------------|
| realmouse_1 | realmouse_1.h5ad | Home-made mouse brain 1 (hm1) | 10.5281/zenodo.10566172 | Custom protocol |
| realmouse_2 | realmouse_2.h5ad | Home-made mouse brain 2 (hm2) | 10.5281/zenodo.10566172 | Custom protocol |
| realmouse_3 | realmouse_3.h5ad | Home-made mouse brain 3 (hm3) | 10.5281/zenodo.10566172 | Custom protocol |
| realmouse_4 | realmouse_4.h5ad | Home-made mouse brain 4 (hm4) | 10.5281/zenodo.10566172 | Custom protocol |

**Species**: Mus musculus  
**Tissue**: Brain (coronal sections)  
**Protocol**: Optimized for this benchmarking study  
**Format**: Latest Xenium output format (2024)  

### Human Brain Datasets (3 total)

| Dataset ID | Filename | Description | Format Version | Disease State |
|------------|----------|-------------|----------------|---------------|
| human_brain | human_brain.h5ad | Human healthy brain | Mid-2023 | Healthy control |
| human_alzheimers | human_alzheimers.h5ad | Human Alzheimer's brain | Mid-2023 | Alzheimer's disease |
| human_gbm | human_gbm.h5ad | Human glioblastoma | Mid-2023 | Brain cancer |

**Species**: Homo sapiens  
**Cell Types**: Neurons, astrocytes, oligodendrocytes, microglia, endothelial cells, tumor cells (GBM)  
**Pathology**: Normal, neurodegenerative disease, brain cancer  
**Genes**: ~300-500 genes (includes addon panels)  

### Human Breast Datasets (7 total)

#### **FFPE Breast Sections (2 datasets)**
| Dataset ID | Filename | Description | Format Version | Section Size |
|------------|----------|-------------|----------------|--------------|
| h_breast_1 | h_breast_1.h5ad | Human breast FFPE large | 2022 | Large section |
| h_breast_2 | h_breast_2.h5ad | Human breast FFPE small | 2022 | Small section |

#### **Invasive Ductal Carcinoma (IDC) Collection (4 datasets)**
| Dataset ID | Filename | Cancer Type | Analysis Type | Description |
|------------|----------|-------------|---------------|-------------|
| hbreast_idc_addon_set1 | hbreast_idc_addon_set1.h5ad | IDC | Addon panel | Set 1 with extended gene panel |
| hbreast_idc_addon_set2 | hbreast_idc_addon_set2.h5ad | IDC | Addon panel | Set 2 with extended gene panel |
| hbreast_idc_addon_set4 | hbreast_idc_addon_set4.h5ad | IDC | Addon panel | Set 4 with extended gene panel |
| hbreast_idc_entiresample_set3 | hbreast_idc_entiresample_set3.h5ad | IDC | Entire sample | Complete section analysis |

#### **Invasive Lobular Carcinoma (ILC) Collection (3 datasets)**
| Dataset ID | Filename | Cancer Type | Analysis Type | Description |
|------------|----------|-------------|---------------|-------------|
| hbreast_ilc_addon_set2 | hbreast_ilc_addon_set2.h5ad | ILC | Addon panel | Set 2 with extended gene panel |
| hbreast_ilc_addon_set4 | hbreast_ilc_addon_set4.h5ad | ILC | Addon panel | Set 4 with extended gene panel |
| hbreast_ilc_entiresample_set3 | hbreast_ilc_entiresample_set3.h5ad | ILC | Entire sample | Complete section analysis |

**Species**: Homo sapiens  
**Cell Types**: Epithelial cells (ductal, lobular), stromal fibroblasts, immune cells (T cells, B cells, macrophages), endothelial cells, cancer cells  
**Disease States**: Normal, IDC, ILC  
**Genes**: ~200-500 genes (base + addon panels)  

### Human Lung Datasets (2 total)

| Dataset ID | Filename | Description | Format Version | Disease State |
|------------|----------|-------------|----------------|---------------|
| healthy_lung | healthy_lung.h5ad | Human healthy lung with addon | Mid-2023 | Healthy tissue |
| lung_cancer | lung_cancer.h5ad | Human lung cancer | Mid-2023 | Cancer tissue |

**Species**: Homo sapiens  
**Cell Types**: Pneumocytes (type I/II), alveolar macrophages, epithelial cells, endothelial cells, fibroblasts, immune cells, cancer cells  
**Disease States**: Normal, lung cancer  
**Tissue Regions**: Alveoli, airways, blood vessels  

### Human Spinal Cord Datasets (2 total)

| Dataset ID | Filename | Description | Original Publication | Disease Region |
|------------|----------|-------------|---------------------|----------------|
| human_spinal_chord_active | human_spinal_chord_active.h5ad | Human spinal cord active | Kukanja et al. Cell 2024 | Active disease |
| human_spinal_chord_inactive | human_spinal_chord_inactive.h5ad | Human spinal cord inactive | Kukanja et al. Cell 2024 | Inactive disease |

**Species**: Homo sapiens  
**Cell Types**: Motor neurons, interneurons, oligodendrocytes, astrocytes, microglia, ependymal cells  
**Disease Context**: Multiple sclerosis (active vs. inactive lesions)  
**Original Study**: https://doi.org/10.1016/j.cell.2024.02.030  

## Dataset Characteristics Summary

### Species Distribution
- **Human**: 14 datasets (54%)
- **Mouse**: 12 datasets (46%)

### Tissue Distribution
- **Brain**: 14 datasets (54%) - 11 mouse, 3 human
- **Breast**: 7 datasets (27%) - all human
- **Lung**: 2 datasets (8%) - all human  
- **Spinal cord**: 2 datasets (8%) - all human
- **Other**: 1 dataset (4%) - varies by analysis

### Disease State Distribution
- **Healthy/Normal**: ~15 datasets (58%)
- **Cancer**: ~9 datasets (35%) - breast IDC/ILC, lung cancer, glioblastoma
- **Neurological**: ~3 datasets (12%) - Alzheimer's, MS lesions

### Platform Version Distribution
- **2022 format**: 5 datasets (19%) - Early Xenium pre-release
- **Early 2023 format**: 3 datasets (12%) - First commercial release  
- **Mid-2023+ format**: 18 datasets (69%) - Current format with improvements

## Data Processing Standards

### Quality Metrics
- **Transcript Quality**: QV > 20 (Phred quality score)
- **Cell Filtering**: min_counts=40, min_genes=15
- **Distance Filtering**: Transcripts within specified distance to nuclei (typically 5-15μm)
- **Library Size**: Varies by tissue (1,000-50,000 transcripts per cell)

### Gene Panel Information
- **Base Panel**: ~200-300 genes (standard Xenium panel)
- **Addon Panels**: Additional ~100-300 genes for specific applications
- **Custom Panels**: Tissue-specific gene selections
- **Total Coverage**: Up to ~500 genes per dataset

### Spatial Resolution
- **Transcript Resolution**: ~200-300 nm precision
- **Cell Resolution**: Single-cell with subcellular transcript localization
- **Field of View**: Variable (1-10 mm²) depending on tissue section size
- **Imaging**: DAPI nuclear staining + transcript detection

## Cell Type Annotations

### Brain Tissues (Mouse & Human)
**Major Cell Classes**:
- **Neurons**: Excitatory neurons, inhibitory interneurons, motor neurons
- **Glia**: Astrocytes, oligodendrocytes, microglia, ependymal cells
- **Vascular**: Endothelial cells, pericytes, smooth muscle cells
- **Other**: Choroid plexus cells, meningeal cells

**Anatomical Regions**: Cortex, hippocampus, striatum, white matter tracts

### Breast Tissues (Human)
**Cell Types**:
- **Epithelial**: Ductal epithelium, lobular epithelium, myoepithelial cells
- **Stromal**: Fibroblasts, adipocytes, smooth muscle cells  
- **Immune**: T cells, B cells, macrophages, plasma cells
- **Vascular**: Endothelial cells, pericytes
- **Cancer**: Malignant epithelial cells (IDC/ILC subtypes)

### Lung Tissues (Human)
**Cell Types**:
- **Epithelial**: Type I/II pneumocytes, Clara cells, ciliated cells
- **Immune**: Alveolar macrophages, neutrophils, lymphocytes
- **Stromal**: Fibroblasts, smooth muscle cells
- **Vascular**: Pulmonary endothelium, capillary cells
- **Cancer**: Various lung cancer cell types

### Spinal Cord Tissues (Human)  
**Cell Types**:
- **Neural**: Motor neurons, interneurons, sensory neurons
- **Glial**: Oligodendrocytes, astrocytes, microglia, ependymal cells
- **Vascular**: CNS endothelium, pericytes
- **Disease-related**: Activated microglia, reactive astrocytes

## Usage Recommendations

### For New Users
1. **Start with example dataset**: Download human spinal cord sample (zenodo.11120922)
2. **Use end-to-end pipeline**: Begin with `end-to-end_pipeline_optimized_single_tissue.ipynb`
3. **Follow documentation**: Comprehensive guide at https://xenium-benchmarking-test.readthedocs.io

### For Specific Applications
- **Method development**: Use multiple tissue types for generalizability testing
- **Disease studies**: Human cancer datasets for pathology-focused analysis  
- **Comparative studies**: Mouse brain datasets for cross-species analysis
- **Technical validation**: Multiple format versions for robustness testing

### Data Download Strategy
1. **Small-scale testing**: Single example dataset (~1-2 GB)
2. **Comprehensive analysis**: Full pre-formatted collection (~50-100 GB)
3. **Custom analysis**: Original Xenium outputs from 10X Genomics (>500 GB)

## File Format Specifications

### AnnData Structure (.h5ad files)
```python
adata.X                    # Gene expression matrix (cells × genes)
adata.obs                  # Cell metadata
  ├── 'x_centroid'         # Cell centroid X coordinate  
  ├── 'y_centroid'         # Cell centroid Y coordinate
  ├── 'cell_area'          # Cell area in pixels
  ├── 'n_counts'           # Total transcript count per cell  
  └── 'sample'             # Sample identifier
adata.var                  # Gene metadata
adata.obsm['spatial']      # Spatial coordinates array
adata.layers['raw']        # Raw count data (if normalized)
adata.uns                  # Unstructured metadata
```

### Original Xenium Output Structure
```
xenium_output/
├── cell_feature_matrix/   # Gene expression matrix
├── transcripts.csv(.gz)   # Individual transcript coordinates
├── cells.csv(.gz)         # Cell polygon coordinates  
├── nucleus_boundaries.csv # Nuclear segmentation
├── cell_boundaries.csv    # Cell segmentation
├── morphology_focus/      # Tissue imaging
└── analysis/             # 10X analysis outputs
```

## Citation Requirements
When using these datasets, please cite:
1. **Primary study**: Marco Salas et al. "Optimizing Xenium In Situ data utility by quality assessment and best practice analysis workflows", Nature Methods (2024)
2. **Spinal cord data**: Kukanja, Langseth et al. (Cell, 2024) - for spinal cord datasets
3. **10X Genomics**: Acknowledge datasets from https://www.10xgenomics.com/datasets
4. **Zenodo repositories**: Include relevant Zenodo DOIs for downloaded data

## Data Use Agreements
- **10X Genomics datasets**: Follow 10X Genomics data use policies
- **Published datasets**: Respect original publication requirements  
- **Zenodo data**: Open access with attribution requirements
- **Human data**: May require institutional review for certain applications

## Contact and Support
For dataset-specific questions or access issues:
- **GitHub Issues**: https://github.com/Moldia/Xenium_benchmarking/issues
- **Documentation**: https://xenium-benchmarking-test.readthedocs.io
- **Primary Contact**: Marco Salas (corresponding author)

---

*Last updated: [Current Date] - Dataset catalog reflects data available at the time of study publication*