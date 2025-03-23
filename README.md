# Genomic Explotatory Data Analysis (EDA) 
This package contains functions to help explore genomic data of any type. All it requires is a counts matrix containing samples and feature information (i.e., genes, microbes, functions, etc...)

![Alt text](/img/RGenEDA_hex.png)

# Table of Contents
- [Installation](#installation)
- [Examples](#examples)
- [Contact](#contact)
- [License](#license)

## Installation

RGenEDA calls the following dependencies:
- ComplexHeatmap
- RColorBrewer
- grid
- magick
- scales
- pheatmap

To intall the RGenEDA package through R, run the following command:

```r
library(devtools)
devtools::install_github("mmartinez99/RGenEDA/")

library(RGenEDA)

```

## Examples
To demonstrate RGenEDA, we will utilize the pasilla dataset from R package `pasilla`. We will follow the standard [DESeq2 Workflow](https://www.bioconductor.org/packages/release/bioc/vignettes/DESeq2/inst/doc/DESeq2.html), but genomic data generated from other software is also acceptable. See [Introduction vignette](https://github.com/mikemartinez99/RGenEDA/blob/main/vignettes/introduction.Rmd) for more information regarding typical differential expression pre-processing and function calls. 

### Sample Distance heatmap
The sample distance heatmap is a powerful tool in genomic exploratory data analysis that helps assess samepl similarity using Euclidean distance. By visualizing these sample-to-sample distances, potential batch effects or outliers can be detected. In general, samples from the same condition (e.g., treatment, tissue-type, genotype, etc...) should cluster together. If anomalies are seen, it could suggest high intra-group variability, or even an additional covariate such as technical factors (i.e., high mitochondrial gene content, library size, etc...)

The example below assesses both metadata categories available from the `pasilla` dataset and is a basic example. Any number of metadata categories can be visualized with this function.

![Alt text](img/Sample_Distance_HM.tiff)

### Variable Feature Selection
Principal component analysis (PCA) is a dimensionality reduction technique used in exploratory data analysis to capture the most informative axes of variation in your data. Applying PCA to all features (e.g., genes, microbes, etc...) can introduce noise and obscure meaningful biological signals as many features in genomic data show little to no variation. Selecting highly variable features before performing PCA can improve the interpretability and efficiency of the analysis. The following plot which can be easily generated by the `plotVariance` function can help you choose a threshold for the number of features to include for PCA. Additionally, the variances returned by the function can be passed to the `generatePCs` function which returns a dataframe of eigenvectors which can be combined with metadata and easily passed to `ggplot2` for highly customizable PCA plots. 
![Alt text](img/Variable_Features.tiff)

### Eigenvector correlations
Eigenvector plots are a highly underrated diagnostic tool in exploratory data analysis. These plots help visualize how Eigenvectors (PCs) correlate with metadata variables to help identify which variables are driving major axes of variation in your data. If a PC strongly correlates with a variable of interest, you can confirm that your experiment is driven by the biology you are interested in, and also identify covariates affecting lesser axes of variation to help explain additional variance. 

![Alt text](img/EigenCorrelations.tiff)

## Contact
Michael Martinez M.S.

f007qps@dartmouth.edu
