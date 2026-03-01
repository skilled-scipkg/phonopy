# phonopy source map: Examples and Tutorials

Generated from source roots:
- `c`
- `phonopy`
- `test`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Fast source navigation
- `rg -n "<symbol_or_keyword>" phonopy test c`
- `rg -n "^(def |class )" phonopy/interface/*.py phonopy/phonon/random_displacements.py`
- For example adaptation issues, map example command -> interface parser -> FORCE_SETS path.

## Suggested source entry points
- `phonopy/phonon/random_displacements.py` | random displacement generator: `RandomDisplacements`
- `phonopy/interface/qe.py` | QE example parser/write helpers
- `phonopy/interface/cp2k.py` | CP2K example parser/write helpers
- `phonopy/interface/lammps.py` | LAMMPS structure and force parser helpers
- `phonopy/interface/wien2k.py` | Wien2k parser/write helpers
- `phonopy/interface/pwmat.py` | PWmat parser/write helpers
- `phonopy/interface/aims.py` | FHI-aims parser/write helpers
- `phonopy/cui/create_force_sets.py` | FORCE_SETS assembly from parsed force outputs
- `phonopy/scripts/phonopy_load.py` | postprocess command entrypoint used in examples
- `phonopy/api_phonopy.py` | API-level bridge when examples are converted to Python scripts

## Behavior-check test entry points
- `test/interface/test_qe.py` | QE example parser behavior checks
- `test/interface/test_CP2K.py` | CP2K example parser behavior checks
- `test/interface/test_lammps.py` | LAMMPS example parser behavior checks
- `test/interface/test_wien2k.py` | Wien2k parser behavior checks
- `test/interface/test_pwmat.py` | PWmat parser behavior checks
- `test/cui/phonopy_command/test_phonopy_script.py` | CLI example-command behavior checks
