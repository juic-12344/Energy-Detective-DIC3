# Energy Detective — IEEE conference draft (DIC4)

**Title:** Energy Detective: An Evidence-Traceable AI Agent for Household Electricity Analytics

**Status:** 4-page conference-format research draft; not a completed empirical study. Current author block uses Group 20 and National Chung Hsing University; confirm individual English author names before submission.

## Build

`main.tex` is the project root; `references.tex` contains IEEE-numbered references. `IEEEtran.cls` is the unmodified v1.8b class (LPPL 1.3, copyright Michael Shell and contributors; see its license header and [CTAN](https://ctan.org/pkg/ieeetran)). Architecture is editable TikZ.

```bash
latexmk -pdf main.tex
```

For Overleaf, ZIP `main.tex`, `references.tex`, and `IEEEtran.cls` at the root of the archive. In Overleaf choose New Project → Upload Project and compile with pdfLaTeX. Local compilation has been verified; an authenticated Overleaf import is pending.

See the [DIC4 plan](../myplan/DIC4-plan.md) and the [OpenSpec change](../openspec/changes/draft-conference-paper/).
