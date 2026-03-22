# Compositional-Data-Analysis-Frontier
This is the best way how to deal with the compositional data.
# Invariant Reference & Taxa Fluctuation Analysis (Pure Base R)

A robust analytical pipeline designed for **Compositional Data Analysis (CoDa)**, specifically microbiome or high-dimensional abundance data. This engine identifies stable "Invariant Reference" taxa using **Log-Ratio Variance (VLR)** and **CV Asymmetry**, then visualizes statistically certain fluctuations without external library dependencies.

## Key Features
- **Invariant Discovery**: Hybrid scoring using VLR (stability) and CV Asymmetry (directionality).
- **Robustness Scoring**: Calculates confidence levels for taxa shifts relative to the best-fit reference.
- **Pure Base R**: Zero dependencies (`ggplot2` or `tidyverse` not required).
- **Multi-Window Diagnostics**:
    - **Window 1**: Statistical distribution of VLR and Robustness scores.
    - **Window 2**: Scatter plots of Co-moving vs. Exclusionary taxa pairs.
    - **Window 3**: Viridis Heatmap with a **Red Marker (X)** on the most certain fluctuation.
    - **Window 4**: Trend lines with uncertainty bands (SD) for top candidates.

## Methodology
1. **Filtering**: Strict abundance thresholding to remove low-count noise.
2. **VLR Matrix**: Computes all-pairwise log-ratio variances to find stable co-movement.
3. **Reference Selection**: Ranks taxa by their ability to serve as a stable denominator (lowest Total Score).
4. **ALR Transformation**: Performs Additive Log-Ratio analysis centered on the selected invariant reference.
5. **Confidence Mapping**: Identifies fluctuations where the shift magnitude significantly outweighs the variance (`abs(median) / sd`).

## Usage
Ensure your input data (`Dataset`) is a matrix where:
- **Rows**: Samples
- **Columns**: Taxa / Features
- **Values**: Numeric relative abundances

```R
# Simply load your data into 'Dataset' and run the script.
Dataset <- read.csv("your_data.csv", row.names = 1)
# [Paste the provided script here]
