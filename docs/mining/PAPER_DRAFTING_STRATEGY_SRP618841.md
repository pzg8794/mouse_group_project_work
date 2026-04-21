# Paper drafting strategy — final team guide

This guide keeps the useful parts of the earlier mind maps, but organizes them as a clearer **story-first paper-writing strategy** for a team that has not written a paper before.

The goal is to help the team move from **choosing the story** in **Draft 1** for the BIOL550 final paper.

In BIOL550, this guide maps to the course paper schedule:

- **Draft 1 / Week 13** = outline of the paper

We are using the term:

- **mind map**

---

## Main recommendation

Use a **story-first drafting strategy**.

That means the team should not organize the paper mainly around:

- the order in which analyses happened
- the history of failed and improved paths
- pipeline chronology

Instead, the team should organize the paper around:

- the **main claim** of the paper
- the **strongest evidence** supporting that claim
- the **supporting evidence** that strengthens confidence in that claim
- the **secondary results** that add context but do not lead the story

Mind maps are still useful, but they should support the paper story rather than replace it.

If needed, one mind map can sit inside another, as long as the levels stay clear:

- high-level paper map
- draft-level map
- section or story map

---

## Core rule for this team

Before writing sections, the team should agree on five things:

1. **What is the paper's main claim?**
2. **Which result is the strongest support for that claim?**
3. **Which results are support only, rather than the center of the story?**
4. **Which results are secondary and should not lead the paper?**
5. **What does Draft 1 need to accomplish?**

If those five points are clear, the paper becomes much easier to draft.

A practical rule for this team:

- write the **one-sentence main claim** early
- revise it as the draft improves
- use it to decide what stays central, supporting, secondary, or out

---

## 1) High-level mind map — from planning to Draft 1

```text
                        [ High-level planning ]
                        - define paper goal
                        - align the team
                        - agree on paper claim
                        - agree on draft roles
                                   |
                                   v
                               [ Draft 1 ]
                        - lock the main paper story
                        - choose main claim
                        - choose main results
                        - define support vs secondary results
```

### Meaning

- **High-level planning** sets the writing target before section drafting starts.
- **Draft 1** is the most important stage because it fixes the main story.
- The work order should read in the same direction as the drafting process:
  - **High-level planning -> Draft 1**

This planning layer still feeds a standard journal-style paper with the usual required sections:

- Introduction
- Materials and Methods
- Results
- Discussion
- References

The **Materials and Methods** section should describe the main analysis path clearly and only mention earlier exploratory paths when they help explain a design choice.

---

## 2) Draft 1 framework — how to build the paper story

This is the **generic Draft 1 framework**. It explains how Draft 1 should work for any project.

```text
                         [ Draft 1: build the paper story ]
                                        |
        -----------------------------------------------------------------
        |                       |                      |                 |
        v                       v                      v                 v
 [ Main claim ]         [ Strongest evidence ]  [ Supporting evidence ] [ Secondary results ]
        |                       |                      |                 |
        v                       v                      v                 v
 - one clear paper       - result family that    - data-quality and    - useful, but not the
   message                 best supports claim     analysis checks       main paper driver
 - central biological    - should lead figures     strengthen trust    - can appear later or
   or analytical signal  - should anchor the     - supporting results   in support sections
   is explicit             Results section         increase confidence - should not compete
 - story is focused      - should appear early     in the main result    with the main claim
                                        |
                                        v
                           [ Section and figure outline ]
                           - Introduction sets up the question
                           - Results lead with strongest evidence
                           - supporting analyses follow
                           - Discussion explains meaning and limits
```

### Meaning

Draft 1 should not begin with **what happened first in the project**.

Draft 1 should begin with:

- the **main claim**
- the **best evidence**
- the **supporting evidence**
- the **secondary evidence**
- the section and figure order that follows this logic

For the current DRG mouse project, this likely means a **DE-centered story** in which the **side-specific DRG signal** is central. Other projects should substitute their own main signal here.

### Checklist for Draft 1 (any project)

By the end of Draft 1, the team should have:

- one main claim written in 1 sentence
- one main family/result path locked
- 1 to 2 core figures selected
- one short statement explaining what counts as supporting evidence only
- one short statement explaining what is secondary and should not lead the paper
- one Results outline in the order the reader should encounter the story
- one short PCA interpretation that explains the dominant sample structure before gene-level claims
- one clear rule for narrowing very large significant-gene lists without relying only on an arbitrary top-N cutoff

Write the current one-sentence main claim here:

- `__________________________________________________`

---

## 3) Draft 1 application — this project

This is the **project-specific Draft 1 map**. It applies the generic Draft 1 framework above to the current mouse and DRG paper story.

```text
                           [ Draft 1 paper story for this project ]
                                              |
                 ------------------------------------------------------------------
                 |                         |                        |               |
                 v                         v                        v               v
         [ Paper goal ]          [ Main analytical path ]   [ Supporting evidence ] [ Secondary results ]
                 |                         |                        |               |
                 v                         v                        v               v
      - journal-style paper      - SRP618841 / mouse_new     - QC improved data   - geno_in_contra
      - DE-centered story        - family_drg_novaseqx       - alignment supports - geno_in_ipsi
      - strong analysis claim    - strongest usable path       DE                 - interaction
                                 - cleaner paper story       - PCA interpreted
                                                              first to confirm
                                                              side-driven structure
                                                            - processing steps
                                                              support confidence
                                              |
                                              v
                               [ Main result to center the paper ]
                               - side-specific DRG expression signal
                               - ipsi_vs_contra_in_ff
                               - ipsi_vs_contra_in_cre
                                              |
                                              v
                           [ Large DE list handling for Draft 1 ]
                           - do not rely only on arbitrary top-100 lists
                           - use p-value distribution / cumulative bend logic
                             if a principled cutoff is needed
                           - reserve GO/pathway analysis as a later interpretive
                             step after narrowing
                                              |
                                              v
                                   [ Decision: main paper center ]
                         - center the paper on the side-specific DE signal
                         - keep QC/alignment as support, not the paper's core
                         - treat genotype-related results as secondary unless they
                           become stronger than the side-specific contrasts
```

### Meaning

For this project, the cleanest Draft 1 strategy is:

- center the paper on the **side-specific DRG differential expression signal**
- use **`mouse_new` / `SRP618841`** as the main analysis path
- treat **QC and alignment** as support for trustworthiness
- treat **secondary contrasts** as additional context, not the lead story

### Decision points that should be locked by Draft 1

These should not change in later drafts unless there is a very strong new reason:

- **Decision:** `mouse_new` / `SRP618841` is the main paper path.
- **Decision:** `family_drg_novaseqx` is the main family.
- **Decision:** side-specific DRG differential expression is the primary signal.
- **Decision:** QC and alignment are support, not the paper center.

### Checklist for this project's Draft 1

By the end of Draft 1, the team should have:

- the main claim written in 1 sentence
- `ipsi_vs_contra_in_ff` and `ipsi_vs_contra_in_cre` named as the central results
- 1 to 2 hero figures selected
- a short PCA interpretation showing that side-class structure is the first thing to explain
- a short paragraph explaining why the first mouse path is not the main Results center
- a short paragraph defining what stays **supporting** vs **secondary**
- a short note explaining how very large significant-gene lists will be narrowed without using only an arbitrary cutoff

---

## Recommended use of this document

Use this shared version when:

- aligning the team on the paper story
- deciding what belongs in Draft 1
- checking whether a result is central, supporting, or secondary

Keep the later-draft expansion and more detailed local strategy documents in the local paper workspace.

## Review tracking

Active review notes and comment targets are recorded in:

- [../../group_project/mouse_new/paper/HTSA_Review_Feedback_Log.md](../../group_project/mouse_new/paper/HTSA_Review_Feedback_Log.md)

Use that log to keep the exact highlight spans, comments to leave, and revision candidates together for the current review pass.
