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

1. **value of berry_task not recognised in param_read**  
The error is still present in the latest release of *Wannier90* `v3.0.0`. 
To resolve this issue you might need to try the [develop branch](https://github.com/wannier-developers/wannier90/archive/develop.zip) of the wannier90 repository. 
There is a related [issue](https://github.com/wannier-developers/wannier90/issues/286) on github as well. 

2. **kmesh_get_bvector: Not enough bvectors found**  
This error can be resolved by changing (inreasing) the `kmesh_tol` in the `.win` file. 

3. **Direct lattice mismatch**  
This error happens because the real and reciprocal lattice vectors of the `.scf` file and the `.win` file do not match.  
I was not able to get a perfect match, so I just commented out the part of code that compares lattice vectors in `pw2wannier90.f90` file and recompiled it.

4. **too many projections to be used without selecting a subset**  
The error seems to go away if you set the projections in the `.win` file to random as follows. 
```
begin projections
random
end projections
```
