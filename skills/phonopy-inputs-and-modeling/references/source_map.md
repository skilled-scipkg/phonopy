# phonopy source map: Inputs and Modeling

Generated from source roots:
- `c`
- `phonopy`
- `test`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Fast source navigation
- `rg -n "<symbol_or_keyword>" phonopy test c`
- `rg -n "^(def |class )" phonopy/interface/*.py phonopy/structure/*.py phonopy/harmonic/*.py`
- For input failures, trace parser -> dataset construction -> force-constant generation.

## Suggested source entry points
- `phonopy/interface/calculator.py` | parser/router functions: `read_crystal_structure`, `write_supercells_with_displacements`
- `phonopy/structure/cells.py` | cell transforms: `shape_supercell_matrix`, `get_primitive_matrix_with_auto`
- `phonopy/structure/symmetry.py` | symmetry behavior: `Symmetry`, `symmetrize_borns_and_epsilon`
- `phonopy/structure/dataset.py` | displacement-force dataset extraction: `get_displacements_and_forces`
- `phonopy/file_IO.py` | input file parsers: `parse_FORCE_SETS`, `parse_disp_yaml`, `parse_BORN`
- `phonopy/cui/create_force_sets.py` | FORCE_SETS creation and consistency checks
- `phonopy/harmonic/force_constants.py` | FC solving/symmetry: `solve_force_constants`, `symmetrize_force_constants`, `get_drift_force_constants`
- `phonopy/harmonic/dynamical_matrix.py` | DM construction: `DynamicalMatrix`, `get_dynamical_matrix`
- `phonopy/interface/cp2k.py` | CP2K input/force parsing functions
- `phonopy/interface/lammps.py` | LAMMPS structure and force parsing functions
- `phonopy/spectrum/dynamic_structure_factor.py` | DSF setup: `DynamicStructureFactor`

## Behavior-check test entry points
- `test/structure/test_symmetry.py` | symmetry mapping and born/epsilon symmetrization checks
- `test/harmonic/test_force_constants.py` | force-constant solver and symmetry checks
- `test/interface/test_qe.py` | parser and unit-handling checks
- `test/interface/test_lammps.py` | LAMMPS parser and force-rotation checks
- `test/spectrum/test_dynamic_structure_factor.py` | dynamic structure factor checks
