# Engineering Maths Notes

LaTeX notes for engineering mathematics subjects.

## Subjects

| Code | Title |
|------|-------|
| IPE 401 | Mathematical Methods in Production Engineering |
| MTS 415 | Mathematical Modelling |

## How to Read the Notes

### Option 1 — Overleaf (recommended, no install)

1. Download this repo as a ZIP: **Code → Download ZIP** on this page
2. Go to [overleaf.com](https://overleaf.com) → **New Project → Upload Project** → upload the ZIP
3. In Overleaf, go to **Menu → Main document** and select the `main.tex` of the subject you want
4. Click **Compile** — the PDF appears on the right

To switch subjects, repeat step 3 with a different `main.tex`.

### Option 2 — Compile locally

Requires MacTeX (`brew install --cask mactex`).

```bash
cd mathematics/mts415-mathematical-modelling
pdflatex main.tex && pdflatex main.tex
open main.pdf
```
