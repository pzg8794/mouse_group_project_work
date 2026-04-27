# Source-paper RSS comparison assets

This folder supports `../source_paper_rss_comparison_shared_findings.ipynb`, a low-code educational notebook that explains how the source paper's RSS-prioritized AhR gene set was compared against the local `mouse_new` DESeq2, bend-point, and GO/pathway-level outputs.

## Contents

- `source_rss_*scatter.png`, `source_rss_bendpoint_venn_style.png`, `source_rss_membership_matrix.png`, and `source_rss_overlap_counts.png`: shareable comparison figures used in the notebook.
- `source_rss_constrained_*`: second-pass source-constrained bend-point outputs that rerun the local bend-point selection rule inside the matched source-paper RSS gene subset.
- `source_rss_*summary.tsv`, `source_rss_gene_level_comparison.tsv`, and `source_rss_go_*tsv`: tabular outputs behind the figures.
- `source_rss_comparison_summary.md`: compact source-output summary generated with the comparison outputs.

## Reading order

Open the notebook first. It explains each figure in a consistent format: method, inputs, result/output, interpretation, and biological meaning.
