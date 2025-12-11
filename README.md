Stage Two HackBio: scRNA-seq Analysis of “Bone Marrow” Dataset

Reference: HackBio Internship 2025 – Stage Two Single-Cell RNA-seq Analysis
Dataset label: “Bone Marrow” (10X Genomics)

Overview

This repository contains the complete workflow and written interpretation for Stage Two of the HackBio Internship. The project focused on analysing a single-cell RNA-sequencing dataset labelled “bone marrow”, performing dimensionality reduction, clustering, and cell-type annotation using Scanpy. A detailed biological evaluation was carried out to determine whether the dataset truly represents bone marrow tissue.

The repository includes:

The computational notebook


Full biological interpretation


Figures generated during clustering and annotation


Summary of findings regarding tissue identity

Objectives

Import and preprocess the scRNA-seq dataset


Perform UMAP-based clustering to detect major cell populations


Annotate clusters using canonical marker genes


Assess biological relevance and verify whether the dataset truly corresponds to bone marrow


Provide a clear scientific explanation of identified cell types

Dataset

Format: 10X Genomics matrix (.h5ad)

Provided as a labelled “bone marrow” dataset from HackBio

Single-Cell Analysis Pipeline (Scanpy + scVelo)
1. Load Data
Import Scanpy and load the .h5ad dataset into an AnnData object.
2. Quality Control
Filter out low-quality cells and lowly expressed genes.
 Compute QC metrics such as total counts, gene counts and mitochondrial percentage.
3. Normalisation
Adjust counts so each cell has the same total read depth (e.g. 10,000 counts).
4. Log Transform
Apply log1p to stabilise expression variance and reduce the influence of extreme values.
5. Identify Highly Variable Genes
Select the most informative genes with high variability across cells.
6. Scaling
Standardise gene expression to mean 0 and variance 1.
 Optionally regress out unwanted factors like mitochondrial percentage.
7. PCA (Principal Component Analysis)
Reduce dimensionality and capture the main patterns of variation.
8. Neighbour Graph Construction
Build a k-nearest neighbour graph using PCA components.
9. UMAP Embedding
Create a 2D visualisation for exploring cell populations.
10. Clustering (Leiden or Louvain)
Group cells into clusters based on similarity in the neighbour graph.
11. Marker Gene Identification
Identify genes that best distinguish each cluster.
12. Cell Type Annotation
Assign biological identities to clusters using known marker genes or automated annotation tools.


Cell Types Identified

The following cell populations were detected through marker-based annotation:


Neutrophils


Plasma cells


Naïve B cells


T cells (two separate clusters)


γδ (gamma-delta) T cells


Eosinophils


Dendritic cells


Platelets


Podocytes (kidney epithelial cells – unexpected)

Biological Role of Each Cell Type

Neutrophils – Rapid innate responders that phagocytose pathogens.

Plasma cells – Mature B-cell derivatives that secrete antibodies.

Naïve B cells – Antigen-inexperienced B cells capable of activation and differentiation.

T cells (clusters 3 & 7) – Mediate cytotoxic immunity or coordinate immune responses.

γδ T cells – Fast-acting T-cell subpopulation that recognises non-peptide antigens.

Eosinophils – Granulocytes involved in helminth immunity and allergic inflammation.

Dendritic cells – Antigen-presenting cells that initiate adaptive immune responses.

Platelets – Support clotting and inflammation; fragments derived from megakaryocytes.

Podocytes – Specialised kidney epithelial cells that form the glomerular filtration barrier (not expected in bone marrow).

Is the Dataset Truly Bone Marrow?

Conclusion: No — the dataset does NOT biologically represent bone marrow tissue.

Multiple lines of evidence indicate a mismatch:

a. Absence of true bone-marrow lineages

Expected marrow populations were missing:

Haematopoietic stem cells (HSCs)

Early myeloid and lymphoid progenitors

Erythroid precursors

Megakaryocyte lineage intermediates

Their absence contradicts the biology of a true marrow sample.

b. Presence of immune-dominant PBMC-like populations

The cell types detected (T cells, B cells, dendritic cells, eosinophils, platelets) resemble peripheral blood mononuclear cells (PBMCs) more than bone marrow.

This pattern is typical for circulating blood, NOT a haematopoietic tissue rich in progenitors.

c. Presence of podocytes (kidney epithelial cells)

Podocytes are terminally differentiated kidney cells, which should never appear in bone marrow.

Their presence suggests:

Dataset mislabelling

Or contamination in cell-type reference predictions

d. Lack of differentiation gradients

True bone marrow shows strong developmental trajectories:

HSC → progenitors → mature lineages

This dataset shows fully differentiated immune cells, with no visible maturation continuum.

Key Findings

Ten distinct clusters were identified representing mainly immune cells.

The dataset composition aligns with PBMCs, not bone marrow.

Podocyte detection indicates probable misannotation or dataset mislabelling.

UMAP clustering confirms absence of progenitor lineages expected in marrow.

Tools: Scanpy, Matplotlib, Seaborn

Analysis and interpretation: Akpederi Gloria Omogwigho


