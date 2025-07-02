# NBDA-Project
This repository contains the code developed for the "Network-based Data Analysis" (NBDA) course at the University of Trento, taught by Professor Lauria. The project focuses on applying various bioinformatics methods, including network-based approaches, to analyze a gene expression dataset related to Melanoma.
The primary goal was to identify molecular signatures and biological pathways associated with the progression from primary melanoma tumors to metastases, and to build classification models to distinguish between these two states.
## Dataset

The analysis utilizes gene expression data from the Gene Expression Omnibus (GEO).

*   **GEO Accession:** GSE8401
*   **Description:** Gene expression profiles comparing human primary cutaneous melanoma tumors and melanoma metastases.

## Analysis Steps

The R code in this repository performs the following main steps:

1.  **Data Loading and Preprocessing:**
    *   Fetching the GSE8401 dataset using `GEOquery`.
    *   Inspecting the expression data and metadata.
    *   Quality control through boxplots and histograms.
    *   Normalization and scaling of expression data.

2.  **Exploratory Data Analysis (EDA):**
    *   Principal Component Analysis (PCA) to visualize sample relationships and identify potential outliers based on tumor type.
    *   K-Means Clustering to group samples based on expression profiles and compare clusters to clinical labels.
    *   Hierarchical Clustering (HCL) with various distance metrics and linkage methods, evaluated using the Adjusted Rand Index (ARI) against clinical labels. Visualization of the optimal clustering.

3.  **Feature Selection and Modeling:**
    *   Identifying differentially expressed genes (using t-tests) between primary and metastatic samples.
    *   Training and evaluating several classification models:
        *   Linear Discriminant Analysis (LDA)
        *   Random Forest (RF)
        *   Lasso Regression (glmnet)
    *   Utilizing cross-validation (simple and repeated) to assess model performance and robustness (Accuracy).
    *   Identifying important genes based on model coefficients/importance scores (from RF, LDA, and Lasso).

4.  **Signature-based and Network Analysis (rScudo):**
    *   Applying the rScudo package to perform signature-based classification and network analysis on training and testing sets.
    *   Visualizing sample networks based on signature similarity.

5.  **Functional Enrichment Analysis:**
    *   Translating probe IDs to gene symbols.
    *   Performing functional enrichment analysis on sets of important/significant genes (identified by RF, LDA, Lasso) using `gprofiler2` to find enriched GO terms, pathways (KEGG, Reactome), etc.
    *   Utilizing `pathfindR` to perform pathway enrichment analysis and visualize results as networks (Term-Gene graphs), incorporating protein-protein interaction data. Analysis is performed separately for up and down-regulated genes identified by different models.

## Technologies Used

*   **Language:** R
*   **Key Packages:** `BiocManager`, `GEOquery`, `useful`, `pROC`, `ggplot2`, `genefilter`, `randomForest`, `caret`, `MASS`, `glmnet`, `ROCR`, `rScudo`, `igraph`, `gprofiler2`, `pathfindR`, `hgu133a.db`, `AnnotationDbi`, `org.Hs.eg.db`, `KEGGREST`, `KEGGgraph`, `dplyr`, `dendextend`, `aricode`, `pheatmap`, `RColorBrewer`, `ggrepel`.

## How to Run the Code

1.  Clone this repository to your local machine.
2.  Ensure you have R and RStudio installed.
3.  Install the required R packages. Many can be installed via `install.packages()` and `BiocManager::install()`. 
4.  Open the `.Rmd` file in RStudio.
5.  Run the R Markdown file chunk by chunk or knit the entire document to reproduce the analysis and generate the output.
