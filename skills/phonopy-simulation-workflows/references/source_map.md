# phonopy source map: Simulation Workflows

Generated from source roots:
- `c`
- `phonopy`
- `test`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Fast source navigation
- `rg -n "<symbol_or_keyword>" phonopy test c`
- `rg -n "^(def |class )" phonopy/cui/*.py phonopy/interface/*.py phonopy/gruneisen/*.py`
- Start from CLI entry points, then follow into parser/helpers used by that command.

## Suggested source entry points
- `phonopy/scripts/phonopy.py` | CLI preprocess/import entrypoint (`run`)
- `phonopy/cui/phonopy_script.py` | workflow functions: `_create_FORCE_SETS_from_settings`, `_produce_force_constants`, `_post_process_force_constants`
- `phonopy/cui/create_force_sets.py` | force-import assembly: `create_FORCE_SETS`
- `phonopy/scripts/phonopy_load.py` | postprocess entrypoint (`run`)
- `phonopy/cui/load.py` | yaml-driven loader: `load`
- `phonopy/cui/load_helper.py` | FC/data helpers: `select_and_extract_force_constants`, `produce_force_constants`, `get_nac_params`
- `phonopy/interface/vasp.py` | VASP parsing: `parse_set_of_forces`, `parse_force_constants`
- `phonopy/interface/qe.py` | QE parsing: `parse_set_of_forces`, `read_pwscf`
- `phonopy/interface/cp2k.py` | CP2K parsing: `read_cp2k`, `parse_set_of_forces2025`
- `phonopy/interface/lammps.py` | LAMMPS parsing/rotation: `parse_set_of_forces`, `rotate_lammps_forces`
- `phonopy/scripts/phonopy_gruneisen.py` | Gruneisen CLI entrypoint (`run`)
- `phonopy/api_gruneisen.py` | API-level Gruneisen workflow: `PhonopyGruneisen`
- `phonopy/gruneisen/core.py` | Gruneisen core behavior: `GruneisenBase`
- `phonopy/sscha/core.py` | finite-temperature FC workflow: `MLPSSCHA`

## Behavior-check test entry points
- `test/cui/phonopy_command/test_phonopy_script.py` | end-to-end CLI workflow checks (disp, force import, load)
- `test/phonopy_load/test_phonopy_load.py` | postprocess load and conversion checks
- `test/gruneisen/test_gruneisen.py` | gruneisen mesh/band behavior checks
- `test/cui/phonopy_gruneisen/test_phonopy_gruneisen_script.py` | gruneisen CLI behavior checks
