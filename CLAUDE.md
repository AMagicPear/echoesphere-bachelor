# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

NJUPT bachelor's thesis: "面向实体展览的沉浸式多模态交互系统设计与实现" (Design and Implementation of an Immersive Multimodal Interaction System for Physical Exhibitions). A LaTeX document with custom class and bibliography style.

## Build Commands

```bash
# One-shot full compilation
xelatex main.tex && bibtex main && xelatex main.tex && xelatex main.tex

# Quick edit check (just LaTeX, no bib)
xelatex main.tex
```

Always use XeLaTeX (not pdfLaTeX) for CJK support.

## Document Structure (main.tex)

- **Preamble**: `\documentclass[bachelor]{njupthesis}`, metadata fields (title, author, advisor, etc.)
- **Front matter**: `\makecover`, `chineseabstract`/`englishabstract` environments, `\thesistableofcontents`, `\thesischapterexordium`
- **6 body chapters**: 绪论 → 文献综述 → 需求分析与总体设计 → 交互系统和配套应用实现 → 应用场景演示与测试 → 总结与展望
- **Back matter**: `\chapter*{结束语}`, `\thesisacknowledgement`, `\thesisloadbibliography[nocite]{reference}`, appendix

### Key LaTeX Commands (from njupthesis.cls)

| Command | Purpose |
|---------|---------|
| `\citing{key}` | Superscript citation (NOT `\cite`) |
| `\thesisloadbibliography[nocite]{reference}` | Loads refs with `\nocite{*}` |
| `\thesischapterexordium` | Starts Arabic page numbering before Ch1 |
| `\thesisacknowledgement` | 致谢 section |
| `\thesisappendix` | Appendix wrapper |

## Custom Class (njupthesis.cls)

- Based on `book` class (12pt, openany, twoside)
- CJK fonts via xeCJK: macOS uses Songti SC / Heiti SC / Kaiti SC; Windows uses SimSun / SimHei / STKaiti
- `\begin{spacing}{1.391}` wraps bibliography for line spacing
- `\cite` is wrapped by `\citing` for superscript output

## Bibliography Style (njupthesis.bst)

Based on **gbt7714-2025-numeric.bst** (https://github.com/zepinglee/gbt7714-bibtex-style) with these customizations:

1. **`output.bibitem`**: Writes `\bibitem{key}` (no author-year label) for `[1]` auto-numbering
2. **`begin.bib`**: Uses `{lo}` label width, sets `\interlinepenalty=10000`, `\small`, zero itemsep/parskip
3. **`control.sentence.case.title`** = 0 (keeps original title capitalization)

### Citation Keys

The BST auto-detects language and uses:
- Chinese entries: 等 (not et al.)
- English entries: et~al
- `[J]` / `[J/OL]` for journal articles
- `[EB/OL]` for web resources (@misc)
- `[C]` for conference papers
- `[M]` for books
- `[D]` for theses

### reference.bib Rules

- Chinese entries must use **`language = {chinese}`** (NOT `{zh}` — gbt7714 won't recognize it)
- English entries can use `language = {english}` or omit the field (auto-detected)
- Use `author = {{Corporate Name}}` (double braces) for corporate authors like `{Epic Games}` or `{Qwen Team}`
- DOI field is supported and auto-links via `\doi{}`
- For @misc entries, URL + year are the primary fields; urldate is optional

## Writing Style

- Academic but natural prose — avoid bureaucratic stiffness
- Balance technical precision with readability
- Use Chinese punctuation (，。等) in Chinese text
- Ensure Chinese quotation marks  “ ” are paired correctly
