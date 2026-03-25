# Sperm WGS Analysis

Statistical analysis of allelic ratio distortion (ARD) in mitochondrial-defined subpopulations of porcine sperm.

---

## Overview

This repository contains a complete workflow for processing whole genome sequencing (WGS) data and performing downstream statistical analysis to identify allele frequency shifts between sperm subpopulations separated by mitochondrial fluorescence intensity.

The pipeline spans raw sequencing data preprocessing, variant discovery, stringent filtering, cross-population SNP matching, and statistical evaluation of allele frequency differences within individual boars.

---

## Workflow Summary

### 1. Preprocessing and Alignment (scripts/)

Raw sequencing data were processed using a stepwise pipeline:

- FASTQ merging across sequencing lanes  
- Quality control (FastQC)  
- Adapter trimming  
- Alignment to the *Sus scrofa* reference genome (BWA)  
- Sorting and indexing of BAM files  
- Addition of read groups  
- Merging of BAM files  
- Duplicate marking (Picard)  
- Alignment statistics generation  

---

### 2. Variant Calling and Filtering (scripts/)

- Variant calling using GATK HaplotypeCaller  
  - Individual subpopulations  
  - Merged populations (per boar)  
- Genotyping using GATK GenotypeGVCFs  
- Hard filtering of SNPs using GATK-recommended thresholds  
- Filtering for high-confidence heterozygous SNPs  
- Removal of SNPs located within repeat regions  

---

### 3. SNP Matching and Annotation (scripts/)

- Identification of shared SNPs between subpopulations and merged populations using **bcftools isec**  
- Retention of SNPs present in both subpopulations and corresponding merged samples  
- Extraction of matched SNP sets for downstream analysis  
- Functional annotation of filtered SNPs using **SnpEff**  

This approach ensures that allele frequency comparisons are restricted to loci consistently detected across both subpopulations and their corresponding merged population, reducing bias from differential variant calling.

---

### 4. Downstream Statistical Analysis (analysis/)

- Matching SNPs across subpopulations based on genomic coordinates  
- Calculation of allele frequencies from allelic depth (AD) values  
- Filtering based on:
  - Read depth (DP)  
  - Allele depth (AD)  
  - Allele frequency (AF)  
- Retention of heterozygous SNPs in merged populations (AF = 0.4–0.6)  
- Comparison of allele frequencies between subpopulations  

---

## Statistical Methods

- Two-sided proportional Z-test  
- Fisher’s exact test  
- False discovery rate (FDR) correction  
- Welch’s t-test  
- Cohen’s D (non-pooled standard deviation)  

---

## Repository Structure
