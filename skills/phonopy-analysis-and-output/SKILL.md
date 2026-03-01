---
name: phonopy-analysis-and-output
description: Use this skill for interpreting phonopy result files, plotting outputs, and running QHA/post-processing pipelines.
---

# phonopy: Analysis and Output

## High-Signal Playbook
### Route conditions
- Use this skill when users ask what output files mean, how to plot them, or how to compute thermodynamic quantities (including QHA).
- Route to `phonopy-simulation-workflows` if outputs are missing due to upstream run failures.
- Route to `phonopy-advanced-topics` for detailed option/tag lookups.

### Triage questions
- Which outputs are already available (`band.yaml`, `mesh.yaml`, `thermal_properties.yaml`, `phonopy.yaml`, etc.)?
- Is the goal quick plotting, quantitative extraction, or QHA fitting?
- Are multiple volumes prepared for QHA in consistent order and temperature grid?
- Is PDOS needed by atom blocks or projected directions?

### Canonical workflow
1. Generate the required output mode via `phonopy-load` (band, mesh/DOS, thermal properties).
2. Inspect YAML/dat semantics from `doc/output-files.md` before plotting.
3. Plot with dedicated tools:
   - `phonopy-bandplot` for band outputs,
   - `phonopy-pdosplot` for DOS files,
   - `phonopy-propplot` for thermal properties.
4. For QHA, prepare `e-v.dat` plus ordered `thermal_properties.yaml-*` volume series and run `phonopy-qha`.
5. Validate smoothness and physical plausibility before downstream reporting.

### Minimal working example
```bash
phonopy-load --band auto -p
phonopy-bandplot --gnuplot band.yaml
phonopy-load --mesh 20 20 20 -t
phonopy-propplot thermal_properties.yaml
phonopy-qha -p e-v.dat thermal_properties.yaml-{00..10}
```

### Pitfalls and fixes
- QHA with too few volumes: provide at least 5 points (docs: `doc/qha.md`).
- QHA file order mismatch: ensure thermal-property files follow the same volume order as `e-v.dat` (docs: `doc/qha.md`).
- Inconsistent temperature grids across volume datasets: regenerate thermal properties with identical `TMIN/TMAX/TSTEP`.
- Misread PDOS columns: PDOS ordering follows primitive-cell atom order (docs: `doc/output-files.md`).
- Overinterpreting unconverged mesh data: increase mesh density and recheck trends.

### Convergence and validation checks
- Verify expected files exist and are non-empty after each mode.
- Check q-mesh convergence for DOS/thermal quantities.
- Ensure QHA outputs are smooth (`volume-temperature`, `bulk_modulus-temperature`, `Cp-temperature`).
- Treat persistent imaginary frequencies in nominally stable systems as a warning for upstream setup issues.

## Scope
- Handle questions about output formats, analysis, and post-processing.
- Keep explanation tied to concrete files and scripts.

## Primary documentation references
- `doc/output-files.md`
- `doc/auxiliary-tools.md`
- `doc/qha.md`

## Workflow
- Start with docs above.
- Use `references/doc_map.md` for broader output-related docs.
- Escalate to `references/source_map.md` for implementation behavior.

## Tutorials and examples
- `example`

## Test references
- `test`

## Optional deeper inspection
- `c`
- `phonopy`

## Source entry points for unresolved issues
- `phonopy/api_qha.py`
- `phonopy/qha/core.py`
- `phonopy/qha/eos.py`
- `phonopy/scripts/phonopy_qha.py`
- `phonopy/scripts/phonopy_bandplot.py`
- `phonopy/scripts/phonopy_pdosplot.py`
- `phonopy/scripts/phonopy_propplot.py`
- `phonopy/scripts/phonopy_tdplot.py`
- `test/qha/test_QHA.py`
- `test/spectrum/test_dynamic_structure_factor.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" c phonopy`).
