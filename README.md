# SOLPS on Omega
Documentation and scripts for running the central SOLPS-ITER installation on the Omega cluster at General Atomics.

# How to use SOLPS-ITER code on Omega
Please note that the GA CSS team has set up the `solps_iter` module on Omega very well. The instructions below are for using the new master version v.3.0.10 released on April 3, 2026. Most of the libraries used to compile v.3.0.10, except GKS and MSCL, are from the CSS installation.
## SOLPS-ITER v.3.0.10
1. Load the public v.3.0.10 distribution on Omega
```tcsh
tcsh
cd /fusion/projects/codes/solps/SOLPS-ITER/public_code/solps-iter_3.0.10_apr2026
source setup.csh
```
## SOLPS-ITER v.3.2.1 - Wide Grid
1. Load the public v.3.2.1 distribution on Omega
```tcsh
tcsh
cd /fusion/projects/codes/solps/SOLPS-ITER/public_code/solps-iter_wg-release_apr2026
source setup.csh
```
## CSS installation: SOLPS-ITER v.3.0.8
```tcsh
# ${SOLPSTOP} will be /fusion/projects/codes/imas/c8/SOLPS-ITER/solps-iter_3.0.8_develop_test
tcsh
module purge
module load solps_iter
```
