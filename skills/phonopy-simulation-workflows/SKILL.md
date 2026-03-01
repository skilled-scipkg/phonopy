---
name: phonopy-simulation-workflows
description: Use this skill for end-to-end phonopy execution flows (preprocess, force collection, postprocess, restart paths) across calculators, with docs-first routing and source escalation for unresolved behavior.
---

# phonopy: Simulation Workflows

## High-Signal Playbook
### Route conditions
- Use this skill when the user asks how to run phonopy end-to-end (finite displacement, DFPT readfc, gruneisen, phonopy-load postprocess).
- Route to `phonopy-inputs-and-modeling` when the main blocker is file/tag semantics.
- Route to `phonopy-analysis-and-output` when the run already succeeded and the question is only plotting/QHA/output interpretation.

### Triage questions
- Which calculator interface is used (`vasp`, `qe`, `cp2k`, `lammps`, etc.)?
- Are you starting from forces (`FORCE_SETS`) or already have force constants (`FORCE_CONSTANTS`/`force_constants.hdf5`)?
- What are `--dim` and primitive axes (`--pa` or `PRIMITIVE_AXES`)?
- Is NAC required (`BORN` present, polar material)?
- What output is needed first: bands, DOS, thermal properties, or Gruneisen?
- Are you rerunning after a failure, or building a fresh run directory?

### Canonical workflow
1. Prepare/relax the unit cell outside phonopy, then keep atomic positions fixed for displaced-supercell force runs (docs: `doc/vasp.md`, `doc/qe.md`, `doc/cp2k.rst`).
2. Create displaced supercells: `phonopy -d --dim ... --pa auto -c <unitcell>` (docs: `doc/vasp.md`, `doc/qe.md`).
3. Run calculator forces for each displaced supercell (no relaxation of displaced cells).
4. Build displacement-force dataset: `phonopy -f ...` (or interface-specific variant) with `phonopy_disp.yaml` in the same directory.
5. Run postprocess with `phonopy-load` for mesh/band/thermal tasks (docs: `doc/phonopy-load.md`).
6. For DFPT VASP runs, generate and read force constants directly: `phonopy --fc vasprun.xml`, then `phonopy-load --readfc ...` (docs: `doc/vasp-dfpt.md`).
7. For volume workflows, run three-volume Gruneisen or multi-volume QHA on top of converged per-volume phonons (docs: `doc/gruneisen.md`, `doc/workflow.md`).

### Minimal working example
```bash
# Finite-displacement NaCl/Si-style flow (VASP-like)
phonopy -d --dim 2 2 2 --pa auto -c POSCAR-unitcell
phonopy -f disp-{001..002}/vasprun.xml
phonopy-load --mesh 20 20 20 -t -p
phonopy-load --band "0.5 0.5 0.5  0 0 0  0.5 0.5 0" -p
```

### Pitfalls and fixes
- Displaced supercells were relaxed: rerun force jobs with fixed displaced structures (docs: `doc/vasp.md`, `doc/qe.md`, `doc/cp2k.rst`).
- `phonopy -f` cannot map forces: ensure `phonopy_disp.yaml` is in the current directory (docs: `doc/qe.md`, `doc/input-files.md`).
- `phonopy-load` behavior differs from `phonopy`: provide `phonopy_xxx.yaml` input or keep `phonopy_disp.yaml`/`phonopy.yaml` in cwd (docs: `doc/phonopy-load.md`).
- Unexpected LO-TO behavior: verify `BORN`; disable with `--nonac` if needed (docs: `doc/phonopy-load.md`, `doc/vasp.md`, `doc/qe.md`).
- Gruneisen bands look unordered near crossings: expected due to mode connection handling (docs: `doc/gruneisen.md`).

### Convergence and validation checks
- Converge q-mesh for thermal properties and DOS (docs: `doc/vasp.md`).
- Confirm expected space group/supercell in command output before long runs.
- Check force-constant drift/symmetrization logs in postprocess output.
- Verify output artifacts exist (`phonopy.yaml`, `band.yaml`, `thermal_properties.yaml`, etc.).
- Flag persistent imaginary branches (outside known instabilities) as modeling/convergence issues.

## Scope
- Handle questions about simulation setup, execution flow, and runtime controls.
- Keep responses docs-first, then escalate to source only for unresolved behavior details.

## Primary documentation references
- `doc/workflow.md`
- `doc/phonopy-load.md`
- `doc/vasp.md`
- `doc/vasp-dfpt.md`
- `doc/qe.md`
- `doc/cp2k.rst`
- `doc/gruneisen.md`
- `example/NaCl/README.md`
- `example/Si/README.md`
- `example/NaCl-VASPdfpt/README.md`
- `example/NaCl-rd/README.md`
- `example/KCl-SSCHA/README.md`

## Workflow
- Start with the references above.
- If details are missing, inspect `references/doc_map.md` for the full grouped docs.
- Use `references/source_map.md` only when docs leave ambiguity.
- Cite exact file paths when answering.

## Tutorials and examples
- `example`

## Test references
- `test`

## Optional deeper inspection
- `c`
- `phonopy`

## Source entry points for unresolved issues
- `phonopy/scripts/phonopy_load.py`
- `phonopy/cui/load.py`
- `phonopy/cui/load_helper.py`
- `phonopy/cui/create_force_sets.py`
- `phonopy/interface/vasp.py`
- `phonopy/interface/qe.py`
- `phonopy/interface/cp2k.py`
- `phonopy/interface/lammps.py`
- `phonopy/scripts/phonopy_gruneisen.py`
- `phonopy/gruneisen/core.py`
- `phonopy/sscha/core.py`
- `phonopy/api_gruneisen.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" c phonopy`).
