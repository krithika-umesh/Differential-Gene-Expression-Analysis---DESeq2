# Differential Gene Expression Analysis using DESeq2
This repository aims to investigate differential gene expression between the heart and thyroid tissues, focusing on autoimmunity-related genes. The study seeks to uncover molecular distinctions contributing to autoimmunity, with the heart and thyroid selected as contrasting models for analysis.

There is a rising prevalence of Autoimmune Disease (AD) in the US over the past three decades. AD arises from the body's immune system malfunction, attacking its own cells due to failure in distinguishing foreign invaders from self-antigens. While autoimmunity affects various organs, the heart appears relatively protected. The hypothesis behind this analysis was that cardiac tissue was less prone to autoimmunity than thyroid tissue which represents prevalent autoimmune disorders like Grave's Disease, Hashimoto Thyroiditis etc. In other words, the genes that were responsible for the autoimmune conditions in thyroid were not expressed significantly in the heart i.e., there was a significant differential gene expression between the two tissues. 

# Materials & Methods
The bulk RNA Seq data of both the tissues from human samples was provided by the University and each tissue had 4 replicates. The samples were in the FASTQ format. Extracting the data for the analysis involved four steps to be performed on a shared computing cluster:
1. Quality control: In this step, each sample was tested for overall quality using FastQC (version 0.11.9). It checked parameters like per base sequence quality, per tile sequence quality, sequence duplication levels etc.
2. Trimming & Filtering: After ensuring that the samples were of high quality, the next step of trimming the sequences of low quality read ends and adapter sequences was performed. The sequences of low quality were then filtered. Trimming was performed on Trim Galore (version 0.6.6), Cutadapt (version 3.3). The Phred quality cut off score was 28.
3. Read Mapping: The trimmed sequences which were in ‘.bam’ format were then mapped to a reference human genome using Hisat2 (version 2.2.1), which is a bowtie algorithm. This step helped in identifying the transcripts. These files were sorted and indexed using ‘samtools’ package (version 0.1.19) and the results were visualized in Integrative Genomics Viewer (version 2.8.0). 
4. Counting: All the samples were then counted for total hits of genes using htseq-count from HTSeq library (version 0.11.2). The counted samples were then exported as tab separated text files to the home directory of the Virtual Machine.

# Analyses
1. Differential gene expression analysis - edgeR
2. Enrichment Analysis - Org.Hs.eg.db, DAVID, Enrichr

# Dependencies
R version 4.2.2
