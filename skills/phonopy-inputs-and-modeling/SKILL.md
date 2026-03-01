---
name: phonopy-inputs-and-modeling
description: Use this skill for structure/force input choices, key modeling tags, and pre-run validation checks that prevent expensive misconfigured phonon jobs.
---

# phonopy: Inputs and Modeling

## High-Signal Playbook
### Route conditions
- Use this skill when the blocker is input format, modeling tags, force-constant representation, or structure assumptions.
- Route to `phonopy-advanced-topics` for deep tag-by-tag references (`command-options`, `setting-tags`, symmetry theory).
- Route to `phonopy-simulation-workflows` once inputs are validated and the user needs full execution flow.

### Triage questions
- Which structure format is being used (POSCAR, QE input, CP2K input, LAMMPS structure, yaml)?
- Are you generating `FORCE_SETS` from displaced supercells, or reading precomputed `FORCE_CONSTANTS`?
- Are you using type-1 or type-2 displacement-force datasets?
- What are `DIM`, `PRIMITIVE_AXES`, and symmetry tolerance choices?
- Is NAC (`BORN`) needed and available?
- Are there magnetic moments (`MAGMOM`) or non-standard masses involved?

### Canonical workflow
1. Validate unit-cell quality/symmetry first (`--symmetry`, tight tolerance checks) (docs: `doc/symmetry.md`).
2. Choose supercell and primitive settings (`DIM`, `PRIMITIVE_AXES` or `--pa`) (docs: `doc/setting-tags.md`).
3. Generate displacement metadata (`phonopy_disp.yaml`) and calculator-compatible supercells.
4. Collect forces and build `FORCE_SETS` (or provide `FORCE_CONSTANTS` directly).
5. For advanced fitting workflows, use compatible force-constant calculators for type-2 datasets.
6. Keep all run-critical metadata in yaml artifacts for reproducibility (`phonopy_params.yaml`).

### Minimal working example
```bash
# Input-driven run with explicit dimensions and primitive axes
phonopy -d --dim 2 2 2 --pa auto -c POSCAR-unitcell
phonopy -f disp-{001..003}/vasprun.xml
phonopy-load --mesh 20 20 20 -t -p
```

### Pitfalls and fixes
- Distorted input cell gives unstable symmetry behavior: test multiple tolerances and start from standardized `BPOSCAR` when needed (docs: `doc/symmetry.md`).
- Wrong format assumptions per calculator: confirm interface parser expectations (docs: `doc/interfaces.md`, `doc/cp2k.rst`, `doc/lammps.md`).
- Missing `phonopy_disp.yaml` during `-f`: run force import in the same directory as displacement metadata (docs: `doc/input-files.md`).
- Type-2 `FORCE_SETS` used without fitting solver context: switch to supported FC calculator flow (docs: `doc/input-files.md`, `doc/command-options.md`).
- Group velocity around non-symmorphic degeneracies can be misleading: validate by visual inspection (docs: `example/SnO2/README.md`).

### Convergence and validation checks
- Confirm expected space group with tight tolerance before force runs.
- Verify calculator, distance units, and displacement amplitude are consistent.
- Inspect drift and symmetry enforcement messages when creating force constants.
- Validate primitive/supercell atom mappings before high-cost production runs.

## Scope
- Handle questions about inputs, system setup, models, and physical parameterization.
- Emphasize checks that prevent costly reruns.

## Primary documentation references
- `doc/input-files.md`
- `doc/setting-tags.md`
- `doc/interfaces.md`
- `doc/phonopy-module.md`
- `doc/lammps.md`
- `doc/cp2k.rst`
- `doc/dynamic-structure-factor.md`
- `example/SnO2/README.md`

## Workflow
- Start with references above.
- Use `references/doc_map.md` for complete grouped docs.
- Escalate to `references/source_map.md` for parser/structure implementation details.

## Tutorials and examples
- `example`

## Test references
- `test`

## Optional deeper inspection
- `c`
- `phonopy`

## Source entry points for unresolved issues
- `phonopy/interface/calculator.py`
- `phonopy/interface/cp2k.py`
- `phonopy/interface/lammps.py`
- `phonopy/cui/create_force_sets.py`
- `phonopy/harmonic/force_constants.py`
- `phonopy/harmonic/dynamical_matrix.py`
- `phonopy/structure/symmetry.py`
- `phonopy/structure/dataset.py`
- `phonopy/spectrum/dynamic_structure_factor.py`
- `test/interface/test_qe.py`
- `test/interface/test_lammps.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" c phonopy`).
