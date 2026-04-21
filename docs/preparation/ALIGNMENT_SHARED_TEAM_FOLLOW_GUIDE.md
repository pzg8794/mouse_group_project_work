# Mouse alignment — shared follow guide

Purpose:
- give the team the minimum they need to follow the alignment phase
- show where the shared reference, index, inputs, logs, and outputs live
- reduce repeated questions about what to run and what not to touch

## Short version

The cleanup decision is already made:
- use the `fastp` outputs as the alignment inputs

This is not a new workflow.

The pipeline theme is simple:
- we first built the workflow around the Trampnell-style analysis
- then we adjusted that same pipeline structure for the mouse dataset

So for mouse, we are reusing the same core alignment logic:
- choose the reference
- build the STAR index
- point STAR at the cleaned paired-end FASTQs
- write sorted BAM outputs
- collect the alignment logs and gene-count tables

In other words, this is the Trampnell-style pipeline adapted to mouse, not a completely different alignment process.

The alignment is being done in two places:
- canonical workspace: `/home/pzg8794/mouse_qc_remediation/`
- shared workspace: `/home/zebrafish/mouse/PRJNA1017789_parallel/`

The shared run is chained to start automatically after the canonical run finishes.

## What the team will get in the shared tree

### Shared trimmed inputs
- `/home/zebrafish/mouse/PRJNA1017789_parallel/fastp_out/`

Expected naming:
- mate 1: `SRR*_1.trim.fastq.gz`
- mate 2: `SRR*_2.trim.fastq.gz`

### Shared reference bundle
- `/home/zebrafish/mouse/PRJNA1017789_parallel/reference/grcm39_ensembl/`

This shared reference bundle will contain:
- the chosen mouse FASTA
- the matching Ensembl GTF
- the STAR index
- reference metadata

### Shared alignment outputs
- `/home/zebrafish/mouse/PRJNA1017789_parallel/alignment/star_grcm39_ensembl_all26_fastp/`

### Shared logs
- `/home/zebrafish/mouse/PRJNA1017789_parallel/logs/`

## What is the reference choice?

Chosen reference pair:
- assembly: `GRCm39`
- annotation: matching `Ensembl` GTF

Reason:
- modern mouse assembly
- matching annotation set
- one consistent reference/index for the full alignment

## How the shared run starts

The shared run waits for this completion flag:
- `/home/pzg8794/mouse_qc_remediation/alignment/star_grcm39_ensembl_all26_fastp/all26_fastp_alignment.completed`

Once that file exists, the shared launcher will:
1. copy the finished reference/index bundle into the shared tree
2. write the shared metadata files
3. start the shared STAR alignment

## What the pipeline does

In simple terms, the pipeline does the same steps as the Trampnell analysis, just on the mouse dataset and with the cleaned `fastp` files:

1. choose one reference genome + matching annotation
2. build one STAR index from that reference
3. read the paired-end trimmed FASTQ files
4. align each sample to the mouse genome
5. write one sorted BAM per sample
6. write the STAR logs and gene-count tables
7. keep all outputs in one organized alignment folder

So the technical flow is not new. The main changes are the mouse reference, the mouse cleaned-input files, and the output paths.

## Main launcher command

The canonical run is launched from the orchestration script:

```bash
bash /home/pzg8794/mouse_qc_remediation/scripts/mouse_run_star_all26_fastp_parallel.sh
```

That top-level script handles the same core pieces we used before:
- reference preparation
- STAR index generation
- sample-level STAR alignment
- organized output/log writing

## Direct STAR commands

These are the command-level equivalents of the Trampnell assignment steps.

## Trapnell assignment equivalence

The assignment structure was:
- build the STAR index
- align the reads with STAR

Our mouse pipeline uses the same two STAR stages.

### Assignment step → mouse equivalent

- Trapnell assignment:
  - `STAR --runMode genomeGenerate ...`
- Mouse pipeline equivalent:
  - build the index with:
    - `/usr/local/bin/STAR/STAR --runMode genomeGenerate ...`

- Trapnell assignment:
  - `STAR --genomeDir <index> --readFilesIn <reads> ...`
- Mouse pipeline equivalent:
  - align each mouse sample with:
    - `/usr/local/bin/STAR/STAR --genomeDir /home/pzg8794/mouse_qc_remediation/reference/grcm39_ensembl/star_index_sjdb150 --readFilesIn ...`

So when we say this follows the Trampnell-style analysis, the equivalence is direct:
- same STAR index-building step
- same STAR alignment step
- different organism, reference files, cleaned inputs, and output locations

### Step 1 — build the STAR index

This is the same idea as the Trapnell assignment command:

```bash
/usr/local/bin/STAR/STAR \
  --runMode genomeGenerate \
  --runThreadN 12 \
  --genomeDir /home/pzg8794/mouse_qc_remediation/reference/grcm39_ensembl/star_index_sjdb150 \
  --genomeFastaFiles /home/pzg8794/mouse_qc_remediation/reference/grcm39_ensembl/dna/Mus_musculus.GRCm39.dna.primary_assembly.fa \
  --sjdbGTFfile /home/pzg8794/mouse_qc_remediation/reference/grcm39_ensembl/gtf/Mus_musculus.GRCm39.115.gtf \
  --sjdbOverhang 150 \
  --limitGenomeGenerateRAM 48000000000
```

### Step 2 — align one paired-end sample

This is the same idea as the Trapnell assignment alignment command:

```bash
/usr/local/bin/STAR/STAR \
  --runThreadN 4 \
  --genomeDir /home/pzg8794/mouse_qc_remediation/reference/grcm39_ensembl/star_index_sjdb150 \
  --readFilesIn \
    /home/pzg8794/mouse_qc_remediation/output/fastp/out/SRR30333743_1.fastp.fastq.gz \
    /home/pzg8794/mouse_qc_remediation/output/fastp/out/SRR30333743_2.fastp.fastq.gz \
  --readFilesCommand zcat \
  --twopassMode Basic \
  --quantMode GeneCounts \
  --outSAMtype BAM SortedByCoordinate \
  --outFileNamePrefix /home/pzg8794/mouse_qc_remediation/alignment/star_grcm39_ensembl_all26_fastp/samples/SRR30333743/SRR30333743. \
  --outTmpDir /home/pzg8794/mouse_qc_remediation/alignment/star_grcm39_ensembl_all26_fastp/samples/SRR30333743/_star_tmp
```

### What changed from the assignment version

The command structure is the same. The practical adjustments are:
- mouse reference instead of the class example reference
- cleaned `fastp` inputs instead of raw reads
- sorted BAM output
- `GeneCounts` output turned on
- organized per-sample output folders

So the command pattern is still the Trampnell-style STAR workflow. It is just adapted to the mouse project paths.

## What STAR is doing underneath

At the per-sample level, STAR is reading:
- mate 1 trimmed reads
- mate 2 trimmed reads

and writing:
- a sorted BAM
- `Log.final.out`
- `ReadsPerGene.out.tab`

So when someone asks “what did the pipeline actually do?”, the short answer is:
- it aligned the cleaned paired-end mouse reads to `GRCm39` with STAR and saved the standard alignment outputs

## Current status

Current status:
- `fastp` is the chosen cleanup stage
- canonical alignment is the first run
- shared alignment is queued to start automatically after the canonical run finishes

## If you want the fuller explanation

Related public docs in this repo:
- `GC_WARN_and_Shared_MultiQC_Followup_2026-03-17.md`
