
# Quality_Control_for_data_quality

Quality control assessment of LC-MS data from Omics dataset to ensure
data quality .

This repository contains R scripts and data for performing quality
control (QC) analyses on both omics and xenobiotics datasets. The
analyses follow standard reproducibility metrics and WADA guidelines for
chemical and biological data.

## Repository Structure

quality_control_for_data_quality/ ├── QC_omics_statistical_analysis.Rmd
\# QC analysis for omics datasets ├──
QC_xenobiotics_statistical_analysis.Rmd \# QC analysis for xenobiotics
datasets ├── input/ \# Raw input files │ ├── formulas.csv \# Omics
dataset │ └── xenob_QC.csv \# Xenobiotics dataset ├── output/ \#
Generated output (processed data, plots) ├── quality_control_stats.Rproj
\# R project file └── README.md \# This file

## 1. QC Analysis of Omics Data

File: QC_omics_statistical_analysis.Rmd

This analysis performs quality control on LC-HRMS omics datasets.

### Key Steps:

1.  Load raw data: Import the LC-HRMS measurements.
2.  Clean data: Remove isotopologues, low-intensity features, and known
    contaminants.
3.  Chemical filtering: Apply H/C, N/C, O/C ratios and magnitude
    thresholds.
4.  Reproducibility metrics:

-   Identify common vs. unique features across replicates.
-   Calculate replicate intensity differences (RIdiff) and thresholds.

5.  Average replicates: Compute mean peak intensities for repeated
    molecular formulas.
6.  Visualizations:

-   Average peak intensities per retention time
-   RSD distribution across replicates

7.  Export results: Cleaned datasets, reproducibility summary, and plots
    are saved in the output/ folder. 

R Packages Used: tidyverse, data.table, NLP, jsonlite

## 2. QC Analysis of Xenobiotics Data

File: QC_xenobiotics_statistical_analysis.Rmd

This analysis performs quality control on xenobiotics datasets according to WADA guidelines.

### Key Steps:

1. Load raw data: Import xenobiotics QC measurements.
2. Calculate measured concentration: Compute mean ratios, standard deviation, and CV (%).
3. Relative accuracy (% Bias): Compare blood and urine measurements against reference matrix.
4. Precision:

- Intra-day: Variability within the same day.
- Inter-day: Variability across different days.

5. System suitability: Assess retention time (RT) reproducibility and internal standard precision.
6. Visualizations:

- Accuracy and CV across matrices
- Intra- and inter-day precision

7. Export results: Processed datasets and plots are saved in the output/ folder.
R Packages Used: tidyverse

## How to Use

Clone the repository:
```
git clone git@github.com:beccamatos/quality_control_for_data_quality.git
cd quality_control_for_data_quality
```
Open the project in RStudio using quality_control_stats.Rproj.
Render the Markdown files to HTML:
```
rmarkdown::render("QC_omics_statistical_analysis.Rmd")
rmarkdown::render("QC_xenobiotics_statistical_analysis.Rmd")
```
