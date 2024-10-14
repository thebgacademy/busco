# BUSCO

This session is part of [**Biodiversity Genomics Academy 2024**](https://thebgacademy.org/)

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/thebgacademy/busco)

[YouTube Recording](https://www.youtube.com/@thebiodiversitygenomicsacademy) <-- To be updated after BGA24

## Session Leader(s)
Matthew Berkeley - SIB, Switzerland

## Description

Introduction to BUSCO, description of the pipelines and datasets, best practices and example use cases.

## Prerequisites

1. Understanding of linux command line basics

>[!warning] "Please make sure you MEET THE PREREQUISITES and READ THE DESCRIPTION above"
>
>    You will get the most out of this session if you meet the prerequisites above.
>
>    Please also read the description carefully to see if this session is relevant to you.
>    
>    If you don't meet the prerequisites or change your mind based on the description or are no longer available at the session time, please email damon at thebgacademy.org to cancel your slot so that someone else on the waitlist might attend.


## Instructions

### Exercise 1
This exercise provides a run through of the simplest BUSCO pipeline.

Navigate to the `exercise1` directory and run BUSCO using the following commands:

```
cd /workspace/busco/exercises/exercise1
busco -i GCF_000009065.1_ASM906v1_protein.faa -m protein -l bacteria_odb10 -c 4
```

### Exercise 2
This exercise introduces the genome mode pipeline for prokaryota.

Navigate to the `exercise2` directory and run BUSCO using the following commands:

```
cd /workspace/busco/exercises/exercise2
busco -i GCF_000008865.2_ASM886v2_genomic.fna -o bacteria_genome_mode -l bacteria_odb10 -m genome -c 4
```

### Exercise 3

To test the genome mode pipelines we will use the test genome file in the busco repository.
Navigate to the `exercise3` directory, clone the repository and run BUSCO using the following commands:

```
cd /workspace/busco/exercises/exercise3
git clone https://gitlab.com/ezlab/busco.git
cp busco/test_data/eukaryota/genome.fna .
busco -i genome.fna -o miniprot_genome_pipeline -m genome -l eukaryota_odb10 -c 4
```

This will run the default Miniprot pipeline. To run again with Metaeuk and Augustus run the following:

```
busco -i genome.fna -o metaeuk_genome_pipeline -m genome -l eukaryota_odb10 -c 4 --metaeuk
busco -i genome.fna -o augustus_genome_pipeline -m genome -l eukaryota_odb10 -c 4 --augustus
```

### Exercise 4

To test the auto-lineage pipeline we will use the `--auto-lineage` command instead of the `-l` lineage dataset command.

```
cd /workspace/busco/exercises/exercise4
busco -i GCF_000008865.2_ASM886v2_genomic.fna -o autolineage_pipeline -m genome -c 4 --auto-lineage
```

### Exercise 5

It is possible to run BUSCO with a directory of input files instead of a single file.

```
cd /workspace/busco/exercises/exercise5
busco -i batch_input/ -o batch_input_pipeline -m genome -l bacteria_odb10 -c 4
```
