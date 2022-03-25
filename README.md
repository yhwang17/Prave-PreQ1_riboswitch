# prave_PreQ1_riboswitch
GROMACS and PLUMED codes to reproduce result in  the draft <a href="https://www.biorxiv.org/content/10.1101/2021.09.28.462207v1.abstract">Interrogating RNA-small molecule interactions with structure probing and AI augmented-molecular simulations</a> The simulations and analysis are preformed on 3 system: PreQ1 without ligand (apo), PreQ1 with the cognate ligand (6e1w) and PreQ1 with the synthetic ligand (6e1u)


## Usage
Files for the MD simulations can be found in the `gromacs` folder.

You can run `gromp` to generate the binary input file (.tpr).  
For apo system,  you can run:
```bash
gmx grompp -f md.mdp -c npt.gro -p topol.top -t npt.cpt -o md_0_1.tpr
```

For riboswitch with cognate or synthetic ligand, you can run:
```bash
gmx grompp -f md.mdp -c npt.gro -p topol.top -t npt.cpt -n index.ndx -o md_0_1.tpr
```

You can run `mdrun` to start the enhanced MD simulation:
```bash
gmx mdrun md_0_1 -plumed plumed.production.dat
```
The associated PLUMED files can be found in the `production` folders.

To calculate the  C2-C2 distances, please refer to the files in the `analysis` folders.
