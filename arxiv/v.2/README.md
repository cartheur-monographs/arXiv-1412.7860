# arXiv v.2 Submission Bundle

This directory contains the `v.2` arXiv submission materials for the
`arXiv-1412.7860` paper.

Working title:

- `A Self-Organizing Geometric Algorithm for Autonomous Data Partitioning`

## Primary files

- `main.tex`: LaTeX source for the paper
- `main.pdf`: locally compiled reference PDF
- `figures/`: extracted figure assets used by the manuscript

## Local build

```bash
cd arxiv/v.2
pdflatex -interaction=nonstopmode -halt-on-error main.tex
pdflatex -interaction=nonstopmode -halt-on-error main.tex
```

## Submission package

For arXiv submission, upload source rather than PDF-only.

Current source bundle:

- `main.tex`
- `figures/fig1.png`
- `figures/fig2.png`
- `figures/fig3.png`
- `figures/fig4.png`

The local `main.pdf` should be treated as a comparison artifact, not the
upload format.

## Notes

- This bundle mirrors the repository structure used in the `symbolic-logic`
  publication so front matter, layout, and packaging stay consistent across
  monographs.
- This bundle is the second arXiv-ready revision prepared in this repository.
- The figure assets in `figures/` were extracted from the original 2014 PDF
  source preserved in the repo root.
