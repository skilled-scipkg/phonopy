# phonopy source map: Test

Generated from source roots:
- `c`
- `phonopy`
- `test`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Fast source navigation
- `rg -n "<symbol_or_keyword>" test phonopy c`
- `rg -n "^def test_" test/**/*.py`
- `rg -n "^(def |class )" phonopy/**/*.py`

## Suggested source entry points
- `phonopy/cui/create_force_sets.py` | key functions: `create_FORCE_SETS`, `check_number_of_force_files`
- `phonopy/cui/load.py` | key function: `load`
- `phonopy/interface/qe.py` | key functions: `read_pwscf`, `parse_set_of_forces`
- `phonopy/interface/lammps.py` | key functions: `parse_set_of_forces`, `rotate_lammps_forces`
- `phonopy/harmonic/force_constants.py` | key functions: `solve_force_constants`, `symmetrize_force_constants`
- `phonopy/phonon/band_structure.py` | key class: `BandStructure`
- `phonopy/phonon/group_velocity.py` | key class: `GroupVelocity`
- `phonopy/qha/core.py` | key class: `QHA`
- `phonopy/spectrum/dynamic_structure_factor.py` | key class: `DynamicStructureFactor`

## Behavior-check test entry points
- `test/api/test_api_phonopy.py` | API state mutation and calculator routing checks
- `test/cui/phonopy_command/test_phonopy_script.py` | CLI end-to-end workflow checks
- `test/interface/test_qe.py` | QE reader and q2r force-constant checks
- `test/interface/test_lammps.py` | LAMMPS structure/force parser checks
- `test/phonopy_load/test_phonopy_load.py` | loader conversion-factor checks
- `test/harmonic/test_force_constants.py` | FC solver/symmetry behavior checks
- `test/phonon/test_band_structure.py` | band generation and output checks
- `test/qha/test_QHA.py` | QHA fitting and thermodynamic trend checks
- `test/spectrum/test_dynamic_structure_factor.py` | dynamic structure factor behavior checks
