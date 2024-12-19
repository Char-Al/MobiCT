# MobiCT
ctDNA Analysis pipeline 

# Introduction
Mobict is an analysis pipeline designed for detecting SNV and small InDels in circulating tumor DNA (ctDNA) obtained through non-invasive liquid biopsy, serving diagnostic, prognostic, and therapeutic purposes.
The pipeline is built using Nextflow.

# Quick Start

1. Install nextflow (https://www.nextflow.io/docs/latest/install.html).
2. Create a conda environment for MobiCT:
    `conda create -n myenv -c conda-forge -c bioconda gatk4 fgbio bwa fastp samtools picard vardict ensembl-vep`
3. Download the reference genome
4. Download the datasets needed by VEP (see https://github.com/Ensembl/ensembl-vep)
5. Edit the *.config* file with input and output files/paths
6. Activate your conda environment
7. Run MobiCT on your Dataset
    `Nextflow -log /output_directory/my.log run MobiCT.nf -c nextflow.config`

# Pipeline output
The output files are stored in the directory you specified using the **outdir** parameter in the .config file. The **outdir** contains a folder per sample plus a **multiQC** folder. Each sample folder contains a deduplicated and aligned *.bam* file and its index, an annotated *.vcf* file, 3 metrics files (*.HsMetrics.1.txt*, *.HsMetrics.3.txt* and *QC.bcftools_stats.stats*).
