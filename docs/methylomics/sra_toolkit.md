---
layout: default
title: SRA Toolkit
parent: Tools
---

# SRA Toolkit
The SRA Toolkit is used to manipulate data from the Sequence Read Archive. The main two tools used in the project are the `prefetch` and `fasterq-dump` tools.

## Download
The SRA Toolkit can be downloaded from [GitHub](https://github.com/ncbi/sra-tools/wiki/01.-Downloading-SRA-Toolkit). Its image can be retrieved from Docker Hub ([main](https://hub.docker.com/r/ncbi/sra-tools), [mirror](https://hub.docker.com/r/staphb/sratoolkit/)).

## Usage
**prefetch**  
```bash
# Template
prefetch [SRA Accession Number]

# Example
prefetch SRR21470609
```  

For multiple sequences, you may choose to create a file containing all the SRA accession numbers separated by a new line and add the file to the command using the `--option-file` option.

```bash
prefetch --option-file sra.txt
```

**fasterq-dump**
```bash
# Template
fasterq-dump --split-files [SRA Accession Number]

# Example
fasterq-dump --split-files SRR21470609
```

Using this command, you should get one set of paired-end reads, `SRR21470609_1.fastq` and `SRR21470609_2.fastq`.  
For multiple sequences, you may create a loop in your Bash script using the text file containing the SRA accession numbers.

```bash
sratoolkit/prefetch --option-file $1
while read sra; do
	sratoolkit/fasterq-dump --split-files "$sra"
done < $1
```