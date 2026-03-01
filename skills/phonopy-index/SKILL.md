---
name: phonopy-index
description: Use this router skill to classify phonopy requests into the right topic skill quickly, keeping docs-first behavior and escalating to source only when needed.
---

# phonopy Skills Index

## Route the request
- Start docs-first: classify the request into the smallest matching topic skill below.
- Prefer workflow-level guidance first; escalate to source only if docs are ambiguous.
- For narrow one-doc reference topics (tags, symmetry note, citation/changelog, specific interfaces), route to `phonopy-advanced-topics`.

## Generated topic skills
- `phonopy-simulation-workflows`: end-to-end preprocess/force-import/postprocess flows, restart loops, multi-volume workflows.
- `phonopy-examples-and-tutorials`: runnable example adaptation by calculator and use case.
- `phonopy-api-and-scripting`: CLI families, Python API entry points, automation patterns.
- `phonopy-inputs-and-modeling`: input formats, key tags, structure/force-constant modeling choices.
- `phonopy-analysis-and-output`: output semantics, plotting, QHA and post-processing.
- `phonopy-build-and-install`: installation/build prerequisites and environment setup.
- `phonopy-test`: regression triage and focused test routing.
- `phonopy-general`: project-level documentation navigation.
- `phonopy-advanced-topics`: consolidated low-signal single-doc topics (command options, setting tags, symmetry, theory notes, citation/changelog, specialized small interface docs).

## First simulation bootstrap
- Use `phonopy-build-and-install` first when environment status is unknown.
- Start from a known runnable example (for example `example/NaCl` or `example/Si`) and follow:
  - `phonopy -d --dim 2 2 2 --pa auto -c POSCAR-unitcell`
  - external force calculations on displaced supercells
  - `phonopy -f disp-{001..002}/vasprun.xml`
  - `phonopy-load --mesh 20 20 20 -t`
- Validate that `phonopy_disp.yaml` and `FORCE_SETS` exist before expensive production runs.

## Documentation-first inputs
- `doc`

## Tutorials and examples roots
- `example`

## Test roots for behavior checks
- `test`

## Escalate only when needed
- Start from the selected topic skill primary references.
- If needed, use that skill's `references/doc_map.md`.
- If docs are still insufficient, use that skill's `references/source_map.md` and inspect ranked entry points.
- Use targeted symbol search (e.g., `rg -n "<symbol_or_keyword>" c phonopy`).

## Source directories for deeper inspection
- `c`
- `phonopy`
