# ScRNAseq pre-processing workflow with Seurat"

## 1 Introduction 
This repository provides a preprocessing pipeline for single-cell RNA sequencing (scRNA-seq) data from lung tumor samples, using the Seurat package in R. The goal is to clean and structure raw count data, ensuring it is ready for downstream analyses like differential expression, cell type annotation, and pathway enrichment.

The pipeline includes key steps such as quality control, normalization, feature selection, batch correction (if needed), dimensionality reduction (PCA, UMAP), and clustering to identify distinct cell populations. These steps help minimize technical noise and enhance the biological insights derived from the data.

By leveraging R, Seurat, Bioconductor, and ggplot2, this project provides a reproducible workflow for processing lung tumor scRNA-seq data. The structured datasets generated here will support further exploration of tumor heterogeneity and microenvironment dynamics.
# Pipeline 
![image](https://github.com/user-attachments/assets/da082eec-3bc7-4914-a42a-a5351c5d4f56)

---

## 2 Input data explaination
- **File HDF5**: `40k_NSCLC_DTC_3p_HT_nextgem_Multiplex_count_raw_feature_bc_matrix.h5`
- **Data gene expression**
https://cf.10xgenomics.com/samples/cell-exp/6.1.0/40k_NSCLC_DTC_3p_HT_nextgem_Multiplex/40k_NSCLC_DTC_3p_HT_nextgem_Multiplex_count_raw_feature_bc_matrix.h5

---

## 3 Analysis Workflow
3.1 Data Import
Use Read10X_h5() to load the .h5 file and extract gene expression data.

3.2 Create Seurat Object
Initialize a Seurat object with CreateSeuratObject(), applying cell filtering criteria.

3.3 Quality Control (QC)
Compute the percentage of mitochondrial (MT) genes.
Visualize data quality using VlnPlot() and FeatureScatter().
Filter cells based on gene expression thresholds (nFeature_RNA, percent_mt).

3.4 Normalization & Feature Selection
Normalize data with NormalizeData().
Identify highly variable genes using FindVariableFeatures().

3.5 Dimensionality Reduction & Clustering
Perform PCA with RunPCA() and assess with ElbowPlot().
Cluster cells using FindNeighbors() and FindClusters().
Apply UMAP for visualization with RunUMAP().

## 4 How to Run
Environment Requirements
  R (>= 4.0)
  Required packages: Seurat, ggplot2, dplyr, Matrix
  Execute the Script
Open R and run:
source("code/analysis.R")

- Expected Outputs
    Cell clustering based on gene expression.
    Dimensionality reduction using PCA and UMAP.
    Identification of highly variable genes within the dataset.

Clustering visualization and results will be saved in the results/ directory.
