---
name: challenge-rate
description: Forces a self-review of draft complexity before presenting work. Use when drafting plans, architecture, code changes, explanations, or workflows where complexity may exceed an acceptable threshold. Rates complexity 1-10 and refactors anything above 5 before showing the user.
---

# Challenge Rate

## Mission

Before showing a draft, rate its complexity from 1 to 10. Anything above 5 is unacceptable. If the draft scores above 5, refactor it immediately before presenting it.

## Complexity Scale

- 1-2: Obvious, tiny, almost no moving parts.
- 3-4: Clear and practical; some details but still easy to execute.
- 5: Maximum acceptable complexity; only keep if each part earns its place.
- 6-7: Too complex; refactor before showing.
- 8-10: Bloated, fragile, or over-engineered; do not present as-is.

## Required Self-Check

Ask:

- Can this be explained in half the words?
- Can one step absorb another step?
- Is this abstraction solving today's problem or a hypothetical future?
- Is any section there only because it feels professional?
- Can the user act without reading the whole thing?
- Are there more options than necessary?
- Is the implementation plan carrying avoidable coordination cost?

## Refactor Rules

If complexity is above 5:

- Delete low-value sections.
- Merge overlapping steps.
- Replace abstractions with direct actions.
- Remove optional nice-to-haves.
- Cut defensive caveats unless they prevent real harm.
- Prefer a smaller first move with a clear upgrade trigger.
- Keep only details needed for execution, correctness, or risk control.

## Output Behavior

Usually do not expose the internal draft. Present the simplified final answer.

When useful, include a short note:

```text
Complexity self-check: 6 -> refactored to 4.
```

If the user explicitly asks for the rating, include:

1. Original complexity score.
2. What made it too complex.
3. What was cut.
4. Final complexity score.

## Tone

Be strict. Do not defend complexity. If the answer is bloated, cut it.
