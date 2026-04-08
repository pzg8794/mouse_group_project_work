# Bend-Point Tool — Simple Team Guide

This is the shared team tool for taking a differential-expression table, drawing the bend/elbow plot, and creating a new bend-point threshold.

## Tool path

- Script:
  - `/Users/pitergarcia/DataScience/Semester5/BIOL550/mouse_group_project_work/scripts/mouse_bendpoint_from_table.py`

## What data to use

Use a full differential-expression results table that has at least:
- a gene ID column
- a `pvalue` column

The easiest current inputs are the `*_full.tsv` tables from:
- `/Users/pitergarcia/DataScience/Semester5/BIOL550/mouse_group_project_work/data/differential_expression_all20/family_drg_novaseqx/tables/`

Examples:
- `/Users/pitergarcia/DataScience/Semester5/BIOL550/mouse_group_project_work/data/differential_expression_all20/family_drg_novaseqx/tables/ipsi_vs_contra_in_ff_full.tsv`
- `/Users/pitergarcia/DataScience/Semester5/BIOL550/mouse_group_project_work/data/differential_expression_all20/family_drg_novaseqx/tables/ipsi_vs_contra_in_cre_full.tsv`

These tables come from the DESeq2 differential-expression stage of the shared mouse workflow.

## What the tool makes

The tool writes 4 outputs into your output folder:
- `ordered_pvalue_and_cumulative_curve.png`
- `ordered_pvalues_with_bendpoint.tsv`
- `selected_genes_bendpoint.tsv`
- `bendpoint_summary.tsv`

## Simple run command

Run from the shared repo root:

```bash
cd /Users/pitergarcia/DataScience/Semester5/BIOL550/mouse_group_project_work
/Users/pitergarcia/DataScience/Semester5/BIOL550/biol550_env/bin/python scripts/mouse_bendpoint_from_table.py \
  --input data/differential_expression_all20/family_drg_novaseqx/tables/ipsi_vs_contra_in_ff_full.tsv \
  --outdir data/differential_expression_all20/shared_bendpoint_runs/ipsi_vs_contra_in_ff \
  --name ipsi_vs_contra_in_ff
```

## Parameter meanings

- `--input`
  - the DE results table you want to analyze
- `--outdir`
  - the folder where the plot and output tables will be saved
- `--name`
  - the label used in the plot title and summary table
- `--gene-col`
  - gene ID column name
  - default: `gene_id`
- `--p-col`
  - raw p-value column name
  - default: `pvalue`
- `--padj-col`
  - adjusted p-value column name
  - default: `padj`
- `--lfc-col`
  - log2 fold-change column name
  - default: `log2FoldChange`
- `--basemean-col`
  - base mean column name
  - default: `baseMean`
- `--sep`
  - file separator if needed
  - default: auto-detect (`tab` for `.tsv` / `.txt`, `comma` for `.csv`)

## Dummy example

If your file already has the standard DESeq2-style column names, you usually only need:

```bash
cd /Users/pitergarcia/DataScience/Semester5/BIOL550/mouse_group_project_work
/Users/pitergarcia/DataScience/Semester5/BIOL550/biol550_env/bin/python scripts/mouse_bendpoint_from_table.py \
  --input path/to/your_results_full.tsv \
  --outdir path/to/output_folder \
  --name my_contrast_name
```

## If your columns have different names

Example:

```bash
cd /Users/pitergarcia/DataScience/Semester5/BIOL550/mouse_group_project_work
/Users/pitergarcia/DataScience/Semester5/BIOL550/biol550_env/bin/python scripts/mouse_bendpoint_from_table.py \
  --input path/to/results.tsv \
  --outdir path/to/output_folder \
  --name my_contrast_name \
  --gene-col gene_symbol \
  --p-col p_value
```

## What the bend point means

The script ranks genes by p-value and finds the point with the maximum distance from the start-to-end line of the ordered curve.
That point becomes the new bend-point threshold.
Genes at or below that threshold go into `selected_genes_bendpoint.tsv`.
