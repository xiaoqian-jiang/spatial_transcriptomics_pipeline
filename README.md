# Spatial Transcriptomics Analysis Pipeline

## Overview
This repository provides a streamlined workflow for analyzing spatial transcriptomics (ST) data, utilizing advanced computational tools in Python (and R) to map cellular compositions and spatial niches in tissue sections. Using Zhu et al. (2022) as a case study, the pipeline explores the progression of lung adenocarcinoma (LUAD) from pre-invasive to invasive stages.

The primary aim is to gain hands-on experience with analyzing ST data while offering a practical reference for researchers interested in implementing similar workflows. By integrating best practices and robust tools, this repository enables the investigation of complex spatial dynamics in tissues.

## Project Objective
This repository provides a comprehensive workflow for ST data analysis, focusing on:
- **Deconvolution** of cell types and subtypes in spatial spots using reference single-cell RNA-seq (scRNA-seq) data.
  - Cell type annotations for the reference single-cell data are derived from our **[sgRNA-seq-pipeline](https://github.com/xiaoqian-jiang/sgRNA-seq-pipeline)**. Detailed documentation of the annotation process is available in the linked repository.
- **Integration** of spatial transcriptomics and scRNA-seq data to uncover spatially resolved molecular mechanisms driving LUAD progression.
## Data Source
The datasets analyzed in this project are from Zhu et al. (2022):

- **Title**: *Delineating the dynamic evolution from preneoplasia to invasive lung adenocarcinoma by integrating single-cell RNA sequencing and spatial transcriptomics.*
- **DOI**: [10.1038/s12276-022-00896-9](https://doi.org/10.1038/s12276-022-00896-9)

### Dataset Overview: ST Data
- **Platform**: 10× Genomics Visium
- **Sample Details**:
  - **Stages of LUAD**:
    - **Adenocarcinoma in situ (AIS)**: Samples TD5, TD8
    - **Minimally invasive adenocarcinoma (MIA)**: Samples TD3, TD6
    - **Invasive adenocarcinoma (IAC)**: Samples TD1, TD2
  - **Sequencing Depth**: 250–270M reads per sample
- **Data Processing**: Spatial transcriptomics data were processed using Space Ranger for alignment, quality control, and initial clustering.

## Analysis Workflow
The pipeline is divided into the following key steps:

### 1. Preprocessing of Spatial Transcriptomics Data (1.QC_and_Integration.py)
This step outlines fundamental preprocessing steps for raw spatial RNA-seq data, focusing on quality control and dataset integration:
- **Quality Control**: Metrics such as the proportion of mitochondrial gene expression (<15%), total UMI counts per spot (>500), and the number of detected spots per gene (>3) were evaluated using Scanpy.
- **Batch Effect Correction**: Using Scanorama, shared highly variable genes (HVGs) across datasets were used to align and integrate samples, minimizing technical artifacts while preserving biological variation.

### 2. Deconvolution Using Cell2location (2.Deconvolution_cell2location.py)
Cell2location was used to annotate cell types in spatial transcriptomics data by leveraging single-cell RNA sequencing (scRNA-seq) as a reference:
- **Reference Data**: Deconvolution relied on a reference built from nine scRNA-seq datasets derived from the same tissue type, ensuring consistency and biological relevance.
- **Cell Type Mapping**: Fine-grained cellular compositions were determined for each spatial spot, providing detailed insights into spatial niches.

### 3. Downstream Analyses
This section is currently under development. Future updates will include advanced analyses such as:
- Spatial trajectory analysis
- Cell-cell interaction mapping
- Visualization of spatial dynamics across LUAD stages

Stay tuned for detailed documentation and examples as the pipeline evolves.
