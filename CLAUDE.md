# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a LaTeX thesis project for Nanjing University of Posts and Telecommunications (南京邮电大学) bachelor's degree. The thesis topic is "面向实体展览的沉浸式多模态交互系统设计与实现" (Design and Implementation of an Immersive Multimodal Interaction System for Physical Exhibitions).

## Build Commands

```bash
# Compile the thesis (XeLaTeX)
xelatex main.tex

# Full compilation cycle (to include bibliography)
xelatex main.tex
bibtex main
xelatex main.tex
xelatex main.tex
```

For faster iteration during editing, run `xelatex main.tex` twice to get PDF output.

## Repository Structure

- `main.tex` - Thesis main document (content goes here)
- `reference.bib` - Bibliography database
- `njupthesis.cls` - NJUPT thesis LaTeX class file
- `njupthesis.bst` - Bibliography style file
- `pic/` - Images folder (supports eps, jpg, png, pdf)

## Architecture

This is a standalone LaTeX thesis project with no code architecture to speak of. Key files:

- **Template class** (`njupthesis.cls`): Defines NJUPT bachelor's thesis formatting (cover page, abstract styles, chapter/section headings, etc.)
- **Bibliography**: Uses BibTeX with `njupthesis.bst` style, entries in `reference.bib`
- **Citation format**: Use `\citing{key}` (NOT `\cite{key}`) for in-text citations
- **Main document** (`main.tex`): Uses `\chapter{}` for major sections and `\section{}` for subsections

## Important Notes

- Chinese language support via xeCJK package - use XeLaTeX (not pdfLaTeX) for compilation
- The `reference.bib` file uses `language={zh}` for Chinese references with 3+ authors to ensure "等." is displayed correctly instead of "et al."
- For the `\citing{}` command to work with all references, first compile with `latex` then `bibtex` then `latex` twice

## Writing Style Guidelines

- When editing or rewriting sections in `main.tex`, maintain **academic yet natural and fluent** language style
- Avoid overly stiff or bureaucratic phrasing; aim for clear academic prose that reads smoothly
- Balance technical precision with readability
