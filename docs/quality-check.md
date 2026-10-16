# Quality check

In order to be published on ESGF-NG, CORDEX data must pass the Quality Checker without high severity issues.
In any case, having data complying with the specifications is key to ease downstream use.
The quality control process is quite straightforward and the software can be installed in any Linux machine.

## Setting up the environment

### Starting from scratch

First, if you don't have a local working Python environment, use conda (or micromamba in the example below) to get your virtual environment. Yoo cn skip this step if you already have a working Python environment.
```bash
"${SHELL}" <(curl -L micro.mamba.pm) # Say yes to all
source ~/.bashrc
micromamba create -n cordex python=3
micromamba activate cordex
```
You should see `(cordex)` in your prompt, and you are now in an isolated working environment with python3 installed.
You can return to it any other time just by issuing: `micromamba activate cordex`.

### Installing the required tools

Now let's install some tools:

```bash
pip install esgvoc
pip install cmip7_repack
bash <(curl -L https://wcrp-cordex.github.io/ncrepack-cordex/install.sh)
pip install esgf-qa
# Configure esgvoc to use the latest versions:
esgvoc use cordex-cmip6@latest
esgvoc use universe@latest
```

## Repacking your data

It is strongly recommended to "repack" your files (a future version of the quality checker will raise a failure if data are not repacked).
The environment above includes a tool that you can use to perform this repacking.
The defaults are fine:

```bash
ncrepack-cordex -o file.nc
```

## Running the quality checker

We are ready to check our files. E.g.:

```bash
esgqa -P 4 -t wcrp_cordex_cmip6:latest -t cf:1.11 CORDEX-CMIP6/DD/AFR-12/INST/ERA5/evaluation/r1i1p1f1/RCM2/v1-r1/1hr/tas/v20261016
```

The [DKRZ QC Result Viewer](https://cmiphub.dkrz.de/info/display_qc_results.html) is a nice tool to display the json QC output files.

## Resources

- https://github.com/ESGF/esgf-qa
- https://esgf.github.io/esgf-vocab
- https://github.com/WCRP-CORDEX/ncrepack-cordex
- https://wcrp-cordex.github.io/archive-specifications/CORDEX-CMIP6_archiving_specifications_DD