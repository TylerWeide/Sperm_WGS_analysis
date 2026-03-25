## WGS Processing Pipeline

This directory contains stepwise scripts used for preprocessing, alignment, variant calling, filtering of whole genome sequencing (WGS) data, matching SNPs across populations, extraction of shared SNPs, and functional annotation.

Scripts are numbered to reflect execution order.

### Pipeline Steps and Scripts

1. FASTQ merging  
   - Step1_Merging_Fastq_individual  

2. Raw read quality control  
   - Step2_FastQC_raw  

3. Adapter trimming  
   - Step3_TrimAdapters  

4. Quality control summary  
   - Step4_MultiQC  

5. Alignment and initial sorting  
   - Step5_Align_Sort  

6. Indexing individual BAM files  
   - Step6_Index_individual  

7. Add read groups  
   - Step7_AddReadGroups  

8. Sort and index after adding read groups  
   - Step6b_Sort_and_Index_after_AddingRG  

9. Merge BAM files  
   - Step8_MergeBAMS  

10. Add read groups to merged BAMs  
    - Step8b_Add_Merged_ReadGroups  

11. Sort and index merged BAMs  
    - Step9_Sort_and_Index_Merged  

12. Duplicate marking  
    - Step10a_MarkDuplicates_Merged  
    - Step10b_MarkDuplicates  

13. Alignment statistics  
    - Step11a_Stats_Merged  
    - Step11b_Stats_Individual  

14. Variant calling (GATK HaplotypeCaller)  
    - Step12a_HaplotypeCaller_Individual  
    - Step12b_HaplotypeCaller_Merged  

15. Joint genotyping (GATK)  
    - Step13b_GenotypingGATK_Individual_A  
    - Step13b_GenotypingGATK_Individual_B  

16. Variant filtering (hard filters)  
    - Step14a_HardFilters_Merged  
    - Step14b_HardFilters_Individual  

17. Heterozygous SNP filtering  
    - Step15a_HetFilter_Merged  
    - Step15b_NonHetFilter_Individual  

18. SNP-level statistics  
    - Step16a_StatsOnSNPS_Merged  
    - Step16b_StatsOnSNPs_Individual  

19. Matching SNPs to merged heterozygous sites (bcftools isec)  
    - Step17_MatchingSNPs_to_Merged  

20. Extraction of shared SNPs  
    - Step18_ExtractingSharedSNPs  

21. Functional annotation  
    - Step19_Annotation  

---

These scripts were executed on HPC infrastructure and may require modification of file paths and environment variables for reuse in different computational environments.
