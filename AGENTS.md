# AGENTS.md

## Project overview

Notes and problem sets following Fredric Schuller's "Geometric Anatomy of Theoretical Physics"
lecture series. Reference PDF: `Lectures_on_Geometric_Anatomy_of_Theoretical_Physics.pdf`.

## Structure

- `lec{NN}-{topic}/notes.md` — lecture notes
- `lec{NN}-{topic}/problems.md` — problem statements (NO solutions)
- Lectures 01–04 are review material (concise, reference-style)
- Lecture 05 onward: detailed notes as the user progresses

## Conventions

- Notes should mirror the PDF structure (definitions, theorems, examples)
- Problems are statement-only — no solutions, no hints
- Use LaTeX-style math notation (compatible with markdown renderers)
- Keep review notes dense; keep new notes thorough
- When generating new lecture content, extract relevant text from the PDF using pymupdf (`import fitz`)

## PDF extraction

The course PDF is at the repo root. To extract a chapter:
```python
import fitz
doc = fitz.open("Lectures_on_Geometric_Anatomy_of_Theoretical_Physics.pdf")
# Chapter N: use page ranges from the TOC
# Chapters are 1-indexed, pages are 0-indexed in fitz
```

## Tools available

- pymupdf (fitz) is installed for PDF text extraction
- Python 3 at /opt/homebrew/bin/python3
