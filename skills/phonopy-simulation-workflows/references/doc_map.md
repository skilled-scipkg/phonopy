# phonopy documentation map: Simulation Workflows

Generated from documentation roots:
- `doc`
- `example`
- `test`

Total docs grouped in this topic: 24

## File inventory
- `example/KCl-SSCHA/README.md` | title: Example of KCl SSCHA calculation | headings: Example of KCl SSCHA calculation; How to run; Comparison with the reported result
- `example/NaCl/README.md` | title: NaCl example | headings: NaCl example; % phonopy -d --dim 2 2 2 --pa auto -c POSCAR-unitcell; % phonopy -f vasprun.xml-001 vasprun.xml-002
- `example/Si/README.md` | title: Si example | headings: Si example; % phonopy -d --dim 2 2 2 --pa auto -c POSCAR-unitcell; % phonopy -f vasprun.xml
- `example/NaCl-rd/README.md` | title: NaCl example with random direction displacements. | headings: NaCl example with random direction displacements.; % phonopy --rd 10 --dim 2 2 2 --pa auto --amplitude 0.03 -c POSCAR-unitcell; % phonopy -f force-calcs/disp-{001..010}/vasprun.xml
- `example/NaCl-VASPdfpt/README.md` | title: NaCl phonon calculation with DFPT functional of VASP code | headings: NaCl phonon calculation with DFPT functional of VASP code; % mv SPOSCAR POSCAR; % phonopy --fc vasprun.xml
- `example/Cr/README.md` | title: Cr with collinear magnetic moments | headings: Cr with collinear magnetic moments; % phonopy -d --dim 2 2 2 --pa "-1/2 1/2 1/2 1/2 -1/2 1/2 1/2 1/2 -1/2" --magmom "1 -1" -c POSCAR-unitcell; % phonopy -f vasprun.xml.xz
- `example/Al2O3/README.md` | title: Corundum Al2O3 | headings: Corundum Al2O3; % phonopy -c POSCAR-unitcell --symmetry --pa=auto; % phonopy -d --dim 2 2 1 --pa auto -c POSCAR-unitcell
- `doc/vasp.md` | title: VASP & phonopy calculation | headings: VASP & phonopy calculation; Pre-process; Calculation of sets of forces
- `doc/vasp-dfpt.md` | title: VASP-DFPT & phonopy calculation | headings: VASP-DFPT & phonopy calculation; How to run; 0.0000000000000000  0.0000000000000000  0.5000000000000000
- `doc/qe.md` | title: Quantum ESPRESSO (QE) & phonopy calculation | headings: Quantum ESPRESSO (QE) & phonopy calculation; Supported QE-PW tags; How to run
- `doc/mlp-sscha.md` | title: Temperature dependent force constants calculation using pypolymlp and symfc | headings: Temperature dependent force constants calculation using pypolymlp and symfc; Citation of pypolymlp; Citation of symfc
- `doc/gruneisen.md` | title: Calculation of mode Grüneisen parameters | headings: Calculation of mode Grüneisen parameters; How to run; Force calculator interfaces
- `doc/phonopy-load.md` | title: phonopy-load command | headings: phonopy-load command; Example; List of differences from phonopy command
- `doc/qlm.md` | title: Questaal & phonopy calculation | headings: Questaal & phonopy calculation; How to run; phonopy --qlm -d --dim='2 2 2' -c site.lm
- `doc/workflow.md` | title: Work flow | headings: Work flow; Phonon calculations at constant volume; Combinations of phonon calculations at different volumes
- `doc/crystal.rst` | title: CRYSTAL & phonopy calculation | headings: CRYSTAL & phonopy calculation; Supported features; How to run
- `doc/turbomole.rst` | title: TURBOMOLE & phonopy calculation | headings: TURBOMOLE & phonopy calculation; Supported features; How to run
- `doc/siesta.rst` | title: Siesta & phonopy calculation | headings: Siesta & phonopy calculation; Supported Siesta tags; How to run
- `doc/elk.rst` | title: Elk & phonopy calculation | headings: Elk & phonopy calculation; Supported Elk tags; How to run
- `doc/abinit.rst` | title: Abinit & phonopy calculation | headings: Abinit & phonopy calculation; Supported Abinit variables; How to run
- `doc/wien2k.rst` | title: Wien2k & phonopy calculation | headings: Wien2k & phonopy calculation; How to run
- `doc/dftb+.rst` | title: DFTB+ & phonopy calculation | headings: DFTB+ & phonopy calculation; How to run
- `doc/abacus.rst` | title: ABACUS & phonopy calculation | headings: ABACUS & phonopy calculation; How to run
- `doc/Fleur.rst` | title: Fleur & phonopy calculation | headings: Fleur & phonopy calculation; How to run
