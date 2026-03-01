# phonopy source map: Analysis and Output

Generated from source roots:
- `c`
- `phonopy`
- `test`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Fast source navigation
- `rg -n "<symbol_or_keyword>" phonopy test c`
- `rg -n "^(def |class )" phonopy/qha/*.py phonopy/scripts/phonopy_*plot.py phonopy/file_IO.py`
- For output bugs, trace producer command -> yaml/dat parser -> plotting utility.

## Suggested source entry points
- `phonopy/scripts/phonopy_load.py` | postprocess entrypoint (`run`)
- `phonopy/api_qha.py` | API wrapper for QHA: `PhonopyQHA`
- `phonopy/scripts/phonopy_qha.py` | QHA CLI entrypoint (`run`)
- `phonopy/qha/core.py` | QHA implementation classes: `QHA`, `BulkModulus`
- `phonopy/qha/eos.py` | EOS fitting helpers: `get_eos`, `fit_to_eos`
- `phonopy/file_IO.py` | output readers: `read_thermal_properties_yaml`, `read_v_e`, `read_efe`
- `phonopy/scripts/phonopy_bandplot.py` | band plotting entrypoint (`run`)
- `phonopy/scripts/phonopy_pdosplot.py` | PDOS plotting entrypoint (`run`)
- `phonopy/scripts/phonopy_propplot.py` | thermal-property plotting entrypoint (`run`)
- `phonopy/scripts/phonopy_tdplot.py` | thermal-displacement plotting entrypoint (`run`)
- `phonopy/phonon/band_structure.py` | band data generation and write paths

## Behavior-check test entry points
- `test/qha/test_QHA.py` | QHA fitting and thermal trend checks
- `test/qha/test_QHA_efe.py` | electronic free-energy QHA path checks
- `test/phonon/test_band_structure.py` | band output generation checks
- `test/phonopy_load/test_phonopy_load.py` | load-mode output behavior checks
- `test/spectrum/test_dynamic_structure_factor.py` | spectral output sanity checks
