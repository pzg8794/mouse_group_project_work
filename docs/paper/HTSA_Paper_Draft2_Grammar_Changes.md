# HTSA Paper Draft 2 — Grammar & Inconsistency Change Log

**Course:** BIOL550 | **Prepared by:** Piter Garcia (via review pass)  
**Date:** April 15, 2026  
**Purpose:** Documents every grammar fix, punctuation correction, and wording inconsistency found between the Original PDF (`HTSA_Paper_Original.pdf`) and the working `.tex` file (`HTSA_Paper.tex`). **No content was added or removed — only grammar, punctuation, and consistency corrections are listed here.**

---

## How to Read This Log

- **Location:** Section and paragraph where the issue appears.
- **Original (PDF):** Exact wording from the source PDF.
- **Fixed (.tex):** Corrected wording used in the `.tex`.
- **Issue type:** Grammar | Punctuation | Consistency | Run-on | Fragment

---

## Introduction

### 1. Run-on / Fragment — Opening paragraph

| | Text |
|---|---|
| **Original** | "Furthermore, some of the most detrimental types of injuries humans experience are of the neurological nature. Thus, research that aims to further the field of neurology and patient recovery is of the utmost importance." |
| **Fixed** | No change to wording; sentence retained as-is. Fragment flagged: "To understand the mechanism that balances the stress response and regenerative demands of neurons once injured." — this is a sentence fragment with no main clause. |
| **Issue** | Fragment — missing main verb/clause |

---

### 2. Fragment — AhR stress paragraph

| | Text |
|---|---|
| **Original** | "Establishing AhR as a functionally entirely separate network driven by HIF-1α, Bmal1, and stress-response TFs like ATF4 and ATF6." |
| **Fixed** | Should begin: "This established AhR as a functionally entirely separate network…" |
| **Issue** | Dangling participial phrase / sentence fragment — no subject or finite verb |

---

### 3. Comma splice / run-on — cKO model sentence

| | Text |
|---|---|
| **Original** | "The main study we looked at; its goal to identify the role of AhR." |
| **Fixed** | "The main study we examined had the goal of identifying the role of AhR." |
| **Issue** | Semicolon misuse; incomplete predicate |

---

### 4. Redundant phrasing — goals paragraph

| | Text |
|---|---|
| **Original** | "Firstly, we wanted to reproduce the study's findings, specifically the DEGs. Even though the study used response-shift scores (RSS) as a filter for DEGs, we did a global differential expression analysis on the genes and identified 709 statistically significant genes. Secondly, we want to cross-reference these genes…" |
| **Fixed** | Tense inconsistency: "we wanted" (past) vs. "we want" (present) — both should be past tense: "we wanted to cross-reference." |
| **Issue** | Tense shift (past → present within same paragraph) |

---

### 5. Awkward phrasing — RSS filter sentence

| | Text |
|---|---|
| **Original** | "We use the paper as a guide to understanding what biological processes are happening and how they differ from our global DE approach. With their data specifically looking at genes correlated to AhR(RSS filter), we can compare them to the global level...." |
| **Fixed** | Missing space before parenthesis: "AhR(RSS filter)" → "AhR (RSS filter)"; trailing ellipsis ("....") should be removed or replaced with a period. |
| **Issue** | Punctuation — missing space, trailing ellipsis |

---

### 6. Tense consistency — closing intro paragraph

| | Text |
|---|---|
| **Original** | "Keeping our goals for the paper in mind, we were able to complete the basic steps of RNASeq analysis… We also conducted a thorough differential expression analysis… Beyond differential expression, we were able to conduct a gene ontology analysis…" |
| **Note** | Tense is consistently past here — correct. However, the jump between present tense in the preceding paragraph ("we use," "we can compare") and past tense here is jarring. The entire introduction should settle on one tense (past is preferred for scientific writing). |
| **Issue** | Tense inconsistency across intro paragraphs |

---

## Materials and Methods

### 7. Figure caption incomplete

| | Text |
|---|---|
| **Original** | "Figure 1. Overview ribbon summarizing the four computational stages and their stage in the mouse" |
| **Fixed** | Caption is cut off — missing "workflow" or similar ending word. Should read: "Overview ribbon summarizing the four computational stages and their stage-owned handoffs in the mouse\_new workflow." |
| **Issue** | Incomplete sentence in figure caption |

---

### 8. Table caption inconsistency

| | Text |
|---|---|
| **Original (PDF)** | "Table 2. Representative command examples for the tools used in the mouse\_new" |
| **Fixed (.tex)** | "Representative command examples for the tools used in the mouse\_new workflow." |
| **Issue** | Caption was cut off in the PDF; `.tex` correctly completes it — no further action needed |

---

### 9. Abbreviation expansion inconsistency — "fastp"

| | Text |
|---|---|
| **Original** | "fastp v0.23.2" (Materials and Methods) vs. just "fastp" elsewhere |
| **Note** | Version number only appears once; it should appear on first use of the tool in Methods and not be repeated. Already handled correctly in the `.tex`. |
| **Issue** | Minor — no change needed; flagged for awareness |

---

### 10. Passive voice overuse — Preparation subsection

| | Text |
|---|---|
| **Original** | "Reverse-stranded counts (column 4 of each ReadsPerGene.out.tab file) were used as the input for downstream DESeq2 modeling, consistent with the strandedness assumption used in the project workflow." |
| **Note** | Passive is acceptable in Methods; no change. Flagged because the sentence that follows ("Treating alignment review…") abruptly switches to a gerund construction. Could be unified as: "Treating alignment review and count-matrix assembly as explicit handoffs also made the preparation stage reusable across candidate datasets." |
| **Issue** | Stylistic inconsistency — no mandatory change |

---

## Results

### 11. Figure caption phrasing — QC figure

| | Text |
|---|---|
| **Original** | "Figure X. Plots displaying adapter content present in the RNASeq samples pre-trim (A) and post-trim (B). The plots demonstrate the percentage of sequences that have the adapter content due to RNASeq steps, where the post-trim plot has significantly less adapter content present." |
| **Fixed** | "The plots demonstrate the percentage of sequences **with** adapter content…" (remove "that have"); "…where the post-trim plot **shows** significantly less adapter content." ("has…present" is redundant) |
| **Issue** | Redundant phrasing; awkward verb choice |

---

### 12. "Fig.XA" notation inconsistency

| | Text |
|---|---|
| **Original** | Uses "Fig.XA", "Fig.XB", "Fig. X", "(Fig.XA.1)", "(Fig.XB.2)" — inconsistent spacing and format throughout Results |
| **Fixed** | Should be uniform: "(Fig. X, Panel A)", "(Fig. X, Panel B)", etc., OR use the LaTeX cross-reference system (\ref{}) — the latter is preferred since the document is in LaTeX |
| **Issue** | Citation/reference format inconsistency |

---

### 13. Spelling — "Melansome"

| | Text |
|---|---|
| **Original** | "The most enriched term was Melansome" |
| **Fixed** | "The most enriched term was **Melanosome**" |
| **Issue** | Spelling error |

---

### 14. Repeated word — MF paragraph

| | Text |
|---|---|
| **Original** | "The molecular function (MF) component analysis contained the least consistency, compared to BP and CC." |
| **Note** | "The molecular function (MF)  component" has two spaces before "component" — typographic error |
| **Issue** | Extra whitespace / typo |

---

### 15. Lowercase after period — MF paragraph

| | Text |
|---|---|
| **Original** | "These genes are more correlated with the binding of molecules...." |
| **Fixed** | Remove trailing ellipsis; end with a period. "These genes are more correlated with the binding of molecules." |
| **Issue** | Trailing ellipsis used as a period; implies unfinished thought when the paragraph is complete |

---

## Discussion

### 16. Duplicate `\begin{piterpara}` — Discussion opening

| | Text |
|---|---|
| **Original (.tex)** | `\begin{piterpara}` appears **twice in a row** at the start of the Discussion section (nested incorrectly) |
| **Fixed** | Remove the duplicate opening tag — only one `\begin{piterpara}` should wrap the first Discussion paragraph |
| **Issue** | LaTeX structural error — duplicate environment opening |

---

### 17. Tense shift — Discussion paragraph 2

| | Text |
|---|---|
| **Original** | "The secondary branches show that genotype effects are not absent, but they do not displace the side-specific injury signal as the main story." |
| **Fixed** | Acceptable in present tense for a discussion claim; however, the surrounding sentences use past tense ("the analysis converged," "genotype behaved"). Suggest: "The secondary branches **showed** that genotype effects were not absent, but did not displace the side-specific injury signal as the main story." |
| **Issue** | Tense inconsistency within paragraph |

---

### 18. Word choice — "centerpiece"

| | Text |
|---|---|
| **Original** | "That convergence made the WT branch the strongest biological centerpiece for the Discussion." |
| **Fixed** | "…the strongest biological centerpiece **of** the Discussion." (preposition) — or rephrase to "…the primary focus of the Discussion." |
| **Issue** | Minor preposition / word choice issue |

---

### 19. Missing Oxford comma

| | Text |
|---|---|
| **Original** | "GO redundancy can make the functional signal look broader than it really is when overlapping labels are counted as if they were independent findings. Second, the pathway summaries are only persuasive here because they were interpreted after the PCA-first and bend-point-guided narrowing steps. Third, branch prioritization in this project reflects consistency, interpretability, and alignment with the visible sample structure" |
| **Note** | Oxford comma is present in item 3 ("consistency, interpretability, **and** alignment") — consistent with rest of paper. No change needed. |
| **Issue** | No issue — flagged and confirmed correct |

---

## Cross-Cutting Issues

### 20. "RNASeq" vs. "RNA-seq" inconsistency

| | Text |
|---|---|
| **Original** | Uses "RNASeq" (no hyphen) in figure captions and Results text; uses "RNA-seq" (hyphenated) in Methods text |
| **Fixed** | Standardize to **"RNA-seq"** throughout (hyphenated lowercase is the current field standard) |
| **Issue** | Terminology inconsistency — affects Introduction, Results section headings, and figure captions |

---

### 21. "wildtype" vs. "wild-type" vs. "WT"

| | Text |
|---|---|
| **Original** | Uses "wildtype" (one word), "wild-type" (hyphenated), and "WT" interchangeably across sections |
| **Fixed** | Standardize to **"wild-type"** (hyphenated adjective) on first use per section, then abbreviate as **"WT"** |
| **Issue** | Terminology inconsistency |

---

### 22. "cKO" vs. "Ahr cKO" vs. "AhR cKO" vs. "conditional knockout"

| | Text |
|---|---|
| **Original** | Uses "cKO", "Ahr cKO", "AhR cKO", and "conditional knockout" inconsistently |
| **Fixed** | Standardize to **"AhR cKO"** (capital H, capital R) on first full use per section; abbreviate as **"cKO"** thereafter; define fully on first mention in Abstract/Introduction |
| **Issue** | Capitalization and terminology inconsistency |

---

### 23. "g:Profiler" vs. "gProfiler" vs. "g:profiler"

| | Text |
|---|---|
| **Original** | Mostly correct ("g:Profiler") but one inline hyperlink in the `.md` source uses an incorrect format |
| **Fixed** | Always use **"g:Profiler"** (lowercase g, colon, capital P) — this matches the tool's official branding |
| **Issue** | Capitalization inconsistency |

---

### 24. Hyphenation — compound modifiers

| | Text |
|---|---|
| **Original** | "paired end" (no hyphen), "bend point" (no hyphen), "side specific" (no hyphen) used as adjectives |
| **Fixed** | Compound modifiers before nouns must be hyphenated: "paired-end libraries," "bend-point threshold," "side-specific contrasts" |
| **Issue** | Missing hyphens in compound adjectives — appears ~8 times across the document |

---

### 25. Parenthetical citation style — References section note

| | Text |
|---|---|
| **Original (PDF)** | "Intro sources: The Dorsal Root Ganglion as a Novel Neuromodulatory Target… publication + ref 20 in publication." |
| **Note** | This note-style reference stub should be replaced with a proper `\parencite{}` entry in the `.bib` file. The `.tex` currently uses `\parencite{halawani2023ahr}` for the main study but the DRG neuromodulatory target paper (the one that motivated the study) needs its own `.bib` entry and inline citation in the Introduction. |
| **Issue** | Incomplete citation — missing `.bib` entry for the DRG neuromodulatory target paper |

---

## Summary Table

| # | Location | Issue Type | Priority |
|---|---|---|---|
| 1 | Intro §1 | Fragment ("To understand the mechanism…") | **High** |
| 2 | Intro §3 | Fragment ("Establishing AhR as…") | **High** |
| 3 | Intro §2 | Semicolon misuse / incomplete predicate | **High** |
| 4 | Intro §5 | Tense shift (wanted → want) | **High** |
| 5 | Intro §5 | Missing space before parenthesis; trailing ellipsis | Medium |
| 6 | Intro (cross-para) | Tense inconsistency present vs. past | **High** |
| 7 | M&M Fig.1 caption | Incomplete sentence | Medium |
| 8 | M&M Table 2 | Caption cut off in PDF (fixed in .tex) | Low |
| 9 | M&M | Version number usage | Low |
| 10 | M&M Prep | Passive/gerund style inconsistency | Low |
| 11 | Results QC caption | Redundant phrasing | Medium |
| 12 | Results (all) | Fig.XA/Fig. X notation inconsistency | **High** |
| 13 | Results GOA | Spelling: "Melansome" → "Melanosome" | **High** |
| 14 | Results GOA | Double space before "component" | Low |
| 15 | Results GOA | Trailing ellipsis instead of period | Medium |
| 16 | Discussion | Duplicate `\begin{piterpara}` LaTeX tag | **High** |
| 17 | Discussion §2 | Tense shift | Medium |
| 18 | Discussion §4 | Preposition: "for" → "of" | Low |
| 19 | Discussion §5 | Oxford comma (confirmed correct) | — |
| 20 | Cross-cutting | "RNASeq" vs. "RNA-seq" | **High** |
| 21 | Cross-cutting | "wildtype" / "wild-type" / "WT" | **High** |
| 22 | Cross-cutting | "cKO" / "Ahr cKO" / "AhR cKO" | **High** |
| 23 | Cross-cutting | "g:Profiler" capitalization | Medium |
| 24 | Cross-cutting | Missing hyphens in compound adjectives | **High** |
| 25 | References | Missing `.bib` entry for DRG neuromodulatory target paper | **High** |

---

*This log was generated during the Draft 2 revision pass on April 15, 2026. All changes are grammar/style only — no biological content was altered.*
