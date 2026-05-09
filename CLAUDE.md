# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

A collection of LaTeX engineering mathematics notes, organised by subject. Each subject compiles to a standalone PDF book.

## Viewing the Notes (Overleaf — no install required)

1. Zip the repo from the Desktop (excludes git history):
   ```bash
   cd /Users/macbook/Desktop && zip -r maths.zip maths/ --exclude "maths/.git/*"
   ```
2. Go to [overleaf.com](https://overleaf.com) → **Create a new project → Upload Project** → select `maths.zip`.
3. When prompted, set the main document to the `main.tex` inside the subject folder you want to read.
4. Click **Compile** — the PDF appears on the right.

To switch subjects, change the main document via **Menu → Main document** in Overleaf.

## Building Locally (requires LaTeX)

Install MacTeX if not present: `brew install --cask mactex`

To compile a subject to PDF (requires `pdflatex` or `latexmk`):

```bash
# From the subject directory, e.g.:
cd mathematics/mts415-mathematical-modelling
latexmk -pdf main.tex

# Or with pdflatex directly (run twice for TOC/cross-refs):
pdflatex main.tex && pdflatex main.tex
```

To clean build artefacts:

```bash
latexmk -C        # from within the subject directory
```

## Repository Structure

```
shared/
  preamble.tex                  # Shared packages, theorem envs, math macros — included by every subject

mathematics/
  <subject-code>-<name>/
    main.tex                    # Root document: loads preamble, sets metadata, inputs chapters in order
    chapters/
      NN-<topic>.tex            # One chapter per file, numbered for ordering
```

Every `main.tex` includes the shared preamble with `\input{../../shared/preamble}`.

## Adding a New Subject

1. Create `mathematics/<code>-<name>/` with `main.tex` and a `chapters/` subdirectory.
2. In `main.tex`, set `\subjectcode`, `\subjecttitle` (and optionally `\subjectsubtitle`), then `\input` chapters in order.
3. Chapter files start with `\chapter{...}` — no preamble, no `\begin{document}`.

## Adding a Chapter to an Existing Subject

1. Create `chapters/NN-<topic>.tex` starting with `\chapter{...}`.
2. Add `\input{chapters/NN-<topic>}` to `main.tex` in the correct position.

## Shared Preamble Conventions

- **Theorem environments**: `theorem`, `lemma`, `corollary`, `proposition` (numbered by section); `definition`, `example`, `exercise` (share the counter); `remark`, `note`, `solution` (unnumbered).
- **Math macros**: `\R`, `\N`, `\Z`, `\Q`, `\C` for number sets; `\dydx`, `\ddx{}`, `\ddt{}`, `\dndx{}{}` for ordinary derivatives; `\pder{}{}`, `\pdern{}{}{}` for partials; `\abs{}`, `\norm{}` (paired delimiters); `\IF` for integrating factor.
- **Convention**: engineering imaginary unit is `j` (not `i`), matching the existing chapters.

Any macro or environment needed across multiple subjects belongs in `shared/preamble.tex`. Subject-specific macros go at the top of the relevant `main.tex`.
