## ADDED Requirements

### Requirement: Editable IEEE conference manuscript
The project SHALL maintain the Energy Detective research draft in an editable IEEEtran conference-mode LaTeX document with the necessary source files and IEEE-style numbered references.

#### Scenario: Build draft from the source package
- **WHEN** the manuscript is compiled with pdfLaTeX using `paper/main.tex`
- **THEN** the output SHALL be a two-column conference-format PDF with abstract, keywords, introduction, related work, system design, evaluation plan, limitations, conclusion, and references
- **AND** referenced figures, tables, equations, and bibliography entries SHALL resolve without missing-reference errors

#### Scenario: Edit on Overleaf
- **WHEN** the provided project ZIP is imported into an authenticated Overleaf project and `main.tex` is compiled with pdfLaTeX
- **THEN** the LaTeX manuscript and diagram source SHALL remain editable and the user SHALL be able to regenerate the PDF

### Requirement: Research-design traceability
The manuscript SHALL faithfully represent the DIC3 design and distinguish observed historical values, predictions, anomaly candidates, and recommendations.

#### Scenario: Audit methods against source design
- **WHEN** the methods and evaluation protocol are reviewed against `DESIGN.md` and the DIC3 proposal
- **THEN** data visibility, energy conversion, complete-hour requirements, MAD and RF parameters, call and repair limits, train/validation/test split, baselines and the paired task plan SHALL remain consistent
- **AND** the paper SHALL label the experiments as planned unless actual validated results exist

#### Scenario: Evidence unavailable
- **WHEN** no model results or actual energy savings are available
- **THEN** the manuscript SHALL not present fabricated scores or measured savings and SHALL disclose the scope and limitations

### Requirement: Specification and version provenance
The DIC4 manuscript workflow SHALL be tracked as a distinct OpenSpec change in the Energy Detective GitHub repository, preserving the existing DIC3 proposal and implementation change.

#### Scenario: Review DIC4 on GitHub
- **WHEN** a reviewer opens `openspec/changes/draft-conference-paper/`
- **THEN** the proposal, design, delta spec, and task checklist SHALL be accessible
- **AND** the manuscript files and a mapping from DIC3 to DIC4 SHALL be discoverable through the root README

#### Scenario: Audit completion
- **WHEN** a task is checked as complete
- **THEN** it SHALL have corresponding evidence such as source files, successful validation, a compiled PDF or a verified repository update
- **AND** any uncompleted Overleaf-specific action SHALL remain explicitly unchecked
