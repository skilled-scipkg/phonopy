---
name: phonopy-advanced-topics
description: Consolidated reference skill for low-signal single-doc phonopy topics (command/tag reference, symmetry notes, citation/changelog, and focused interface docs) with targeted source entry points.
---

# phonopy: Advanced Topics

## Scope
- Handle narrow, documentation-centric topics that were each represented by one file.
- Keep responses concise and cite exact doc paths.

## Route the request
- Command-line flag lookup or option equivalence -> `doc/command-options.md`.
- Setting-file tag semantics (`DIM`, `PRIMITIVE_AXES`, etc.) -> `doc/setting-tags.md`.
- `phonopy_xxx.yaml` storage/compression and PhononDB usage -> `doc/phonopy-yaml.md`.
- Symmetry tolerance checks and standardized cell usage -> `doc/symmetry.md`.
- Animation output (`ANIME`, `anime.ascii`, v_sim usage) -> `doc/animation.md`.
- FHI-aims or CASTEP calculator-specific quick references -> `doc/aims.rst`, `doc/castep.rst`.
- Theory/reference and citation history -> `doc/reference.md`, `doc/citation.md`, `doc/changelog.md`.

## Primary documentation references
- `doc/aims.rst`
- `doc/animation.md`
- `doc/castep.rst`
- `doc/changelog.md`
- `doc/citation.md`
- `doc/command-options.md`
- `doc/phonopy-yaml.md`
- `doc/setting-tags.md`
- `doc/symmetry.md`
- `doc/reference.md`

## Workflow
- Start with the exact topic doc above.
- If details are missing, inspect `references/doc_map.md` for combined inventory.
- Escalate only when needed via `references/source_map.md`.

## Tutorials and examples
- `example`

## Test references
- `test`

## Optional deeper inspection
- `c`
- `phonopy`

## Source entry points for unresolved issues
- `phonopy/scripts/phonopy.py`
- `phonopy/cui/phonopy_script.py`
- `phonopy/cui/settings.py`
- `phonopy/interface/phonopy_yaml.py`
- `phonopy/structure/symmetry.py`
- `phonopy/cui/show_symmetry.py`
- `phonopy/phonon/animation.py`
- `phonopy/interface/aims.py`
- `phonopy/interface/castep.py`
- `phonopy/interface/calculator.py`
- `phonopy/api_phonopy.py`
- `c/tetrahedron_method.c`
- `c/tetrahedron_method.h`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" c phonopy`).
