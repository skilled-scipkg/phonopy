# phonopy source map: API and Scripting

Generated from source roots:
- `c`
- `phonopy`
- `test`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Fast source navigation
- `rg -n "<symbol_or_keyword>" phonopy test c`
- `rg -n "^(def |class )" phonopy/api_*.py phonopy/cui/*.py phonopy/interface/*.py`
- For automation issues, trace CLI/API entrypoint -> parser -> dataset/FC production.

## Suggested source entry points
- `phonopy/scripts/phonopy.py` | CLI entrypoint (`run`)
- `phonopy/cui/phonopy_script.py` | CLI orchestration and argument-driven control flow
- `phonopy/scripts/phonopy_load.py` | postprocess CLI entrypoint (`run`)
- `phonopy/cui/load.py` | yaml-based runtime loader (`load`)
- `phonopy/api_phonopy.py` | top-level API class: `Phonopy`
- `phonopy/interface/calculator.py` | calculator dispatch/parsing: `read_crystal_structure`, `write_supercells_with_displacements`
- `phonopy/interface/phonopy_yaml.py` | yaml serialization/load classes and helpers
- `phonopy/interface/qe.py` | QE parser functions
- `phonopy/interface/cp2k.py` | CP2K parser functions
- `phonopy/interface/lammps.py` | LAMMPS parser functions
- `phonopy/file_IO.py` | FORCE_SETS/FC and yaml I/O helpers

## Behavior-check test entry points
- `test/api/test_api_phonopy.py` | API object behavior and calculator checks
- `test/phonopy_load/test_phonopy_load.py` | yaml load behavior and unit conversions
- `test/cui/phonopy_command/test_phonopy_script.py` | CLI workflow behavior checks
- `test/interface/test_qe.py` | QE parser checks
- `test/interface/test_CP2K.py` | CP2K parser checks
- `test/interface/test_lammps.py` | LAMMPS parser checks
