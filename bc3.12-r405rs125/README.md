# Rstudio server with RNA-seq DE analysis package(s)

This container was build based on [nickjer/singularity-rstudio:3.6.2](https://github.com/nickjer/singularity-rstudio) (Modified r-base version to 4.0.5).


## Packages included

- ballgown
- DESeq2
- EBSeq
- edgeR
- polyester
- sleuth
- tximport



## Build

```bash
sudo singularity build rstudio-rnaseqde.sif Singularity
```



## Usage

1. Set password

```bash
echo 'export RSTUDIO_PASSWORD=XXXXXXXX' >> $HOME/.bashrc
```

2. Run Rstudio server

   (a) Run on localhost

    ```bash
    RSTUDIO_PASSWORD=${RSTUDIO_PASSWORD} singularity run rstudio-rnaseqde.sif \
    --auth-none 0 \
    --auth-pam-helper rstudio_auth \
    --www-port 8787
    ```
   (b) Run on NIG supercomputer

   @NIG supercomputer (login node)

   ```bash
    RSTUDIO_PASSWORD=${RSTUDIO_PASSWORD} singularity run rstudio-rnaseqde.sif \
    --auth-none 0 \
    --auth-pam-helper rstudio_auth \
    --www-port 58787 # MUST specify an unused port
   ```
   @localhost

   ```{bash}
   ssh -fNL 8787:${hostname}:58787 ${user}@gw.ddbj.nig.ac.jp
   ```

3. Open [https:/localhost:8787]([https:/localhost:8787])

4. Enter execution user ID and `RSTUDIO_PASSWORD`

