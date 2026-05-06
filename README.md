# MetaResist

[![Snakemake](https://img.shields.io/badge/snakemake-≥9.0-brightgreen.svg)](https://snakemake.github.io)

Pipeline for resistome analysis and AMR prediction from metagenomic sequencing data.

## Usage

### Step 1: Install Snakemake

Snakemake is best installed via the [Mamba package manager](https://github.com/mamba-org/mamba) (a drop-in replacement for conda). If you have neither Conda nor Mamba, it can be installed via [Mambaforge](https://github.com/conda-forge/miniforge#mambaforge). For other options see [here](https://github.com/mamba-org/mamba).

Given that Mamba is installed, run

```sh
    mamba create -c conda-forge -c bioconda --name snakemake snakemake
```

to install Snakemake in an isolated environment. For all following commands ensure that this environment is activated via

```sh
    conda activate snakemake
```

### Step 2: Clone workflow

First, create an appropriate project working directory on your system and enter it:

```sh
    WORKDIR=path/to/project_workdir
    mkdir -p ${WORKDIR}
    cd ${WORKDIR}
```

In all following steps, we will assume that you are inside of that directory.

Second, to clone the full workflow run:

```sh
    git clone https://github.com/IKIM-Essen/MetaResist
```

### Step 3: Install required tools

Install <sra-tools> for downloading SRA samples:

```sh
    mamba install -c bioconda -c conda-forge sra-tools
```

Install <peppy> for handling PEP-based sample metadata:

```sh
    mamba install -c conda-forge -c bioconda peppy
```

### Step 4: Download example SRA samples

Example SRA runs used for initial testing:

- SRR26321896 (*Klebsiella pneumoniae*)

Download the sample using <prefetch> and convert it to FASTQ format with <fasterq-dump> :

```sh
    prefetch SRR26321896
    fasterq-dump SRR26321896 --split-files --threads 8
```

For single-end data:

```sh
    gzip SRR26321896.fastq
```

### Step 5: Prepare sample metadata

Edit the config/pep/samples.csv file to add your sample:

```sh
    sample_name,fastq
    SRR26321896,data/raw/SRR26321896.fastq.gz
```

### Step 6: Run the workflow 

Perform a dry-run first:

```sh
    snakemake -n
```

Run the workflow:

```sh
    snakemake --cores all --use-conda
```