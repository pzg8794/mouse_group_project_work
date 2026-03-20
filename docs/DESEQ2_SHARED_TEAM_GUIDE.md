# DESeq2 shared team guide

This is the short operational guide for running the mouse DESeq2 workflow on `sequoia`.

## What this is for

- differential expression analysis of the mouse count matrix
- uses `DESeq2` in a private team environment
- uses the existing count and metadata handoff from the alignment stage

## Important paths

- team DESeq2 environment:
  - `/home/pzg8794/.local/share/micromamba/envs/biol550_deseq2`
- shared input directory:
  - `/home/zebrafish/mouse/PRJNA1017789_parallel/deseq2_shared/inputs/`
- shared output directory:
  - `/home/zebrafish/mouse/PRJNA1017789_parallel/deseq2_shared/output/`
- shared wrapper:
  - `/home/zebrafish/mouse/PRJNA1017789_parallel/scripts/mouse_deseq2_shared_server_run.sh`

## Inputs expected

- `mouse_star_gene_counts_reverse_stranded.tsv`
- `mouse_alignment_sample_summary.tsv`

## Quick checks

```bash
export MAMBA_ROOT_PREFIX=/home/pzg8794/.local/share/micromamba
/home/pzg8794/.local/bin/micromamba run -n biol550_deseq2 \
  Rscript -e "suppressPackageStartupMessages(library(DESeq2)); cat('DESEQ2_OK\n')"
```

```bash
bash /home/zebrafish/mouse/PRJNA1017789_parallel/scripts/mouse_deseq2_shared_server_run.sh check
```

## Run the shared DESeq2 workflow

```bash
bash /home/zebrafish/mouse/PRJNA1017789_parallel/scripts/mouse_deseq2_shared_server_run.sh run
```

## What not to change

- do not replace the input files with a different count matrix unless the team agrees first
- do not treat the shared wrapper as the canonical analysis code
- do not casually change package versions inside the team environment

## Re-run rule

- the wrapper can stay on the server
- the long DESeq2 driver stays local as the source of truth and is copied to the server only when needed
- if the driver is removed after a run, copy it again before the next run
