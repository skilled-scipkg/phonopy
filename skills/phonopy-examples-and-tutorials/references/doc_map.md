# phonopy documentation map: Examples and Tutorials

Generated from documentation roots:
- `doc`
- `example`
- `test`

Total docs grouped in this topic: 12

## File inventory
- `example/Si-PWmat/README.md` | title: % phonopy --pwmat -c atom.config -d --dim 2 2 2 --pa F | headings: % phonopy --pwmat -c atom.config -d --dim 2 2 2 --pa F; % phonopy -f OUT.FORCE-001; % phonopy -p band.conf
- `example/NaCl-wien2k/README.md` | title: NaCl phonon calculation with Wien2k | headings: NaCl phonon calculation with Wien2k; % phonopy --wien2k -c NaCl.struct -d --dim="2 2 2" --pa auto; % phonopy --wien2k -f NaCl-001.scf NaCl-002.scf
- `example/NaCl-wien2k-P1/README.md` | title: NaCl phonon calculation with Wien2k P1 symmetry | headings: NaCl phonon calculation with Wien2k P1 symmetry; % phonopy --wien2k -c NaCl.struct -d --dim="2 2 2" --pa auto; % phonopy --wien2k -f NaCl-001.scf NaCl-002.scf
- `example/NaCl-QE/README.md` | title: % phonopy --qe -c NaCl.in -d --dim 2 2 2 --pa auto | headings: % phonopy --qe -c NaCl.in -d --dim 2 2 2 --pa auto; % phonopy -f NaCl-001.out NaCl-002.out; % phonopy-load --band "0.0 0.0 0.0  0.5 0.0 0.0  0.5 0.5 0.0  0.0 0.0 0.0  0.5 0.5 0.5" -p
- `example/SiO2-HP/README.md` | title: SiO2 high pressure phase of Stishovite | headings: SiO2 high pressure phase of Stishovite; % phonopy-load --band "0.5 0.5 0.5  0.0 0.0 0.0  0.5 0.5 0.0  0.0 0.5 0.0" -p; % phonopy-load --anime 0 0 0
- `example/LiF-nosym/README.md` | title: LiF with `--nosym` option | headings: LiF with `--nosym` option; % phonopy -d --dim="2 2 2" --nosym -c POSCAR-unitcell; % phonopy-load --mesh 50 --nosym -p
- `example/ZnO/README.md` | title: Phonon calculation of ZnO with 2x2x2 supercell | headings: Phonon calculation of ZnO with 2x2x2 supercell; % phonopy-load --irreps 0 0 0
- `example/TiO2-anatase/README.md` | title: Phonon calculation for TiO2-anatase | headings: Phonon calculation for TiO2-anatase; % phonopy-load --band auto -p
- `example/MgO/README.md` | title: MgO example | headings: MgO example; % phonopy-load --band auto -p
- `example/MgB2/README.md` | title: MgB2 example | headings: MgB2 example; % phonopy-load --band "0 0 0  1/3 1/3 0  1/2 0 0  0 0 0  0 0 1/2  1/3 1/3 1/2  1/2 0 1/2  0 0 1/2" -p
- `example/diamond-FHI-aims/README.md` | title: Readme | headings: (no heading extracted)
- `doc/random-displacements.md` | title: Random displacements | headings: Random displacements; Related setting tags; Random directions with constant displacement distance
