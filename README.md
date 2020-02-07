# topological-insulator-spin-hall
Ab initio calculation of the spin Hall conductivity in topological insulators using Quantum ESPRESSO and Wannier90 codes.

### Set paths
The file `set-path` needs to be modified with the correct paths to the root directories of Quantum ESPRESSO and Wannier90 folders on your machine.
```shell 
QE_PATH=$HOME/qe-6.4.1              # replace with your quantum espresso path
WANNIER_PATH=$HOME/wannier90-3.0.0  # replace with your wannier90 path 
```

### Troubleshooting
Here is a list of some common problems that might occur during calculations: 

1. **kmesh_get_bvector: Not enough bvectors found**
This error can be resolved by changing (inreasing) the `kmesh_tol` in the `.win` file. 

2. **Direct lattice mismatch**
This error happens because the real and reciprocal lattice vectors of the `.scf` file and the `.win` file do not match.  
I was not able to get a perfect match, so I just commented out the part of code that compares lattice vectors in `pw2wannier90.f90` file and recompiled it. 
