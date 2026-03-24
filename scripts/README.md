## WGS Processing Pipeline

This directory contains stepwise scripts used for preprocessing, alignment, variant calling, and filtering of whole genome sequencing data.

Scripts are numbered to reflect execution order.

### Major steps:

1. FASTQ merging and quality control  
2. Adapter trimming  
3. Alignment to reference genome (BWA)  
4. BAM processing (sorting, indexing, read groups)  
5. Duplicate marking  
6. Variant calling (GATK HaplotypeCaller)  
7. Variant filtering and SNP extraction  

These scripts were executed on HPC infrastructure and may require modification of file paths and environment variables for reuse.

Scripts labeled A and B are the same scripts but running different samples (limited node space during the time of analysis)
