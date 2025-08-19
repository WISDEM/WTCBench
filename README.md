# WTCBench

[![Coverage Status](https://coveralls.io/repos/github/WISDEM/WEIS/badge.svg?branch=develop)](https://coveralls.io/github/WISDEM/WEIS?branch=develop)
[![Actions Status](https://github.com/WISDEM/WEIS/workflows/CI_WEIS/badge.svg?branch=develop)](https://github.com/WISDEM/WEIS/actions)
[![Documentation Status](https://readthedocs.org/projects/weis/badge/?version=develop)](https://weis.readthedocs.io/en/develop/?badge=develop)
[![DOI](https://zenodo.org/badge/289320573.svg)](https://zenodo.org/badge/latestdoi/289320573)

WTCBench is a fork of the [WEIS](https://github.com/WISDEM/WEIS) repository, focused on controller benchmarking and performance.


## Installation

On laptop and personal computers, installation with [Anaconda](https://www.anaconda.com) is the recommended approach because of the ability to create self-contained environments suitable for testing and analysis.  WEIS requires [Anaconda 64-bit](https://www.anaconda.com/distribution/). However, the `conda` command has begun to show its age and we now recommend the one-for-one replacement with the [Miniforge3 distribution](https://github.com/conda-forge/miniforge?tab=readme-ov-file#miniforge3), which is much more lightweight and more easily solves for the package dependencies.  Sometimes, using `mamba` in place of `conda` with this distribution speeds up the installation process. WEIS is supported on Linux, MAC, Windows Sub-system for Linux (WSL), and native Windows.

The installation instructions below use the environment name, "weis-env," but any name is acceptable. For those working behind company firewalls, you may have to change the conda authentication with `conda config --set ssl_verify no`.  Proxy servers can also be set with `conda config --set proxy_servers.http http://id:pw@address:port` and `conda config --set proxy_servers.https https://id:pw@address:port`.

0.  If you are NOT installing WEIS on DOE's HPC system Kestrel, skip step 0 and run step 1 and 2 (skip step 3). If you are on Kestrel, follow steps 0, 1, and 3, and skip step 2. On Kestrel, start by purging existing modules and load conda

        module purge
        module load conda        

1.  In a terminal, setup and activate the Anaconda environment

        conda config --add channels conda-forge
        conda install git
        git clone https://github.com/WISDEM/WEIS.git
        cd WEIS
        git checkout branch_name                         # (Only if you want to switch branches, say "develop")
        conda env create --name weis-env -f environment.yml
        conda activate weis-env                          # (if this does not work, try source activate weis-env)
        conda install -y petsc4py=3.22.2 mpi4py pyoptsparse     # (Mac / Linux only, sometimes Windows users may need to install mpi4py)

2. If you are NOT on Kestrel, install the software
        pip install -e .

3. If you are on Kestrel, first load some modules and then install:
        module load intel-oneapi-compilers intel-oneapi-mpi intel-oneapi-mkl conda
        pip install --no-deps -e . -v

**NOTE:** To use WEIS again after installation is complete, you will always need to activate the conda environment first with `conda activate weis-env` (or `source activate weis-env`). On Kestrel, make sure to reload the necessary modules

For Windows users, we recommend installing `git` and the `m264` packages in separate environments as some of the libraries appear to conflict such that WISDEM cannot be successfully built from source.  The `git` package is best installed in the `base` environment.

## Developer guide

If you plan to contribute code to WEIS, please first consult the [developer guide](https://weis.readthedocs.io/en/latest/how_to_contribute_code.html).

## Feedback

For software issues please use <https://github.com/WISDEM/WEIS/issues>.  
