# HTSA review feedback log

Date: 2026-04-15

Scope:
- High-priority feedback only
- Keep exact highlight spans, comment text, and a short revision cue together

## 1) PCA / heatmap overstates genotype story

- Section: `Results` → `Differential Expression Analysis`
- Highlight these PCA sentences together:
  - `PC1 (46.2%) represents the primary variance driven by the response to nerve injury...`
  - `PC2 (20.6%) represents the secondary variance driven by the Ahr genotype...`
- Highlight these heatmap sentences together:
  - `The results demonstrate clear and distinct unsupervised clustering...`
  - `samples were further partitioned by genotype...`
- Comment to leave:
  - `This is a little too strong for the genotype story. Our weekly report supports side as the dominant pattern and genotype as a weaker secondary pattern, with some near-overlapping ff/cre pairs. I’d soften this so we don’t overstate genotype separation.`
- Example edit:
  - "PC1 (46.2%) primarily reflects variance associated with side (ipsilateral vs contralateral), which is the dominant pattern in the dataset. PC2 (20.6%) captures secondary variance that partly correlates with Ahr genotype; genotype separation is present but weaker and shows some overlapping FF/CRE pairs."
  - "Unsupervised clustering groups samples mainly by side (ipsilateral vs contralateral). Genotype shows partial partitioning in some pairs but does not produce a clear, uniform separation."

## 2) Bend-point paragraph must name the exact contrast

- Section: `Results` → `Differential Expression Analysis` → volcano / bend-point paragraph
- Highlight this sentence:
  - `The bend point occurred at a p-value of 1.37e-17... At this p-value, about 709 genes appeared.`
- Comment to leave:
  - `Please name the exact contrast here. The 709 genes are from ipsi_vs_contra_in_ff. Without the contrast name, the reader can confuse this with the alternate side-specific branch (ipsi_vs_contra_in_cre, 870 genes).`
- Example edit:
  - "For the ipsi_vs_contra_in_ff contrast the bend point occurred at a p-value of 1.37e-17, yielding approximately 709 genes."

## 3) GO Results should stay centered on the validated main branch

- Section: `Results` → `Gene Ontology Analysis`
- Highlight the opening GO paragraph.
- If needed, also highlight the starts of the BP, CC, and MF paragraphs.
- Comment to leave:
  - `I think this section should more clearly center the FF side-specific branch as the main validated GO story. Our strongest supported result is the FF branch, especially overlapping BP themes like signaling/regulation, migration or morphogenesis, and injury-response/development. Right now BP, CC, and MF read a bit too equally weighted.`
- Example edit:
  - "We focus the GO analysis on the FF side-specific branch (ipsi_vs_contra_in_ff), which shows the strongest and most consistent enrichment—particularly in BP terms related to signaling/regulation, migration/morphogenesis, and injury-response/development."

## 4) Some Results sentences move from observation to interpretation too fast

- Section: mostly `Gene Ontology Analysis`, secondarily `Differential Expression Analysis`
- Highlight these BP sentences:
  - `With this in mind, it makes sense for all the pathways to be connected...`
- Highlight the unfinished bracketed sentence in CC.
- Highlight the unfinished bracketed sentence in MF.
- Comment to leave:
  - `This moves a little too quickly from what the figure shows to interpretation. I’d first describe the observed pattern, then add a short interpretation. Also, the bracketed sentences need to be completed or cut.`
- Example edit:
  - "Observed: the top BP terms show overlapping gene membership across several enriched terms. Interpretation: this pattern suggests a connected program of signaling and injury response; additional validation is needed before stronger mechanistic claims are made."

## 5) QC claim overstates what trimming fixed

- Section: `Results` → `Quality Control and Trimming of RNASeq Data`
- Highlight this sentence:
  - `the dataset was trimmed to clear the adapter issues along with overrepresented sequences and sequence duplication.`
- Comment to leave:
  - `This overstates what trimming fixed. Our QC outputs strongly support that adapter-content failures were resolved, but not that overrepresented-sequence and duplication issues were fully cleared. I’d make this more precise.`
- Example edit:
  - "Trimming resolved adapter-content failures; overrepresented sequences and duplication levels were reduced but not fully eliminated, so we report the adapter fix specifically."

## 6) Comparison plots should use WT / cKO and show GO IDs

- Section: GO follow-up comparison plots in the notebook
- Update the first plot:
  - relabel the bend-point overlap figure as `WT` vs `cKO`
  - keep the gene overlap summary aligned with those labels
- Update the second plot:
  - annotate each shared GO point with the GO ID plus the term label, the same way the network graph does
  - change the axes/titles to `WT` and `cKO`
- Comment to leave:
  - `Nikhi wants the comparison plots to use more specific GO terminology than a generic label like "transport". Please show the GO IDs directly on the scatter points, and relabel the branches as WT and cKO if that fits the figure.`
- Example edit:
  - Plot 1 (overlap): Title → "Bend-point-selected gene overlap: WT vs cKO"; left label → "WT bend-point (ipsi vs contra)"; right label → "cKO bend-point (ipsi vs contra)".
  - Plot 2 (scatter): Annotate each shared point with its GO ID in bold above a short term label (truncate term to ~42 chars if needed). Axis labels → "WT upregulated GO terms: -log10(FDR)" and "cKO upregulated GO terms: -log10(FDR)".