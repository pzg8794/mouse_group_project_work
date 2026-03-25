# Mouse DESeq2 analysis handoff

This is the simplified team-facing handoff for the current mouse differential expression setup.

## Previous handoff reference

Before using the DE command below, use the shared environment handoff here:

- `docs/DESEQ2_SHARED_TEAM_GUIDE.md`

That guide covers:

- how to activate the shared DESeq2 environment on `sequoia`
- the shared environment path
- the basic server run pattern

## What is shared here

- a notebook preview of the DE workflow:
  - `notebooks/mouse_differential_expression_team_walkthrough.ipynb`
- the subset-definition tables:
  - `data/differential_expression_all26/tables/mouse_de_design_table.tsv`
  - `data/differential_expression_all26/tables/family_manifest.tsv`
  - `data/differential_expression_all26/tables/contrast_manifest.tsv`
- the per-family sample membership tables:
  - `data/differential_expression_all26/family_tissue_novaseq6000/tables/sample_table.tsv`
  - `data/differential_expression_all26/family_tissue_sham_novaseqx/tables/sample_table.tsv`
  - `data/differential_expression_all26/family_neurons_novaseqx/tables/sample_table.tsv`

## What comes from alignment

The DE inputs were built from the canonical STAR alignment outputs.

STAR produced the raw per-sample alignment files, especially:

- `Log.final.out`
- `ReadsPerGene.out.tab`

Those raw alignment outputs were parsed in the local alignment-analysis workflow and turned into the two DE input artifacts:

- `mouse_star_gene_counts_reverse_stranded.tsv`
  - the gene-by-sample count matrix used by `DESeq2`
- `mouse_alignment_sample_summary.tsv`
  - the sample metadata table used to define sample labels, families, and contrasts

So the flow is:

- STAR alignment output
- local alignment-analysis parsing step
- count matrix + sample metadata table
- DESeq2 input

## What the subsets are

The data was organized into three DE families:

1. `family_tissue_novaseq6000`
   - tissue samples on `NovaSeq 6000`
2. `family_tissue_sham_novaseqx`
   - sham tissue samples on `NovaSeq X`
3. `family_neurons_novaseqx`
   - neuron samples on `NovaSeq X`

The subset structure is documented in:

- `data/differential_expression_all26/tables/mouse_de_design_table.tsv`
- `data/differential_expression_all26/tables/family_manifest.tsv`
- `data/differential_expression_all26/tables/contrast_manifest.tsv`

## For analysis

Core reference files:

- `mouse_de_design_table.tsv`
  - sample-to-family mapping used for DE
- `family_manifest.tsv`
  - the DE families and design formulas
- `contrast_manifest.tsv`
  - the contrasts defined inside each family
- `sample_table.tsv`
  - the samples used inside a specific family

## How DESeq2 was used

The notebook calls the R pipeline from Python, but the actual DE analysis is done inside the R script with `DESeq2`.

### DESeq2 example inside the R script

```r
library(DESeq2)

dds <- DESeqDataSetFromMatrix(
  countData = counts_matrix,
  colData = sample_table,
  design = ~ condition
)

dds <- DESeq(dds)
res <- results(dds, contrast = c("condition", "injury", "naive"))
vsd <- vst(dds, blind = FALSE)
```

Description:

- `DESeqDataSetFromMatrix(...)`
  - creates the DESeq2 dataset from counts plus sample metadata
- `countData`
  - the gene-by-sample count matrix
- `colData`
  - the sample metadata table
- `design`
  - the model formula for the family being tested
- `DESeq(dds)`
  - fits the DESeq2 model
- `results(...)`
  - extracts one contrast from that fitted model
- `vst(dds, blind = FALSE)`
  - creates transformed values for PCA and distance plots

## Environment activation before running the command

Run the shared environment activation first:

```bash
source /home/zebrafish/mouse/PRJNA1017789_parallel/scripts/mouse_deseq2_activate_shared.sh
```

## How to run the pipeline

After the environment is active, this wrapper combines the alignment-derived inputs and runs the DESeq2 pipeline with the local R script.

```bash
Rscript pipelines/mouse_deseq2_all26.R \
  --counts mouse/alignment_analysis_star_all26/tables/mouse_star_gene_counts_reverse_stranded.tsv \
  --meta mouse/alignment_analysis_star_all26/tables/mouse_alignment_sample_summary.tsv \
  --outdir mouse/differential_expression_all26
```

Description:

- `--counts`
  - input count matrix derived from STAR alignment output
- `--meta`
  - input sample metadata / design table derived from the alignment-analysis step
- `--outdir`
  - where the DE tables and figures are written

## Notebook

- `notebooks/mouse_differential_expression_team_walkthrough.ipynb`

This notebook is a simplified walkthrough that shows:

- what inputs feed the DE workflow
- how the subsets are defined
- what the family-level DE structure looks like
