# DESeq2 shared team guide

This uses the shared team DESeq2 environment on `sequoia`.
Source the activation script first so the shell uses the correct `R` and `DESeq2`, then run the shared workflow.

## Export section

Run this exactly after logging into `sequoia`:

```bash
source /home/zebrafish/mouse/PRJNA1017789_parallel/scripts/mouse_deseq2_activate_shared.sh
```

## Run section

```bash
bash /home/zebrafish/mouse/PRJNA1017789_parallel/scripts/mouse_deseq2_shared_server_run.sh run
```
