---
name: phonopy-build-and-install
description: Use this skill for installation/build setup, native-extension checks, and environment validation before running real phonopy simulations.
---

# phonopy: Build and Install

## Scope
- Handle package installation, source builds, dependency setup, and extension-loading issues.
- Provide fast verification steps before users spend compute time on simulations.

## Primary documentation references
- `doc/install.md`
- `README.md`
- `pyproject.toml`
- `CMakeLists.txt`

## High-Signal Playbook
### Recommended local build path
```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -U pip
python -m pip install -e .[dev,seekpath] -vv
phonopy --version
python -c "import phonopy; print(phonopy.__version__)"
```

### Optional runtime setting for NFS-backed filesystems
```bash
export HDF5_USE_FILE_LOCKING=FALSE
```

### Fast validation checks
```bash
pytest test/api/test_api_phonopy.py::test_Phonopy_calculator -q
pytest test/phonopy_load/test_phonopy_load.py::test_unit_conversion_factor -q
```

## Validation checkpoints
- `phonopy --version` returns without import errors.
- `python -c "import phonopy"` succeeds and prints a version.
- At least one API test and one `phonopy-load` test pass in the active environment.
- If build flags are changed, reinstall and re-run the same smoke checks.

## Workflow
- Start with `doc/install.md`.
- Use `pyproject.toml` and `CMakeLists.txt` to verify entry points, dependencies, and build toggles.
- If ambiguity remains, inspect `references/source_map.md` for function-level build/runtime entry points.
- Cite exact file paths when answering.

## Tutorials and examples
- `example`

## Test references
- `test`

## Optional deeper inspection
- `c`
- `phonopy`

## Source entry points for unresolved issues
- `pyproject.toml`
- `CMakeLists.txt`
- `c/_phonopy.cpp`
- `c/phonopy.c`
- `phonopy/version.py`
- `phonopy/scripts/phonopy.py`
- `phonopy/scripts/phonopy_load.py`
- `test/api/test_api_phonopy.py`
- `test/phonopy_load/test_phonopy_load.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" CMakeLists.txt pyproject.toml c phonopy test`).
