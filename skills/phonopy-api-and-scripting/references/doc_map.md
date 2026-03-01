# phonopy documentation map: API and Scripting

Generated from documentation roots:
- `doc`
- `example`
- `test`

Total docs grouped in this topic: 9

## File inventory
- `example/SiO2-CP2K-xyz/README.md` | title: % python gen_supercell_xyz.py -i Punitcell.inp --dim="2 2 2" --born | headings: % python gen_supercell_xyz.py -i Punitcell.inp --dim="2 2 2" --born; %phonopy --cp2k -f DISP-{0001..0012}/SiO2-forces-1_0.xyz; python get_born_cp2k.py -i DISP-0000/polar.out -m force.out
- `example/Si-lammps/README.md` | title: Si example using LAMMPS interface | headings: Si example using LAMMPS interface; % python generate_displacements.py; % lmp_serial -in in.polymlp
- `example/Si-QE/README.md` | title: QE-PW interface with Si example | headings: QE-PW interface with Si example; % phonopy --qe -c Si.in -d --dim 2 2 2 --pa auto; % phonopy --qe -f supercell-001.out
- `example/Si-CP2K/README.md` | title: Example for the CP2K Phonopy interface using bulk silicon | headings: Example for the CP2K Phonopy interface using bulk silicon; $ phonopy --cp2k -c Si.inp -d --dim="2 2 2"; $ phonopy --cp2k -f Si-supercell-001-forces-1_0.xyz
- `example/NaCl-CP2K/README.md` | title: Example of the CP2K Phonopy interface for NaCl | headings: Example of the CP2K Phonopy interface for NaCl; $ phonopy --cp2k -c NaCl.inp -d --dim="2 2 2"; $ phonopy --cp2k -f NaCl-supercell-001-forces-1_0.xyz NaCl-supercell-002-forces-1_0.xyz
- `example/Ti-lammps/README.md` | title: HCP Ti example using LAMMPS interface | headings: HCP Ti example using LAMMPS interface; \___|_| |_|\__,_|; % lmp_serial -in in.polymlp
- `doc/external-tools.md` | title: External tools | headings: External tools; Phonopy-Spectroscopy; Features
- `doc/interfaces.md` | title: Interfaces to calculators | headings: Interfaces to calculators; List of force calculators; Physical unit system for calculator
- `doc/formulation.md` | title: Formulations | headings: Formulations; Second-order force constants; Modified Parlinski-Li-Kawazoe method
