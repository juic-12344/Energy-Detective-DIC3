# Design — DIC4 conference paper

## Context

Energy Detective is a proposal-stage read-only household electricity analytics agent. The source design is the DIC3 `DESIGN.md`, existing `docs/` materials and latest Final Project Proposal (2026-11-24). DIC4 adds a paper-writing change without superseding the separate implementation plan. There are no trained models or measured experimental results.

## Goals / Non-Goals

**Goals**
- Produce an IEEE conference-mode, two-column English LaTeX draft, editable and compilable in Overleaf.
- Preserve the original technical parameters, research questions, references, and evidence/limitation contracts.
- Establish a spec-driven process with auditable acceptance scenarios and checks.

**Non-goals**
- Submission to a real research conference or automatic external sharing.
- Implementation, model training, new data collection, measured improvements, or appliance control.
- Choosing an LLM provider or model before implementation.

## Decisions

1. **IEEEtran in conference mode.** The root file is `paper/main.tex`, class version 1.8b is included for portability, and `references.tex` carries numbered IEEE-style citations. The diagram is editable TikZ rather than a flat screenshot. This preserves typography and allows all paper content to be revised on Overleaf.
2. **Manuscript structure.** The A–F proposal story maps into the abstract and introduction. The original research synthesis maps into Related Work. The eight-module architecture, controlled data view, RF forecast, MAD heuristic, evidence contract, and bounded algorithm map into System Design and Evidence and Response Verification. Evaluation and Expected Outcomes remain prospective.
3. **Preserve design invariants.** Use minute-to-kWh conversion, 60 valid distinct minutes for a complete hour, no future visibility, no zero imputation, same-day-type 56-day MAD reference (minimum 14, threshold 3.5), RF candidate with 200/12/5/42 initial parameters, 70/15/15 chronological partition, and a maximum of eight tool attempts plus one repair. The experiment has ten pilot and 50 formal tasks, two conditions, three repetitions (300 planned executions). Report MAE, RMSE, availability, correctness, evidence, limitation handling and overhead.
4. **No unsupported claims.** Cite the original dataset and relevant literature. Use Group 20 and National Chung Hsing University provisionally; confirmed English author names must be supplied before submission. Do not attribute causal savings or fault identification to the system.
5. **MCP + OpenSpec workflow.** Read the DIC3 GitHub sources through GitHub MCP, use OpenSpec CLI to create and validate this change, build the manuscript locally using pdfLaTeX, and publish the new text artifacts via the GitHub MCP. The Overleaf account requires authentication before a live project can be created; the LaTeX ZIP is import-ready, not evidence that Overleaf hosted the project.

## Risks / Trade-offs

| Risk | Mitigation |
|---|---|
| Proposal mistaken for a completed study | Use planned/expected language and omit fabricated results. |
| Paper and original design drift apart | Maintain the mapping in `myplan/DIC4-plan.md`; check numerical invariants before each build. |
| Overleaf account access unavailable | Supply a root-level project ZIP (`main.tex`, class, references) that compiles locally. |
| English author spelling uncertain | Group identifier is used until members confirm spelling; do not invent romanization. |
| Template compilation varies by environment | Store class and editable sources; verify local PDF with pdfLaTeX and inspect every page. |

## Verification

Run `openspec validate draft-conference-paper --strict` and check status. Compile twice (or use `latexmk -pdf main.tex`), inspect references and warnings, then visually review the four-page PDF. Verify repository files and completed GitHub commit. Upload the ZIP on Overleaf, compile, and confirm project ownership/authors before submission. Archive this OpenSpec change only when remaining actions are complete.
