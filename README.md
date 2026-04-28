## MetaResist

[![Snakemake](https://img.shields.io/badge/snakemake-≥9.0-brightgreen.svg)](https://snakemake.github.io)

# Pipeline for resistome analysis and AMR prediction from metagenomic sequencing data.

This repository provides an integrated pipeline for the analysis and prediction of antimicrobial resistance (AMR) profiles from metagenomic sequencing data. The workflow aims to enable comprehensive resistome characterization.
Starting from publicly available sequencing data, the pipeline performs taxonomic profiling using Kaiju, followed by visualization with Krona and targeted filtering of species-specific reads (initially Klebsiella pneumoniae and Streptococcus pneumoniae). Identified reads are subsequently mapped to the CARD database to infer resistance-associated genes.
Building on these features, the pipeline incorporates a machine learning approach (stackPred), including retraining on clinical datasets, to predict antimicrobial resistance profiles. The framework is designed to bridge metagenomic data and clinical insights, enabling robust and scalable AMR prediction comparable to real-world clinical samples.


