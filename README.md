# Sperm WGS Analysis

Statistical analysis of allelic ratio distortion (ARD) in mitochondrial-defined subpopulations of porcine sperm.

---

## Overview

This repository contains a full workflow for processing whole genome sequencing (WGS) data and performing downstream statistical analysis to identify allele frequency shifts between sperm subpopulations separated by mitochondrial fluorescence intensity.

The pipeline includes preprocessing of raw sequencing data, variant calling, filtering, and statistical testing of allele frequency differences within individual boars.

---

## Workflow Summary

### 1. Preprocessing and Alignment (scripts/)

Raw sequencing data were processed using a stepwise pipeline including:

- FASTQ merging
- Quality control (FastQC)
- Adapter trimming
- Alignment to the Sus scrofa reference genome (BWA)
- Sorting and indexing of BAM files
- Addition of read groups
- Merging of BAM files
- Duplicate marking (Picard)
- Alignment statistics generation

### 2. Variant Calling and Filtering

- Variant calling using GATK HaplotypeCaller
  - Individual samples
  - Merged populations
- Genotyping and variant calling using GATK
- Hard filtering of SNPs
- Filtering for heterozygous SNPs
- SNP-level summary statistics

Note: Functional annotation (e.g., SnpEff) is not listed here due to being performed via a separate environment and not saved as a separate .sh

### 3. Downstream Statistical Analysis (analysis/)

- Matching SNPs across subpopulations based on genomic coordinates
- Filtering based on:
  - Allele depth (AD)
  - Read depth (DP)
  - Allele frequency (AF)
- Retaining heterozygous SNPs in merged populations (AF = 0.4–0.6)
- Comparing allele frequencies between subpopulations

---

## Statistical Methods

- Two-sided proportional Z-test
- Fisher’s exact test
- False discovery rate (FDR) correction
- Welch's T-test
- Cohen's D (non-pooled SD)

---

## Repository Structure

- `scripts/`  
  Preprocessing, alignment, variant calling, and filtering scripts

- `analysis/`  
  Downstream statistical analysis and visualization

  - `Updated_Manhattan.qmd`  
    Performs allele frequency comparisons and generates Manhattan plots

  - `MitoLength.qmd`  
    Compares mitochondrial sheath length between sperm subpopulations

---

## Data Description

- Samples consist of sperm subpopulations sorted by mitochondrial fluorescence intensity
- Three boars were analyzed
- SNP-level analysis is performed across matched genomic coordinates between subpopulations
- Each population includes approximately 500 measurements for mitochondrial sheath length

---

## Notes

- Raw sequencing data (FASTQ, BAM) are not included due to size constraints
- Analysis was performed using the Sus scrofa reference genome (Sscrofa11.1)
- Allele frequencies were calculated from allelic depth (AD) values rather than relying on INFO/AF fields
- Pipeline scripts reflect HPC-based execution but are provided here for reproducibility

---

## Contact

Tyler Weide  
Iowa State University  
