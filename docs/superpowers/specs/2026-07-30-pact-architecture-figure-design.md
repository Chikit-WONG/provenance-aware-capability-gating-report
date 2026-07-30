# PACT Architecture Figure Design

## Goal

Replace the current architecture raster with a readable 16:9 academic diagram whose arrows and labels match the implemented PACT enforcement semantics, while retaining the previous LaTeX prose and figure block as commented history.

## Chosen approach

Generate a new, non-destructive sibling image with the built-in GPT Image 2 workflow. The old `figures/f1.png` remains unchanged. The new image is stored as `figures/f1_pact_enforcement.png` and becomes the active figure in `main_ChiKitWong.tex`.

## Required data flow

1. A trusted user request and an untrusted email source enter the Reader/Action pipeline.
2. The Reader passes event-linked evidence and provenance parents to the Action Agent.
3. The Action Agent proposes structured tool arguments carrying a value, argument role, and provenance.
4. The deterministic gateway checks both the capability manifest and PACT policy before execution.
5. PACT checks argument role, source authority, exact registered transformations, and sensitivity/sink constraints.
6. `ALLOW` reaches the Tool Executor and then MockWorld tools.
7. `DENY` goes directly to a blocked-and-audited outcome with no tool call and no side effect. There must be no arrow from the Tool Executor to the blocked outcome.
8. The audit/evaluation path distinguishes read exposure from state mutation and uses event logs plus before/after state.

## Visual constraints

- White background, landscape 16:9 composition, vector-like academic style.
- Large sans-serif labels that remain readable at `0.95\textwidth` in a two-column paper.
- Blue for trusted/neutral flow, orange for untrusted data, green for `ALLOW`, and red for `DENY`.
- A dashed box is labeled `Deterministic Enforcement Boundary`, not `Trusted Computing Base`.
- No watermark, decorative clip art, invented components, crossed arrows, or dense prose.
- All in-image labels must be rendered verbatim.

## LaTeX integration

Prefix every line of the existing explanatory paragraph and `figure*` block with `%`. Add the revised paragraph and replacement `figure*` immediately below it. Reuse `\label{fig:architecture}` only in the active block and update the caption to state that PACT runs before `ToolExecutor` and that denied calls produce neither a tool event nor a side effect.

## Validation

- Inspect the generated image for label spelling and arrow direction.
- Compile with TinyTeX using `pdflatex`, `bibtex`, `pdflatex`, `pdflatex`.
- Confirm the PDF exists, cross-references resolve, and the report remains within the accepted nine-page maximum.
- Run `git diff --check` and inspect the final staged scope before commit and push.
