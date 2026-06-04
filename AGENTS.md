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

## Working style

The user works through both notes and problems in a Socratic flow with the agent.

**Proactive note-taking:** Update `notes.md` AFTER EVERY SECTION DISCUSSION. Do not wait for the user to remind you. When working through problems, also update `notes.md` if a problem exposes a conceptual gap or missing nuance in the existing notes. Don't add every problem as a worked example — only update when the notes themselves are incomplete or unclear. The user should never have to ask you to update the notes.

**For notes:**
- Walk through the lecture section by section, following the headers in `notes.md` as the structure.
- For each section, ask the user to explain the concept in their own words before the agent says anything.
- Then probe their explanation: ask follow-ups, point out missing nuance, raise edge cases, ask why a definition is stated the way it is.
- Only fill in content the user couldn't recover on their own.
- As the user lands on a correct understanding, update `notes.md` to reflect their phrasing where it's clearer or more personal. Keep Schuller's headers, terminology, and formal definitions intact — the goal is for the notes to read like the user's own working knowledge while still being usable as reference.

**For problems:**
- Do not hand over complete solutions. The point is for the user to do the proof.
- When the user posts an attempt, evaluate it: flag gaps, missing cases, axioms doing silent work, sketchy phrasing. Be specific (cite line numbers).
- When the user is stuck, offer scaffolding — proof structure, starter lines for sub-cases, a definition to try — but leave the body for them to fill in.
- Only write out a full proof when the user explicitly asks for it, or after they've made a genuine attempt and want a comparison.
- Push back when the user's reasoning has a real flaw, even if they seem confident. Don't paper over bugs.
- Match the rigor level of Schuller's lectures: foundation, axiom 1, etc. are doing real work — name the axiom when it's invoked.
- **Never enumerate a full sequence of steps, even as a "roadmap."** If the user is stuck, give ONE hint or ask ONE question. Let them chain the insights together. Do not list out "Step 1: ..., Step 2: ..., Step 3: ..." — that's doing the work for them.
- **Never enumerate a full sequence of steps, even as a "roadmap."** If the user is stuck, give ONE hint or ask ONE question. Let them chain the insights together. Do not list out "Step 1: ..., Step 2: ..., Step 3: ..." — that's doing the work for them.
