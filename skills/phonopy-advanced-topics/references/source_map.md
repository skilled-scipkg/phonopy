# phonopy source map: Advanced Topics

Generated from source roots:
- `c`
- `phonopy`
- `test`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Fast source navigation
- `rg -n "<symbol_or_keyword>" phonopy test c`
- `rg -n "^(def |class )" phonopy/cui/*.py phonopy/interface/*.py phonopy/structure/*.py`
- If a doc names a flag/tag, locate parser handling first (`cui/settings.py`, `cui/phonopy_script.py`).

## Suggested source entry points
- `phonopy/scripts/phonopy.py` | command entry flow (`run`)
- `phonopy/cui/phonopy_script.py` | command dispatch and run control
- `phonopy/cui/settings.py` | option/tag parsing classes: `PhonopyConfParser`, `PhonopySettings`
- `phonopy/interface/calculator.py` | calculator mode dispatch and defaults
- `phonopy/interface/phonopy_yaml.py` | `phonopy_xxx.yaml` serialization/load behavior
- `phonopy/structure/symmetry.py` | symmetry search and born/epsilon symmetrization
- `phonopy/cui/show_symmetry.py` | symmetry-report CLI behavior
- `phonopy/phonon/animation.py` | animation output generation
- `phonopy/interface/aims.py` | FHI-aims parser/adapter
- `phonopy/interface/castep.py` | CASTEP parser/adapter
- `phonopy/api_phonopy.py` | high-level integration touchpoint for many advanced options
- `c/tetrahedron_method.c` | numerical kernel implementation used by advanced integration paths
- `c/tetrahedron_method.h` | numerical kernel declarations

## Behavior-check test entry points
- `test/interface/test_phonopy_yaml.py` | yaml parsing/dumping behavior checks
- `test/structure/test_symmetry.py` | symmetry and NAC-related behavior checks
- `test/interface/test_castep.py` | CASTEP parser behavior checks
- `test/interface/test_conversion.py` | interface conversion and consistency checks
- `test/cui/phonopy_command/test_phonopy_script.py` | command option/tag behavior checks
