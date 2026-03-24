# Sperm WGS Analysis

Statistical analysis of allelic ratio distortion (ARD) in mitochondrial-defined subpopulations of porcine sperm.

---

## Overview

This repository contains downstream statistical analysis and visualization workflows used to identify allele frequency shifts between sperm subpopulations separated by mitochondrial fluorescence intensity.

Whole genome sequencing (WGS), alignment, and variant calling were performed on high-performance computing (HPC) infrastructure prior to this analysis. This repository focuses on post-processing, statistical testing, and visualization of allele frequency differences.

---

## Analysis Summary

The analysis performed in this repository includes:

- Matching SNPs across subpopulations based on genomic coordinates
- Filtering variants based on:
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
- Cohen's d (non-pooled SD)
---

## Repository Structure

- `analysis/`
  - `Updated_Manhattan.qmd`  
    Performs allele frequency comparison, statistical testing, and generates Manhattan plots

  - `MitoLength.qmd`  
    Compares mitochondrial sheath length between sperm subpopulations

---

## Data Description

- Samples consist of sperm subpopulations sorted by mitochondrial fluorescence intensity
- Three boars were analyzed
- Each population includes approximately 500 measurements for mitochondrial sheath length
- SNP-level analysis is performed across matched genomic coordinates between subpopulations

---

## Notes

- Raw sequencing data (FASTQ, BAM) and intermediate variant files are not included
- Allele frequencies are calculated directly from allelic depth (AD) values rather than INFO/AF fields
- HPC-based processing scripts (alignment, variant calling) are not included in this repository

---

## Contact

Tyler Weide  
Iowa State University  
