# no-latex-llm-rules

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/PratikBidve/no-latex-llm-rules/pulls)
[![Compatible with Cursor](https://img.shields.io/badge/Cursor-Compatible-purple)](https://cursor.com)
[![Compatible with Claude Code](https://img.shields.io/badge/Claude%20Code-Compatible-orange)](https://claude.ai)
[![Compatible with Copilot](https://img.shields.io/badge/GitHub%20Copilot-Compatible-black)](https://github.com/features/copilot)

**Stop LLMs from polluting your markdown, PRs, issue comments, and documentation with unrendered LaTeX artifacts.**

Drop-in rule configurations for **Cursor**, **Antigravity**, **Claude Code**, **GitHub Copilot**, and **Windsurf**.

---

## The Problem

Large Language Models (GPT-4o, Claude 3.5 Sonnet, Gemini 1.5/2.0, DeepSeek) are trained extensively on arXiv preprints, academic textbooks, and STEM datasets formatted in LaTeX.

Because of this training bias, models constantly hallucinate raw LaTeX syntax into standard text:
- `$\times$ 100` instead of `× 100` or `* 100`
- `\rightarrow` or `$\to$` instead of `->` or `→`
- `$\ge$` or `\le` instead of `>=` or `<=`
- `$$ ... $$` block wrappers on ordinary arithmetic

In standard **GitHub Flavored Markdown (GFM)**, Slack, Jira, Notion, and terminal CLI outputs, these LaTeX tags **do not render**. Readers see ugly, unparsed parser debris that degrades the quality of PR descriptions, technical documentation, and AI responses.

---

## The Solution: A Zero-Tolerance Markdown Rule

This repository provides ready-to-use rule files that instruct AI assistants to strictly ban LaTeX wrappers and escape sequences, replacing them with clean UTF-8 Unicode or readable ASCII.

### Quick Comparison

| Banned LaTeX Artifact | What Readers See on GitHub | Clean Replacement |
| :--- | :--- | :--- |
| `15 $\times$ 10` | `15 $\times$ 10` | `15 × 10` or `15 * 10` |
| `p95 $\to$ ACK` | `p95 $\to$ ACK` | `p95 -> ACK` or `p95 → ACK` |
| `$\ge$ 90\%` | `$\ge$ 90\%` | `>= 90%` |
| `$\le$ 3s` | `$\le$ 3s` | `<= 3s` |
| `$\approx$ 50` | `$\approx$ 50` | `~ 50` or `approx. 50` |
| `$\pm$ 5%` | `$\pm$ 5%` | `± 5%` |
| `$\neq$ 0` | `$\neq$ 0` | `!= 0` |
| `$\frac{a}{b}$` | `$\frac{a}{b}$` | `a / b` |

---

## 🚀 Quick Install (1-Line Commands)

Run any of the following commands in your project's root directory:

### For Cursor (`.cursor/rules/`)
```bash
mkdir -p .cursor/rules && curl -sSL https://raw.githubusercontent.com/PratikBidve/no-latex-llm-rules/main/rules/clean-markdown.mdc -o .cursor/rules/clean-markdown.mdc
```

### For Antigravity (`.agents/rules/`)
```bash
mkdir -p .agents/rules && curl -sSL https://raw.githubusercontent.com/PratikBidve/no-latex-llm-rules/main/rules/antigravity.md -o .agents/rules/formatting.md
```

### For Claude Code (`.clauderules`)
```bash
curl -sSL https://raw.githubusercontent.com/PratikBidve/no-latex-llm-rules/main/rules/claude.md >> .clauderules
```

### For GitHub Copilot (`.github/copilot-instructions.md`)
```bash
mkdir -p .github && curl -sSL https://raw.githubusercontent.com/PratikBidve/no-latex-llm-rules/main/rules/copilot.md -o .github/copilot-instructions.md
```

### For Windsurf (`.windsurfrules`)
```bash
curl -sSL https://raw.githubusercontent.com/PratikBidve/no-latex-llm-rules/main/rules/windsurf.md >> .windsurfrules
```

---

## Rule Directives Summary

1. **Zero TeX Delimiters:** No single dollar (`$...$`), double dollar (`$$...$$`), parentheses (`\(...\)`), or bracket wrappers (`\[...\]`).
2. **Zero Escaped Commands:** No backslashed commands (`\times`, `\ge`, `\le`, `\to`, `\text{...}`, etc.).
3. **Clean Unicode & ASCII:** Enforce native `×`, `*`, `>=`, `<=`, `->`, `→`, `!=`, `~`.
4. **Natural English:** Mathematical ratios and formulas must read cleanly in plain English without broken parser fragments.

---

## Contributing

Pull requests, additions for other AI tools, and suggestions are welcome!

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/new-tool-rule`)
3. Commit your changes (`git commit -m 'Add rule for X tool'`)
4. Push to the branch (`git push origin feature/new-tool-rule`)
5. Open a Pull Request

---

## License

[MIT License](LICENSE) © 2026 Pratik Bidve
