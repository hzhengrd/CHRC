# Compatibility Decision Matrix

Application of Supplementary Table S3 (compatibility decision rules) of the manuscript to the three worked-example resources. Each pair is assessed along the nine compatibility dimensions; the overall verdict follows the most restrictive dimension.

## Resources

| ID | Resource | Focal setting | Character |
|----|----------|---------------|-----------|
| A | `wang2021-digital-twin` | Drywall installation, laboratory mock-up | Integrated (task + robot + work-object + relations) |
| B | `pan2023-primitives` | Scaffolding videos | Task-deep (4-level task hierarchy, no robot) |
| C | `wang2023-wearable` | Tower-crane operation | Human-deep (gesture commands, no robot) |

## Verdicts

- **DC** = directly combinable
- **CT** = combinable after documented transformation
- **NP** = comparable but not validly poolable

## Summary

| Dimension | A ↔ B | B ↔ C | A ↔ C |
|-----------|:-----:|:-----:|:-----:|
| 1. Information meaning | NP | NP | NP |
| 2. Unit of observation | NP | NP | NP |
| 3. Measurement and encoding | NP | NP | NP |
| 4. Spatial reference | NP | NP | NP |
| 5. Temporal reference | NP | NP | NP |
| 6. Identity and relations | NP | NP | NP |
| 7. Task and environmental context | NP | NP | NP |
| 8. Provenance and quality | NP | NP | NP |
| 9. Governance | NP | NP | NP |
| **Overall** | **NP** | **NP** | **NP** |

## Per-pair justification

### A ↔ B (digital twin ↔ task primitives)

Primary blockers: **spatial reference absent in B**, **temporal reference not aligned**, **no relations in B**, and **different focal tasks** (drywall vs. scaffolding). Both record `task.structure`, but A's structure is a robot task plan while B's is a four-level human action hierarchy; the two are not the same operational construct.

### B ↔ C (task primitives ↔ wearable gestures)

Primary blockers: **no shared referent** (B records `task.structure`; C records `human.action`/`human.intent`), **spatial reference absent in both**, and **different focal tasks** (scaffolding vs. tower crane). The two resources are complementary but do not overlap on any category whose values could be pooled.

### A ↔ C (digital twin ↔ wearable gestures)

Primary blockers: **spatial/temporal reference absent in C**, **no relations in C**, and **different focal tasks** (drywall vs. tower crane). Both record `human.action`, but A's action is a worker installation operation and C's action is a gesture command; the operational definitions differ.

## Interpretation

None of the three pairs is currently poolable. This is not a failure of the decision rules: it is the corpus-level fragmentation documented in the manuscript, made explicit and *decidable* at the level of a single resource pair. For each pair, the matrix names the exact dimensions that block pooling — predominantly the absence of a shared spatial reference, the absence of a shared temporal anchor, and the absence of explicit cross-referent relations. Those are precisely the fields the resource profile and the collaborative-episode graph require. As resources begin to carry those references and relations, the same rules would reclassify affected dimensions as *combinable after documented transformation*, enabling partial and heterogeneous resources to accumulate as evidence.
