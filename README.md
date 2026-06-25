# SOLPS on Omega
This repo is intended to support SOLPS-ITER code users using a central installation on the Omega cluster at General Atomics.

## Why central installation?
Central installation enables users to create meshes, etc. under `${SOLPSTOP}/modules/.../${DEVICE}/${USER}` instead of `${SOLPSTOP}/modules/.../${DEVICE}` for the scripts such as `dg`, `carre`, `carre2`, and `triang`. 
The `solps-iter` Linux group on Omega is necessary to achieve the appropriate permissions for each `${DEVICE}` subdirectory.
SOLPS-ITER code provides the script `add_central_device` to avoid permission issues when the first user creates a `${DEVICE}` directory. You may ask KyuBeen (kwonk@fusion.gat.com) to create the appropriate `${DEVICE}` directory if needed.
Please refer to Section 1.6 "Using a central installation" in the SOLPS-ITER User Manual for details.

Loading SOLPS-ITER environment using a central installation will: 
- Specify a run directory `${SOLPSWORK}` for each user
  - `${SOLPSWORK}=/fusion/projects/solps-results/${USER}` by default
  - `${SOLPSWORK}=${SOLPS_USER_DIR}` if each user had set `${SOLPS_USER_DIR}`
- Create a file `SOLPSTOP` which contains the value for `${SOLPSTOP}`
- Source `${SOLPSWORK}/setup.csh.local` if it exists

# How to start
## Prerequistes
1. Request to be added to the `solps-iter` Linux group on Omega.
2. Create your own directory `/fusion/projects/solps-results/${USER}` if it doesn't exist
```tcsh
mkdir /fusion/projects/solps-results/${USER}
```
3. (Optional) If you set `${SOLPS_USER_DIR}`, your run directory `${SOLPSWORK}` will be `${SOLPS_USER_DIR}` instead of `/fusion/projects/solps-results/${USER}`.
```tcsh
vim ~/.tcshrc
setenv SOLPS_USER_DIR ${ANYWHERE_YOU_WANT_TO_RUN_SOLPS}
```

## Load SOLPS-ITER environment
Load the public SOLPS-ITER v.3.0.10 environment from your desired directory for `${SOLPSWORK}`
```tcsh
tcsh
cd /fusion/projects/solps-results/${USER}  # Or, cd ${SOLPS_USER_DIR} if it exists.
# SOLPS-ITER v.3.0.10 master
source /fusion/projects/codes/solps/SOLPS-ITER/public_code/solps-iter_3.0.10_apr2026/setup.csh
# SOLPS-ITER v.3.2.1 Wide Grids
source /fusion/projects/codes/solps/SOLPS-ITER/public_code/solps-iter_3.2.1_WG_apr2026/setup.csh
```
This will:
- `module purge` and load modules for SOLPS-ITER code
- Set the environment variable `${DEVICE}` and print it out: `echo "Current DEVICE is: ${DEVICE}"`
