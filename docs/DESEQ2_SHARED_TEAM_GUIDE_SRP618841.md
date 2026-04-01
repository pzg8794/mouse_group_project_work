# DESeq2 shared team guide — `SRP618841`

This is the short operational guide for running the `mouse_new` DESeq2 workflow on `sequoia`.

## What this is for

- differential expression analysis of the `SRP618841` count matrix
- uses `DESeq2` in the private team environment
- uses the existing count and metadata handoff from the alignment stage

## Important paths

- team DESeq2 environment:
  - `/home/zebrafish/mouse/PRJNA1017789_parallel/.local/share/micromamba/envs/biol550_deseq2`
- shared input directory:
  - `/home/zebrafish/mouse/SRP618841_parallel/deseq2_shared/inputs/`
- shared output directory:
  - `/home/zebrafish/mouse/SRP618841_parallel/differential_expression_all20/`
- server-side DE driver copy:
  - `/home/pzg8794/pipelines/mouse_deseq2_all20.R`

## Export section — activate the environment here

Run this exactly after logging into `sequoia` to activate the team DESeq2 environment:

```bash
export MAMBA_ROOT_PREFIX=/home/zebrafish/mouse/PRJNA1017789_parallel/.local/share/micromamba
eval "$(/home/zebrafish/mouse/PRJNA1017789_parallel/.local/bin/micromamba shell hook -s bash)"
micromamba activate biol550_deseq2
```

## Inputs expected

- `mouse_star_gene_counts_reverse_stranded.tsv`
- `mouse_alignment_sample_summary.tsv`

## Run section

```bash
export MAMBA_ROOT_PREFIX=/home/zebrafish/mouse/PRJNA1017789_parallel/.local/share/micromamba
eval "$(/home/zebrafish/mouse/PRJNA1017789_parallel/.local/bin/micromamba shell hook -s bash)"
micromamba activate biol550_deseq2

Rscript /home/pzg8794/pipelines/mouse_deseq2_all20.R \
  --counts /home/zebrafish/mouse/SRP618841_parallel/deseq2_shared/inputs/mouse_star_gene_counts_reverse_stranded.tsv \
  --meta /home/zebrafish/mouse/SRP618841_parallel/deseq2_shared/inputs/mouse_alignment_sample_summary.tsv \
  --outdir /home/zebrafish/mouse/SRP618841_parallel/differential_expression_all20
```

## Output structure

- root output:
  - `/home/zebrafish/mouse/SRP618841_parallel/differential_expression_all20/`
- shared summary tables:
  - `/home/zebrafish/mouse/SRP618841_parallel/differential_expression_all20/tables/`
- family-level output:
  - `/home/zebrafish/mouse/SRP618841_parallel/differential_expression_all20/family_drg_novaseqx/`
- family figures:
  - `/home/zebrafish/mouse/SRP618841_parallel/differential_expression_all20/family_drg_novaseqx/figures/`
- family result tables:
  - `/home/zebrafish/mouse/SRP618841_parallel/differential_expression_all20/family_drg_novaseqx/tables/`

## What the names mean

- `differential_expression_all20`
  - DE output package for the `20`-sample `SRP618841` dataset
- `tables/contrast_manifest.tsv`
  - top-level summary of every contrast that was run
- `tables/family_manifest.tsv`
  - summary of the family or families included in the DE run
- `tables/mouse_de_design_table.tsv`
  - the sample design table used for DESeq2
- `family_drg_novaseqx`
  - the single DE family in this dataset
  - `drg` = dorsal root ganglion tissue family
  - `novaseqx` = `NovaSeq X` platform family
- `geno_in_contra`
  - genotype effect in contralateral DRG
- `geno_in_ipsi`
  - genotype effect in ipsilateral DRG
- `ipsi_vs_contra_in_ff`
  - side effect inside the `FF` genotype group
- `ipsi_vs_contra_in_cre`
  - side effect inside the `CRE` genotype group
- `interaction`
  - genotype-by-side interaction term
- `_full.tsv`
  - full DESeq2 result table for that contrast
- `_significant.tsv`
  - significant genes only
- `_top_genes.tsv`
  - short top-gene summary table
- `_volcano.png`
  - volcano plot for that contrast
- `_ma.png`
  - MA plot for that contrast
- `_heatmap.png`
  - top-gene heatmap for that contrast

## What not to change

- do not replace the input files with a different count matrix unless the team agrees first
- do not treat the server-side driver copy as the canonical analysis code
- do not casually change package versions inside the team environment

## Re-run rule

- the long DESeq2 driver stays local as the source of truth and is copied to the server only when needed
- the shared output directory for this dataset is:
  - `/home/zebrafish/mouse/SRP618841_parallel/differential_expression_all20/`
- keep the output tree group-accessible for the team
