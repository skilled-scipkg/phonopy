# phonopy source map: General

Generated from source roots:
- `c`
- `phonopy`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Fast source navigation
- `rg -n "<symbol_or_keyword>" phonopy test c`
- `rg -n "^(def |class )" phonopy/**/*.py`
- If a doc mentions a symbol, search that symbol first, then inspect the closest call sites.

## Suggested source entry points
- `phonopy/api_phonopy.py` | key class: `Phonopy` (top-level orchestration object)
- `phonopy/cui/phonopy_script.py` | key functions: `_start_phonopy`, `_produce_force_constants`, `_post_process_force_constants`
- `phonopy/cui/load.py` | key function: `load` (yaml-first runtime loader)
- `phonopy/interface/calculator.py` | key functions: `read_crystal_structure`, `write_supercells_with_displacements`
- `phonopy/file_IO.py` | key functions: `parse_FORCE_SETS`, `parse_BORN`, `read_thermal_properties_yaml`
- `phonopy/harmonic/force_constants.py` | key functions: `solve_force_constants`, `symmetrize_force_constants`
- `phonopy/phonon/band_structure.py` | key class: `BandStructure`

## Behavior-check test entry points
- `test/api/test_api_phonopy.py` | verifies API setters and calculator-dependent behavior
- `test/cui/phonopy_command/test_phonopy_script.py` | validates CLI workflow branches and output artifacts
- `test/phonopy_load/test_phonopy_load.py` | validates `phonopy-load` unit conversion and loading behavior
