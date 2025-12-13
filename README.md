

# Stage Two HackBio: Single-Cell RNA-seq Analysis of a Putative Bone Marrow Dataset

## Overview

This repository presents a reproducible single-cell RNA-sequencing (scRNA-seq) analysis conducted as part of **Stage Two of the HackBio Internship (2025)**. The dataset, labelled *bone marrow*, was analysed using a Scanpy-based pipeline to perform dimensionality reduction, unsupervised clustering, and marker-driven cell-type annotation.

Beyond standard exploratory analysis, this project explicitly evaluates whether the inferred cellular composition is biologically consistent with true bone marrow tissue. The findings demonstrate a clear mismatch between the dataset label and the underlying biology.

---

## Objectives

* Preprocess and analyse a 10X Genomics scRNA-seq dataset
* Identify major cellular populations using UMAP and Leiden clustering
* Annotate clusters based on canonical marker genes
* Critically assess tissue identity and biological plausibility
* Provide a rigorous interpretation grounded in haematopoietic biology

---

## Dataset

* **Format:** 10X Genomics (.h5ad)
* **Label:** Bone Marrow (HackBio-provided)

---

## Analysis Summary

The analysis was performed using **Scanpy** and followed best practices for scRNA-seq workflows:

* Quality control and normalisation
* Highly variable gene selection and scaling
* PCA, neighbour graph construction, and UMAP embedding
* Leiden clustering and marker gene identification
* Marker-based cell-type annotation

---

## Cell Types Identified

The dataset was dominated by mature immune populations:

* Neutrophils
* Plasma cells
* Naïve B cells
* T cells (two distinct clusters)
* γδ T cells
* Eosinophils
* Dendritic cells
* Platelets
* **Podocytes (kidney epithelial cells; unexpected)**

---

## Key Finding: Dataset Identity

**Conclusion:** The dataset does **not** biologically represent bone marrow.

### Evidence

* **Absence of marrow progenitors:** No haematopoietic stem cells, early progenitors, erythroid precursors, or megakaryocyte intermediates were detected.
* **PBMC-like composition:** The cellular landscape closely resembles peripheral blood rather than a haematopoietic niche.
* **Unexpected podocytes:** Detection of kidney epithelial cells is incompatible with bone marrow tissue.
* **No differentiation gradients:** Authentic bone marrow exhibits clear stem-to-mature lineage trajectories, which are absent here.

---

## Interpretation

The dataset likely represents a **circulating immune cell population** rather than a true bone marrow sample. The presence of podocytes further suggests potential dataset mislabelling or annotation artefacts. This analysis highlights the importance of biological validation beyond automated cell-type assignment in single-cell studies.

---

## Tools

* Scanpy
* Matplotlib
* Seaborn


