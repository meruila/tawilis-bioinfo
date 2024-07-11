---
layout: default
title: Bismark
parent: Methylomics
---

# Bismark
Bismark performs bisulfite mapping alignments and methylation calls in whole genome bisulfite sequencing and reduced representation bisulfite sequencing. The reads are mapped using Bowtie2, a tool for aligning reads to a reference genome. After alignment, the software outputs several plaintext files that contain summaries of the percentage methylation of cytosines in CG, CHG, and CHH context. The software also provides a method for visualizing these outputs using plots and graphs in Plotly.  
See the [user guide](https://felixkrueger.github.io/Bismark/) and [paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3102221/).

## Genome Preparation
```bash
# Template
bismark_genome_preparation [path_to_ref_genome_directory]

# Example
bismark_genome_preparation --path_to_aligner my_path/bowtie2-2.5.1-linux-x86_64/ /my_path/Genome/Human_Genome_GRCh38.p14/ncbi_dataset/data/GCF_000001405.40_RefSeq/ 
```

**Common error**: If the file extension of the reference genome is in .fna, change file extension to .fa:
```bash
mv <file>.fna <file>.fa
```

## Alignment
```bash
# Template
bismark [path_to_ref_genome_directory] -1 [read_1] -2 [read_2]

# Example
bismark /my_path/Genome/d_rerio/ --path_to_bowtie2 /my_path/bowtie2-2.5.1-linux-x86_64 -1 /my_sequences/read_1.fq -2 /my_sequences/read_2.fq
```

## Deduplication
This is an optional step and is best for WGBS reads only.
```bash
# Template
deduplicate_bismark --paired --bam [BAM_file]

# Example
deduplicate_bismark --paired --bam /my_path/myseq_bismark_bt2_pe.bam
```

## Methylation Extraction
```bash
# Template
bismark_methylation_extractor --comprehensive --bedGraph --cytosine_report --genome_folder [path_to_ref_genome_directory] [BAM_file]

# Example
bismark_methylation_extractor --comprehensive --bedGraph --cytosine_report --genome_folder /my_path/Genome/d_rerio/ myseq_bismark_bt2_pe.deduplicated.bam
```

## Processing Report
```bash
bismark2report
```

## Summary Report
```bash
bismark2summary
```