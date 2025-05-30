# WTCBench

[![Coverage Status](https://coveralls.io/repos/github/WISDEM/WEIS/badge.svg?branch=develop)](https://coveralls.io/github/WISDEM/WEIS?branch=develop)
[![Actions Status](https://github.com/WISDEM/WEIS/workflows/CI_WEIS/badge.svg?branch=develop)](https://github.com/WISDEM/WEIS/actions)
[![Documentation Status](https://readthedocs.org/projects/weis/badge/?version=develop)](https://weis.readthedocs.io/en/develop/?badge=develop)
[![DOI](https://zenodo.org/badge/289320573.svg)](https://zenodo.org/badge/latestdoi/289320573)

WTCBench is a fork of the [WEIS](https://github.com/WISDEM/WEIS) repository, focused on controller benchmarking and performance.


## Installation

On laptop and personal computers, installation with [Anaconda](https://www.anaconda.com) is the recommended approach because of the ability to create self-contained environments suitable for testing and analysis.  WEIS requires [Anaconda 64-bit](https://www.anaconda.com/distribution/). However, the `conda` command has begun to show its age and we now recommend the one-for-one replacement with the [Miniforge3 distribution](https://github.com/conda-forge/miniforge?tab=readme-ov-file#miniforge3), which is much more lightweight and more easily solves for the package dependencies.  Sometimes, using `mamba` in place of `conda` with this distribution speeds up the installation process. WEIS is currently supported on Linux, MAC and Windows Sub-system for Linux (WSL). Installing WEIS on native Windows is not yet supported, but planned in 2024.

The installation instructions below use the environment name, "weis-env," but any name is acceptable. For those working behind company firewalls, you may have to change the conda authentication with `conda config --set ssl_verify no`.  Proxy servers can also be set with `conda config --set proxy_servers.http http://id:pw@address:port` and `conda config --set proxy_servers.https https://id:pw@address:port`.

0.  On the DOE HPC system eagle, make sure to start from a clean setup and type

        module purge
        module load conda        

1.  Setup and activate the Anaconda environment from a prompt (WSL terminal on Windows or Terminal.app on Mac)

        conda config --add channels conda-forge
        conda install git
        git clone https://github.com/WISDEM/WEIS.git
        cd WEIS
        git checkout branch_name                         # (Only if you want to switch branches, say "develop")
        conda env create --name weis-env -f environment.yml
        conda activate weis-env                          # (if this does not work, try source activate weis-env)


2. Add in final packages and install the software

        conda install -y petsc4py=3.22.2 mpi4py pyoptsparse     # (Mac / Linux only, sometimes Windows users may need to install mpi4py)
        pip install -e .

3. Instructions specific for DOE HPC system Eagle.  Before executing the setup script, do:

        module load comp-intel intel-mpi mkl
        module unload gcc
        pip install --no-deps -e . -v

**NOTE:** To use WEIS again after installation is complete, you will always need to activate the conda environment first with `conda activate weis-env` (or `source activate weis-env`). On Eagle, make sure to reload the necessary modules

For Windows users, we recommend installing `git` and the `m264` packages in separate environments as some of the libraries appear to conflict such that WISDEM cannot be successfully built from source.  The `git` package is best installed in the `base` environment.

## Developer guide

If you plan to contribute code to WEIS, please first consult the [developer guide](https://weis.readthedocs.io/en/latest/how_to_contribute_code.html).

## Feedback

For software issues please use <https://github.com/WISDEM/WEIS/issues>.  
