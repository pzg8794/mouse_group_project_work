# DESeq2 shared team guide

This is the short operational guide for running the mouse DESeq2 workflow on `sequoia`.

## What this is for

- differential expression analysis of the mouse count matrix
- uses `DESeq2` in a private team environment
- uses the existing count and metadata handoff from the alignment stage

## Important paths

- team DESeq2 environment:
  - `/home/pzg8794/.local/share/micromamba/envs/biol550_deseq2`
- shared activation script:
  - `/home/zebrafish/mouse/PRJNA1017789_parallel/scripts/mouse_deseq2_activate_shared.sh`
- shared input directory:
  - `/home/zebrafish/mouse/PRJNA1017789_parallel/deseq2_shared/inputs/`
- shared output directory:
  - `/home/zebrafish/mouse/PRJNA1017789_parallel/deseq2_shared/output/`
- shared wrapper:
  - `/home/zebrafish/mouse/PRJNA1017789_parallel/scripts/mouse_deseq2_shared_server_run.sh`

## Activate the environment

Run this command exactly after logging into `sequoia`:

```bash
source /home/zebrafish/mouse/PRJNA1017789_parallel/scripts/mouse_deseq2_activate_shared.sh
```

If activation worked, this should print the R version without an error:

```bash
R --version | head -n 2
```

If you only want to test that `DESeq2` loads:

```bash
Rscript -e "suppressPackageStartupMessages(library(DESeq2)); cat('DESEQ2_OK\n')"
```

## Inputs expected

- `mouse_star_gene_counts_reverse_stranded.tsv`
- `mouse_alignment_sample_summary.tsv`

## If the activation script fails

```bash
export MAMBA_ROOT_PREFIX=/home/pzg8794/.local/share/micromamba
/home/pzg8794/.local/bin/micromamba run -n biol550_deseq2 \
  Rscript -e "suppressPackageStartupMessages(library(DESeq2)); cat('DESEQ2_OK\n')"
```

```bash
bash /home/zebrafish/mouse/PRJNA1017789_parallel/scripts/mouse_deseq2_shared_server_run.sh check
```

## Run the shared DESeq2 workflow

### Preferred: activate first, then run

```bash
source /home/zebrafish/mouse/PRJNA1017789_parallel/scripts/mouse_deseq2_activate_shared.sh
bash /home/zebrafish/mouse/PRJNA1017789_parallel/scripts/mouse_deseq2_shared_server_run.sh run
```

### One-command run without activation

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
