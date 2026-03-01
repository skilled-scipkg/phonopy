---
name: phonopy-test
description: Use this skill for regression triage, focused pytest selection, and mapping failures to phonopy source modules.
---

# phonopy: Test

## High-Signal Playbook
### Route conditions
- Use this skill when users ask to reproduce/fix bugs, verify behavior changes, or choose a targeted regression test slice.
- Route conceptual setup questions to domain skills first when no failing behavior is identified yet.

### Triage questions
- Which subsystem failed (CLI, interface parser, force constants, phonopy-load, qha, spectrum)?
- Is the failure data-driven (fixture mismatch) or algorithmic (math/logic)?
- Is an optional dependency required (`pypolymlp`, `h5py`, calculator-specific tools)?
- Is this a quick smoke check or a release-blocking regression pass?

### Canonical workflow
1. Reproduce with one focused test target.
2. If parser/interface related, run a concrete interface module test (for example `test/interface/test_qe.py` or `test/interface/test_lammps.py`).
3. If output semantics changed, run `test/phonopy_load/test_phonopy_load.py` and neighboring domain tests.
4. Expand to adjacent tests only after the first failing assertion is understood.
5. Trace failures to source entry points in `references/source_map.md`.

### Minimal working example
```bash
pytest test/interface/test_qe.py -q
pytest test/phonopy_load/test_phonopy_load.py -q
pytest test/qha/test_QHA.py -q
```

### Pitfalls and fixes
- Optional-feature tests are skipped: inspect `pytest.importorskip` and environment dependencies.
- Running from a non-root directory breaks fixture-relative paths: execute from repository root.
- Compressed fixtures (`.xz`, `.bz2`) are intentional and loaded through helper I/O paths.
- Broad first-pass test runs hide root causes: keep the first run narrow and deterministic.

### Convergence and validation checks
- Re-run the first failing test until failure is deterministic.
- Keep at least one parser/interface test and one higher-level workflow test passing after fixes.
- Preserve numeric tolerances unless a documented algorithmic reason requires change.

## Scope
- Handle questions about tests, regression behavior, and verification strategy.
- Prioritize bug localization and high-signal test selection.

## Primary documentation references
- `test/conftest.py`
- `test/api/test_api_phonopy.py`
- `test/interface/test_qe.py`
- `test/interface/test_lammps.py`
- `test/phonopy_load/test_phonopy_load.py`
- `test/qha/test_QHA.py`
- `test/spectrum/test_dynamic_structure_factor.py`
- `test/phonon/test_band_structure.py`
- `test/phonon/test_group_velocity.py`

## Workflow
- Start from the test files above.
- Use `references/doc_map.md` for fixture and module inventory context.
- Escalate to `references/source_map.md` and linked implementation files for root-cause tracing.

## Tutorials and examples
- `example`

## Test references
- `test`

## Optional deeper inspection
- `c`
- `phonopy`

## Source entry points for unresolved issues
- `test/conftest.py`
- `test/cui/phonopy_command/test_phonopy_script.py`
- `test/interface/test_qe.py`
- `test/phonopy_load/test_phonopy_load.py`
- `test/qha/test_QHA.py`
- `phonopy/cui/create_force_sets.py`
- `phonopy/cui/load.py`
- `phonopy/interface/qe.py`
- `phonopy/interface/lammps.py`
- `phonopy/harmonic/force_constants.py`
- `phonopy/qha/core.py`
- `phonopy/spectrum/dynamic_structure_factor.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" test phonopy`).
