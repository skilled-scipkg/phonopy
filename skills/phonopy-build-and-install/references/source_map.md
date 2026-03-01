# phonopy source map: Build and Install

Generated from source roots:
- `c`
- `phonopy`
- build config files

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Fast source navigation
- `rg -n "<symbol_or_keyword>" CMakeLists.txt pyproject.toml c phonopy test`
- `rg -n "PHONOPY_USE_OMP|nanobind|project\.scripts|requires" CMakeLists.txt pyproject.toml`
- `rg -n "^(def |class )" phonopy/scripts/*.py phonopy/cui/*.py`

## Suggested source entry points
- `pyproject.toml` | package metadata, optional dependencies, and CLI script entry points
- `CMakeLists.txt` | native build graph, OpenMP toggle, and `_phonopy` extension wiring
- `c/_phonopy.cpp` | nanobind bridge between Python and C kernels
- `c/phonopy.c` | core C kernels linked into the extension
- `c/phonopy.h` | public C declarations used by `_phonopy.cpp`
- `phonopy/version.py` | source of package version used during build metadata generation
- `phonopy/scripts/phonopy.py` | CLI entrypoint (`run`) for preprocessing/import paths
- `phonopy/scripts/phonopy_load.py` | CLI entrypoint (`run`) for postprocessing paths
- `phonopy/cui/phonopy_script.py` | runtime flow orchestration for `phonopy`
- `phonopy/cui/load.py` | runtime flow orchestration for `phonopy-load`

## Behavior-check test entry points
- `test/api/test_api_phonopy.py` | confirms core API behavior in the built environment
- `test/phonopy_load/test_phonopy_load.py` | checks conversion/load behavior that often fails on bad installs
- `test/cui/phonopy_command/test_phonopy_script.py` | validates CLI-driven end-to-end smoke flows
