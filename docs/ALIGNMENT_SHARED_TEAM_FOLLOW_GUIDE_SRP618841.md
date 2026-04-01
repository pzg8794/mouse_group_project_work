# Mouse alignment — shared follow guide (`SRP618841`)

Purpose:
- give the team the minimum they need to follow the alignment phase
- show where the shared reference, inputs, logs, and outputs live
- reduce repeated questions about what to run and what not to touch

## Short version

The cleanup decision is already made:
- use the `fastp` outputs as the alignment inputs

This is not a new workflow.

The pipeline theme is simple:
- we reused the same core alignment logic as the main mouse workflow
- then adapted the paths and output structure for the `SRP618841` dataset

So for `SRP618841`, we are still doing the same core alignment steps:
- choose the reference
- build the STAR index
- point STAR at the cleaned paired-end FASTQs
- write sorted BAM outputs
- collect the alignment logs and gene-count tables

The alignment shared workspace is:
- `/home/zebrafish/mouse/SRP618841_parallel/`

## What the team will get in the shared tree

### Shared trimmed inputs
- `/home/zebrafish/mouse/SRP618841_parallel/qc_remediation/fastp/out/`

Expected naming:
- mate 1: `SRR*_1.fastp.fastq.gz`
- mate 2: `SRR*_2.fastp.fastq.gz`

### Shared reference bundle
- `/home/zebrafish/mouse/SRP618841_parallel/reference/grcm39_ensembl/`

This shared reference bundle contains:
- the chosen mouse FASTA
- the matching Ensembl GTF
- the STAR index
- reference metadata

### Shared alignment outputs
- `/home/zebrafish/mouse/SRP618841_parallel/alignment/star_grcm39_ensembl_all20_fastp/`

### Shared logs
- `/home/zebrafish/mouse/SRP618841_parallel/alignment/star_grcm39_ensembl_all20_fastp/logs/`

## What is the reference choice?

Chosen reference pair:
- assembly: `GRCm39`
- annotation: matching `Ensembl` GTF

Reason:
- modern mouse assembly
- matching annotation set
- one consistent reference/index for the full alignment

## What the pipeline does

In simple terms, the pipeline does the same steps as the main mouse alignment, just on the `SRP618841` dataset and with the cleaned `fastp` files:

1. choose one reference genome + matching annotation
2. build one STAR index from that reference
3. read the paired-end trimmed FASTQ files
4. align each sample to the mouse genome
5. write one sorted BAM per sample
6. write the STAR logs and gene-count tables
7. keep all outputs in one organized alignment folder

## Main launcher command

The shared run is launched with:

```bash
bash /home/pzg8794/pipelines/srp618841_star_launch.sh
```

## What STAR is doing underneath

At the per-sample level, STAR is reading:
- mate 1 trimmed reads
- mate 2 trimmed reads

and writing:
- a sorted BAM
- `Log.final.out`
- `ReadsPerGene.out.tab`

So when someone asks “what did the pipeline actually do?”, the short answer is:
- it aligned the cleaned paired-end mouse reads to `GRCm39` with STAR and saved the standard alignment outputs

## Current status

Current status:
- `fastp` is the chosen cleanup stage
- alignment outputs are available under the shared tree
- the alignment completion marker is:
  - `/home/zebrafish/mouse/SRP618841_parallel/alignment/star_grcm39_ensembl_all20_fastp/all20_fastp_alignment.completed`

## If you want the fuller explanation

Related local docs in this repo:
- `Semester5/BIOL550/group_project/mouse_new/SRP618841_PROCESS_fastq_fastqc_fastp.md`
- `Semester5/BIOL550/group_project/mouse_new/TODO_srp618841.md`
