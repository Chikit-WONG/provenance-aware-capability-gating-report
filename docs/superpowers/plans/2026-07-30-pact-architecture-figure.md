# PACT Architecture Figure Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Generate and integrate a semantically correct PACT architecture figure while retaining the previous LaTeX version as comments.

**Architecture:** GPT Image 2 produces a new 16:9 raster from the frozen design. The report activates the new sibling asset and revised prose, while LaTeX `%` line comments preserve the former paragraph and figure block verbatim.

**Tech Stack:** GPT Image 2 built-in image generation, PNG, LaTeX, TinyTeX, Git.

## Global Constraints

- Do not overwrite or delete `figures/f1.png`.
- `DENY` must branch before the Tool Executor and produce no tool call or side effect.
- PACT must visibly check argument role, source authority, exact registered transformations, and sensitivity/sink constraints.
- Old LaTeX prose, include command, and caption must remain inside an inactive comment block.
- Use TinyTeX from `/hpc2hdd/home/ckwong627/.TinyTeX/bin/x86_64-linux`.

---

### Task 1: Generate and validate the replacement asset

**Files:**
- Create: `figures/f1_pact_enforcement.png`
- Preserve: `figures/f1.png`

**Interfaces:**
- Consumes: the frozen flow and visual constraints in `docs/superpowers/specs/2026-07-30-pact-architecture-figure-design.md`.
- Produces: a 16:9 PNG suitable for `\includegraphics[width=0.95\textwidth]`.

- [ ] **Step 1: Generate the image with GPT Image 2**

Use a structured `infographic-diagram` prompt that states every required label, arrow, color, and prohibited connection.

- [ ] **Step 2: Save the selected output non-destructively**

Copy the selected built-in output to `figures/f1_pact_enforcement.png`; leave `figures/f1.png` unchanged.

- [ ] **Step 3: Validate visual semantics**

Inspect the final image and confirm that `ALLOW` reaches the Tool Executor, `DENY` bypasses it, the PACT box contains all four checks, and all labels are legible and correctly spelled.

### Task 2: Integrate the active LaTeX figure

**Files:**
- Modify: `main_ChiKitWong.tex:157`

**Interfaces:**
- Consumes: `figures/f1_pact_enforcement.png` from Task 1.
- Produces: one inactive historical figure block and one active `fig:architecture` block.

- [ ] **Step 1: Preserve the previous version**

Prefix every line of the old explanatory paragraph and old `figure*` block with `%` without changing their contents.

- [ ] **Step 2: Add the revised explanation**

Describe event-linked provenance, structured `(value, role, provenance)` proposals, pre-execution PACT checks, and evaluator evidence without claiming transcript-keyword detection.

- [ ] **Step 3: Add the new figure and caption**

Reference `figures/f1_pact_enforcement.png`, reuse `fig:architecture` in the active block, and state in the caption that denied calls produce no tool event or side effect.

### Task 3: Verify and publish

**Files:**
- Verify: `main_ChiKitWong.tex`
- Verify: generated `main_ChiKitWong.pdf`

**Interfaces:**
- Consumes: the integrated LaTeX source and PNG.
- Produces: a compiling report commit on `main` pushed to `origin/main`.

- [ ] **Step 1: Compile the report**

Run the TinyTeX sequence `pdflatex`, `bibtex`, `pdflatex`, `pdflatex` on `main_ChiKitWong.tex` and retain the valid PDF even if only a final rerun warning is reported.

- [ ] **Step 2: Check layout and references**

Confirm the PDF page count is at most nine, the architecture figure is present, and the log has no undefined references or missing-file errors.

- [ ] **Step 3: Check the diff**

Run `git diff --check`, inspect `git status --short`, and ensure no unrelated generated files are staged.

- [ ] **Step 4: Commit and push**

Stage only the new image, LaTeX edit, design, plan, and intended compiled PDF if it is tracked; commit with a focused message and push `main` to `origin/main`.
