# GPT Image 2 Prompt Set for the PACT Architecture Figure

## Base generation prompt

```text
Create a publication-ready 16:9 landscape academic architecture diagram on a clean white background, flat vector style, large readable sans-serif labels, no title and no watermark.

Exact left-to-right flow:
"Trusted User Request" and orange "External Email — Untrusted / Injection Carrier" feed "Reader Agent". Reader Agent feeds "Action Agent" with "evidence IDs + provenance". Action Agent proposes "value + role + provenance" to a dashed enclosure titled "Deterministic Enforcement Boundary".

Inside that enclosure, "Capability Manifest", "Role Policy", and "Exact Transform Registry" feed "Capability + PACT Gateway". The gateway visibly checks:
"Capability allow-list"
"Argument role"
"Source authority"
"Exact transform + sink"
Then a diamond asks "All checks pass?"

From the diamond draw exactly:
- green "ALLOW" to "ToolExecutor", then to "MockWorld Tools";
- red "DENY" directly to "Blocked — No tool call — No side effect".
DENY must never touch ToolExecutor. Never draw ToolExecutor to Blocked.

Inside MockWorld Tools show:
"File Vault (read) → Read Exposure"
"Calendar (write) → State Mutation"
"Email Outbox (write) → State Mutation"
Do not connect file reads to state mutation.

Across the bottom, a secondary gray "Append-Only Audit & Decision Log" and "Before / After State" feed "Independent Evaluator".

Colors: trusted blue, untrusted orange, ALLOW green, DENY red, audit gray. Use straight arrows and generous whitespace. Render every quoted label exactly. Do not invent labels, arrows, logos, legends, or decorative objects.
```

## Targeted edit prompts

The selected base image was refined with three narrow edit requests:

1. Replace the sequential audit-log-to-state wiring with two independent evidence inputs to the evaluator and add the compact metric line `exposure • blocked attempt • unauthorized effect • leakage • benign success`.
2. Remove the resulting crossed dashed evidence lines while preserving both solid evidence-to-evaluator arrows.
3. Remove the remaining incorrect dashed arrow from the PACT gateway to `Before / After State`, changing no other element.

The final selected image is `figures/f1_pact_enforcement.png`.
