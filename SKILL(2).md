---
name: challenge-all
description: >-
  Runs all seven personal challenge skills in one pass: challenge-question,
  challenge-unknown, challenge-disagree, challenge-edge-case, challenge-scale,
  challenge-execute, and challenge-rate. Use when the user says challenge-all,
  run all challenges, full challenge review, stress-test my plan, or wants every
  challenge lens applied at once to a decision, architecture, plan, or code change.
---

# Challenge All

## Mission

Apply every personal challenge skill to the user's topic in one structured review. Do not skip lenses. Do not merge them into vague general advice. Each lens keeps its own section and output contract.

## When To Use

- User says `challenge-all`, `run all challenges`, or `full challenge review`
- User wants adversarial + scale + edge-case + execution critique together
- User proposes architecture, plan, product direction, or implementation and wants maximum pressure-testing

## Prerequisite: Load Child Skills

Before analyzing, read all seven skill files:

| Order | Skill | Path |
| ----- | ----- | ---- |
| 1 | challenge-question | `~/.cursor/skills/challenge-question/SKILL.md` |
| 2 | challenge-unknown | `~/.cursor/skills/challenge-unknown/SKILL.md` |
| 3 | challenge-disagree | `~/.cursor/skills/challenge-disagree/SKILL.md` |
| 4 | challenge-edge-case | `~/.cursor/skills/challenge-edge-case/SKILL.md` |
| 5 | challenge-scale | `~/.cursor/skills/challenge-scale/SKILL.md` |
| 6 | challenge-execute | `~/.cursor/skills/challenge-execute/SKILL.md` |
| 7 | challenge-rate | `~/.cursor/skills/challenge-rate/SKILL.md` |

If a path fails, note which skill was unavailable and continue with the rest.

## Execution Order

Run in this sequence. Later lenses may reference earlier findings; do not repeat the same point verbatim across sections.

1. **challenge-question** — Premise and assumptions first.
2. **challenge-unknown** — Advanced concepts that reframe the problem.
3. **challenge-disagree** — Strongest opposing position.
4. **challenge-edge-case** — Hidden assumptions, black swans, paper vs production.
5. **challenge-scale** — 100x data, 50k concurrent users, deadlocks, memory, races.
6. **challenge-execute** — Option A vs B, 80/20, cut 50% of steps.
7. **challenge-rate** — Self-rate final synthesis complexity; refactor if above 5 before presenting.

## Input Scope

Apply to whatever the user gave:

- Decision or architecture choice
- Implementation plan or PR-level change
- Business logic, API, or data model
- Draft answer the agent was about to give (challenge-rate still applies)

If scope is unclear, state the assumed scope in one line, then proceed.

## Required Output

Use one combined report with these top-level sections:

```markdown
# Challenge-All Review

## Scope
[One sentence: what is being challenged]

## 1. Question (challenge-question)
[Follow that skill's output format]

## 2. Unknown Concepts (challenge-unknown)
[Follow that skill's output format]

## 3. Disagree (challenge-disagree)
[Follow that skill's output format]

## 4. Edge Cases (challenge-edge-case)
[Follow that skill's output format]

## 5. Scale (challenge-scale)
[Follow that skill's output format]

## 6. Execute (challenge-execute)
[Follow that skill's output format]

## 7. Complexity Check (challenge-rate)
[Final score 1-10; if refactored synthesis, note before/after]

## Cross-Cut Summary
| Lens | Top risk or insight |
| ---- | ------------------- |
| Question | ... |
| Unknown | ... |
| Disagree | ... |
| Edge case | ... |
| Scale | ... |
| Execute | ... |
| Rate | ... |

## Recommended Next Move
[One concrete action: ship / ship with guardrails / do not ship / run experiment X]
```

## Rules

- Follow each child skill's tone and minimum content (e.g. ≥3 hidden assumptions for edge-case).
- Cite code, files, tables, or endpoints when the topic is implementation-specific.
- Do not soften conclusions to sound balanced; these skills are adversarial by design.
- If lenses conflict, say so explicitly in **Cross-Cut Summary** and **Recommended Next Move**.
- Keep the full report actionable; cut filler before presenting (challenge-rate applies to the whole report).

## Short Mode

If the user asks for a short challenge-all:

- Run all seven lenses internally.
- Output only **Cross-Cut Summary** + **Recommended Next Move** + **Complexity Check** (one line).

## Example Trigger

User: `challenge-all: I will store Twilio recordings only on Wasabi and skip DB until later.`

Agent: Load seven skills → run sequence → deliver combined report per format above.
