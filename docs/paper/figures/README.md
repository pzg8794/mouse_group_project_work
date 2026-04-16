# Figures

This directory contains all figure source files and exports for the HTSA paper.

## Pipeline Diagram

| File | Format | Purpose |
|---|---|---|
| `biol550_pipeline.drawio` | draw.io XML | Editable source — open at [app.diagrams.net](https://app.diagrams.net) |
| `pipeline_figure.pdf` | PDF (to be added) | Export from draw.io for LaTeX `\includegraphics` |

## How to export for LaTeX

1. Open `biol550_pipeline.drawio` at [app.diagrams.net](https://app.diagrams.net)
2. **File → Export as → PDF** (vector quality)
3. Save as `pipeline_figure.pdf` in this directory
4. In the `.tex` file, reference with:

```latex
\begin{figure}[htbp]
\centering
\includegraphics[width=\linewidth]{figures/pipeline_figure.pdf}
\caption{Modular four-stage RNA-seq analysis pipeline. Each stage operates as a
standalone, reusable module with defined inputs, tools, and checkpoint artifacts.
\textit{Data Collection} retrieves SRA runs in parallel and records a design-aware
manifest. \textit{Data Cleaning} applies adapter and quality trimming with fastp and
FastX-toolkit, followed by semi-automated per-sample validation. \textit{Data Preparation}
aligns reads to GRCm39/Ensembl 115 in three steps: reference selection, STAR index
build (sjdbOverhang\,=\,150), and strand-specific alignment with GeneCounts.
\textit{Data Analysis \& Interpretation} applies a side-by-genotype DESeq2 interaction
model, bend-point follow-up selection, and g:Profiler GO/KEGG/Reactome enrichment
with shared-gene redundancy reduction. Dashed badges denote checkpoint metrics
recorded at each stage transition.}
\label{fig:pipeline}
\end{figure}
```
