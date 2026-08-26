# CHRC Data Infrastructure — Public Assets

Public, machine-readable assets accompanying the manuscript:

> **A Data-Centric Perspective on Construction Human–Robot Collaboration: Taxonomy, Landscape, and Infrastructure**

## Contents

| Directory | What it holds |
|-----------|---------------|
| `vocab/` | The CHRC vocabulary (`chrc.ttl`) and the JSON-LD `@context` (`context.jsonld`). |
| `schemas/` | `resource-profile.schema.json` (JSON Schema for the resource profile) and `episode-graph.shacl.ttl` (SHACL shapes for the collaborative-episode graph). |
| `examples/` | Worked examples: a resource profile (JSON-LD) and a collaborative-episode graph (RDF/Turtle) for three published resources. |
| `compatibility/` | The applied compatibility decision matrix (instantiation of Supplementary Table S3 of the manuscript). |
| `review/` | The systematic-review coding data: codebook, per-resource coding table, and the PRISMA exclusion list. |

## Namespace

- Vocabulary IRI prefix: `https://hzhengrd.github.io/CHRC/vocab/chrc#`
  - Example: `chrc:Human` = `https://hzhengrd.github.io/CHRC/vocab/chrc#Human`
- Example instance namespace: `https://hzhengrd.github.io/CHRC/examples/<resource>/`

## Status

These files are **reference implementations** accompanying the manuscript. They are offered as guidance for a future implementation, not as a finished production system.

## Citation

TODO: add the Zenodo DOI after archiving this repository.
