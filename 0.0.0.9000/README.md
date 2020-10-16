# Rstudio server with RNA-seq DE analysis packages

This container was build based on [nickjer/singularity-rstudio:3.6.2](https://github.com/nickjer/singularity-rstudio).


## Packages included

- ballgown
- DESeq2
- EBSeq
- polyester
- sleuth
- tximport



## Build

```bash
sudo singularity build singularity-rstudio-rnaseqde.simg Singularity
```



## Usage

1. Set password

```bash
export RSTUDIO_PASSWORD=XXXXXXXX
```

2. Run Rstudio server

   (a) Run on localhost

    ```bash
    RSTUDIO_PASSWORD=${RSTUDIO_PASSWORD} singularity run singularity-rstudio-rnaseqde.simg \
    --auth-none 0 \
    --auth-pam-helper rstudio_auth
    --www-port 8787
    ```
   (b) Run on NIG supercomputer

   @NIG supercomputer (login node)

   ```bash
    RSTUDIO_PASSWORD=${RSTUDIO_PASSWORD} singularity run singularity-rstudio-rnaseqde.simg \
    --auth-none 0 \
    --auth-pam-helper rstudio_auth
    --www-port 58787 # MUST specify an unused port
   ```
   @localhost
   ```{bash}
   ssh -fNL 8787:${hostname}:58787 ${user}@gw.ddbj.nig.ac.jp
   ```

3. Open [https:/localhost:8787]([https:/localhost:8787])

4. Enter Execution user and `RSTUDIO_PASSWORD`

