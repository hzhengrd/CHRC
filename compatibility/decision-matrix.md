# Compatibility Decision Matrix

Application of Supplementary Table S3 (compatibility decision rules) of the manuscript to the four worked-example resources. Each pair is assessed along the nine compatibility dimensions; the overall verdict follows the most restrictive dimension.

## Resources

| ID | Resource | Focal setting | Character | Access tier |
|----|----------|---------------|-----------|-------------|
| A | `wang2021-digital-twin` | Drywall installation, laboratory mock-up | Integrated (task + robot + work-object + relations) | on-request |
| B | `wang2023-gaze-aware` | Construction commands, laboratory mock-up | Human-deep (gaze + hand gestures, no robot) | open |
| C | `pan2023-task-primitives` | Scaffolding videos | Task-deep (four-level hierarchy, no robot) | metadata-only |
| D | `rossini2026-concert` | Drilling / sanding / plastering, on-site | Robot-deep (module descriptions + meshes) | open |

## Verdicts

- **DC** = directly combinable
- **CT** = combinable after documented transformation
- **NP** = comparable but not validly poolable

## Summary

| Pair | Overall | Primary blockers |
|------|:-------:|------------------|
| A ↔ B | NP | spatial/temporal reference absent in B; no relations in B; task context differs |
| A ↔ C | NP | spatial/temporal reference absent in C; no relations in C; task context differs |
| A ↔ D | NP | different robots and tasks; no shared reference frames; governance differs |
| B ↔ C | NP | no shared referent; no shared references; task context differs |
| B ↔ D | NP | complementary referents (human vs robot) with no shared references |
| C ↔ D | NP | different referents (task vs robot); no shared references; governance differs |

Per-dimension detail is provided in `decision-matrix.csv`.

## Interpretation

None of the six pairs is currently poolable. This is not a failure of the decision rules: it is the corpus-level fragmentation documented in the manuscript, made explicit and *decidable* at the level of individual resource pairs. For each pair, the matrix names the exact dimensions that block pooling — predominantly the absence of a shared spatial reference, the absence of a shared temporal anchor, the absence of explicit cross-referent relations, and divergent focal tasks. Those are precisely the fields the resource profile and the collaborative-episode graph make explicit. As resources begin to carry those references and relations, the same rules would reclassify affected dimensions as *combinable after documented transformation*, enabling partial and heterogeneous resources to accumulate as evidence.
