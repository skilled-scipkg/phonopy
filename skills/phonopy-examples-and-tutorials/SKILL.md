---
name: phonopy-examples-and-tutorials
description: Use this skill when users want runnable example pathways, calculator-specific sample commands, or tutorial-like adaptation patterns from the shipped phonopy examples.
---

# phonopy: Examples and Tutorials

## High-Signal Playbook
### Route conditions
- Use this skill when the request is "show me a working example" or "adapt this example to my calculator/system".
- Route to `phonopy-simulation-workflows` if the user needs a full troubleshooting flow beyond example reproduction.
- Route to `phonopy-api-and-scripting` for Python-first automation instead of CLI-oriented examples.

### Triage questions
- Which example family matches the calculator (`qe`, `cp2k`, `wien2k`, `lammps`, `pwmat`, `aims`)?
- Does the user need finite-displacement or random-displacement (`--rd`) examples?
- Is symmetry intentionally disabled (`--nosym`) or reduced?
- Is the goal bands, irreps, DOS, or animation output?
- Are they running directly in an example directory or adapting to external input files?

### Canonical workflow
1. Pick the closest example README (`example/NaCl-QE/README.md`, `example/Si-CP2K/README.md`, `example/Si-lammps/README.md`, etc.) to the user calculator and objective.
2. Run the exact preprocess command from that README to create supercells and `phonopy_disp.yaml`.
3. Run external force calculations for each displaced supercell.
4. Create `FORCE_SETS` with the interface-aware command in the same directory.
5. Run postprocess (`phonopy-load ...`) and compare output shape/paths with README expectations.
6. Only then replace example inputs with user structures while keeping command skeleton unchanged.

### Minimal working example
```bash
# QE example pattern (example/NaCl-QE)
phonopy --qe -c NaCl.in -d --dim 2 2 2 --pa auto
phonopy -f NaCl-001.out NaCl-002.out
phonopy-load --band "0 0 0  0.5 0 0  0.5 0.5 0  0 0 0  0.5 0.5 0.5" -p

# Random-displacement pattern (example/NaCl-rd)
phonopy --rd 10 --dim 2 2 2 --pa auto --amplitude 0.03 -c POSCAR-unitcell
phonopy -f force-calcs/disp-{001..010}/vasprun.xml
```

### Pitfalls and fixes
- Mixed command styles from different examples: keep one example family end-to-end before mixing options.
- Missing `phonopy_disp.yaml` at force-import time: run `-f` in the displacement generation directory.
- `--nosym` unexpectedly increases displacement count: expected behavior (docs: `example/LiF-nosym/README.md`).
- LAMMPS force orientation mismatch: use generated structure files and let phonopy rotate parsed forces as documented (docs: `example/Si-lammps/README.md`, `doc/lammps.md`).
- Auto labels/paths differ by calculator: keep interface flags consistent (`--qe`, `--cp2k`, `--wien2k`, etc.).

### Convergence and validation checks
- Verify the number of displaced supercells matches README expectations.
- Check that parser input filenames match interface-specific patterns.
- Compare band path outputs with the example command strings before adapting.
- Confirm generated outputs (`FORCE_SETS`, `phonopy.yaml`, plots) exist and are non-empty.

## Scope
- Handle questions about worked examples, tutorials, and cookbook usage.
- Keep answers compact and execution-oriented.

## Primary documentation references
- `example/NaCl-QE/README.md`
- `example/Si-CP2K/README.md`
- `example/NaCl-CP2K/README.md`
- `example/NaCl-wien2k/README.md`
- `example/Si-PWmat/README.md`
- `example/Si-lammps/README.md`
- `example/LiF-nosym/README.md`
- `example/ZnO/README.md`
- `example/TiO2-anatase/README.md`
- `example/MgO/README.md`
- `example/MgB2/README.md`
- `doc/random-displacements.md`

## Workflow
- Start with the references above.
- Use `references/doc_map.md` for the full example inventory.
- Escalate to `references/source_map.md` only for parser/implementation ambiguity.

## Tutorials and examples
- `example`

## Test references
- `test`

## Optional deeper inspection
- `c`
- `phonopy`

## Source entry points for unresolved issues
- `phonopy/phonon/random_displacements.py`
- `phonopy/interface/qe.py`
- `phonopy/interface/cp2k.py`
- `phonopy/interface/wien2k.py`
- `phonopy/interface/pwmat.py`
- `phonopy/interface/aims.py`
- `phonopy/interface/lammps.py`
- `phonopy/scripts/phonopy_load.py`
- `phonopy/api_phonopy.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" c phonopy`).
