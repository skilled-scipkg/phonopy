---
name: phonopy-general
description: Use this skill for top-level phonopy navigation and cross-topic routing; it keeps guidance docs-first and provides a minimal simulation smoke path.
---

# phonopy: General

## Scope
- Use this skill for project-level orientation, capability discovery, and routing to the right topic skill.
- Route end-to-end run setup and restart troubleshooting to `phonopy-simulation-workflows`.
- Route input/tag/file-format blockers to `phonopy-inputs-and-modeling`.
- Route plotting, QHA, and output interpretation to `phonopy-analysis-and-output`.

## Primary documentation references
- `doc/index.md`
- `doc/documentation.md`
- `doc/workflow.md`
- `doc/examples.md`

## Quick simulation smoke path
1. Start in a known-good example directory (for example `example/NaCl`).
2. Generate displacements: `phonopy -d --dim 2 2 2 --pa auto -c POSCAR-unitcell`.
3. Import forces after calculator jobs finish: `phonopy -f disp-{001..002}/vasprun.xml`.
4. Run postprocess smoke check: `phonopy-load --mesh 20 20 20 -t`.

## Validation checkpoints
- `phonopy_disp.yaml` exists before running `phonopy -f`.
- `FORCE_SETS` or `force_constants.hdf5` exists before `phonopy-load`.
- `phonopy-load` produces output files such as `mesh.yaml` or `thermal_properties.yaml` without parser errors.

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the grouped document inventory.
- Use examples as executable patterns before changing options.
- Use tests for behavior confirmation when claims are implementation-sensitive.
- Escalate to `references/source_map.md` only after docs and examples are insufficient.
- Cite exact repository paths in responses.

## Tutorials and examples
- `example`

## Test references
- `test`

## Optional deeper inspection
- `c`
- `phonopy`

## Source entry points for unresolved issues
- `phonopy/api_phonopy.py`
- `phonopy/cui/phonopy_script.py`
- `phonopy/cui/load.py`
- `phonopy/interface/calculator.py`
- `phonopy/file_IO.py`
- `test/api/test_api_phonopy.py`
- `test/cui/phonopy_command/test_phonopy_script.py`
- `test/phonopy_load/test_phonopy_load.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" phonopy test c`).
