# DIC4 — IEEE conference manuscript

## Why

DIC3 established the Energy Detective proposal and implementation specifications, but the research design is not yet a conference-style manuscript. DIC4 requires an editable IEEE conference draft for Overleaf and a version-controlled OpenSpec workflow; the draft must preserve the original design and accurately distinguish planned experiments from results.

## What Changes

- Produce an English IEEEtran conference-mode LaTeX manuscript with an abstract, introduction, related work, design, algorithm, evaluation, limitations, conclusion and references.
- Develop editable architecture diagram, equations and evaluation tables derived from DIC3 and the latest DESIGN.md.
- Provide a reproducible compilation package for Overleaf and retain the manuscript source on GitHub.
- Record the manuscript requirements, design choices, verification and remaining actions in OpenSpec.
- Keep the DIC3 implementation change separate and unchanged; this change does not implement the energy agent or invent results.

## Capabilities

### New Capabilities

- `conference-manuscript`: Maintain a reproducible, editable IEEE conference manuscript and truthful research/evaluation status with a traceable relationship to the existing proposal.

### Modified Capabilities

None. The existing `implement-energy-detective` proposal and its data, agent and evaluation specs remain independent.

## Impact

New files under `paper/`, `myplan/`, and `openspec/changes/draft-conference-paper/`; the root README gains a DIC4 navigation entry. Requires IEEEtran and standard LaTeX packages, and uses OpenSpec CLI and GitHub MCP for the specification/version-control workflow. No runtime model, API provider, dataset, or appliance control is changed.
