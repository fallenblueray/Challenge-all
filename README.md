# Challenge All Skills

A portable collection of eight adversarial-review skills: one orchestrator and seven standalone lenses.

## Skills

- `challenge-all` — runs every lens in sequence.
- `challenge-question` — challenges premises and assumptions.
- `challenge-unknown` — introduces concepts that may reframe the decision.
- `challenge-disagree` — argues the strongest opposing position.
- `challenge-edge-case` — hunts hidden assumptions and production failures.
- `challenge-scale` — stress-tests 100x data and 50,000 concurrent users.
- `challenge-execute` — compares conventional, counter-intuitive, and 80/20 execution paths.
- `challenge-rate` — rates and reduces unnecessary complexity.

Each installable skill lives at `skills/<skill-name>/SKILL.md`. Install all eight as sibling directories so `challenge-all` can load the seven child skills through relative paths.

## Codex installation

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo fallenblueray/Challenge-all- \
  --path \
    skills/challenge-all \
    skills/challenge-question \
    skills/challenge-unknown \
    skills/challenge-disagree \
    skills/challenge-edge-case \
    skills/challenge-scale \
    skills/challenge-execute \
    skills/challenge-rate
```

Restart the agent session after installation so the skills are rediscovered.
