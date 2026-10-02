---
name: clean-markdown-formatting
description: "Enforces 100% clean GitHub-Flavored Markdown (GFM) by strictly eliminating raw LaTeX, TeX escape sequences, and math delimiter artifacts."
globs: ["*"]
---

# Formatting and Text Cleanliness Rules

## Absolute Ban on LaTeX Formatting and Markup Artifacts
- **NEVER** use LaTeX math formatting, dollar-sign math wrappers, or TeX escape sequences anywhere in conversational responses, markdown documents, or tables.
- **Strictly Banned Patterns**:
  - Arrows: `\rightarrow`, `\leftarrow`, `\to`, `\longrightarrow`, `\Rightarrow`, `\Leftarrow`, or their `$...$` wrapped versions.
  - Math symbols: `\times`, `\ge`, `\le`, `\approx`, `\pm`, `\cdot`, `\neq`, `\sum`, `\frac`.
  - LaTeX wrappers: `$ ... $`, `$$ ... $$`, `\( ... \)`, `\[ ... \]`, `\text{...}`.
- **Allowed Clean Alternatives**:
  - Use simple ASCII or clean Unicode: `->` or `→`, `<-` or `←`, `to`.
  - Multiplication: `*` or `×`.
  - Comparisons: `>=`, `<=`, `>`, `<`.
  - Approximations: `~` or `approx`.
  - Ratios and math: write in plain English or standard arithmetic notation (e.g. `200 / 10 = 20`).
- Ensure all text, formulas, workflows, financial models, and tables read 100% naturally as clean, professional English without raw code or parser debris.
