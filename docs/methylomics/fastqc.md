---
layout: default
title: FastQC
parent: Tools
---

# FastQC
FastQC is a tool for checking the quality of reads. This provides an overview of the quality scores, GC content, N content, sequence length, duplication levels, overrepresented sequences, and k-mer content. The tool can give insights on what type of processing needs to be done (e.g., adapter trimming, deduplication). It is commonly used before and after the reads are processed.  
See the [project website](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/).

## Download
FastQC can be downloaded through the Babraham Bioinformatics [website](https://www.bioinformatics.babraham.ac.uk/projects/download.html#fastqc).

## Usage
```bash
fastqc [read_1] [read_2]
```