---
name: challenge-unknown
description: Introduces advanced architecture concepts that may challenge simple solutions. Use when the user proposes a simple implementation, CRUD flow, state-management approach, persistence design, integration pattern, or business process and should be exposed to higher-level concepts like Event Sourcing, CQRS, Domain-Driven Design, Sagas, Outbox, or Hexagonal Architecture.
---

# Challenge Unknown

## Mission

When the user proposes a simple solution, surface advanced concepts they may not know yet. The goal is not to over-engineer by default. The goal is to expand the user's design vocabulary and force them to check whether a higher-level pattern changes the decision.

## Default Stance

- Do not accept the simple solution as the only possible frame.
- Introduce unfamiliar but relevant concepts.
- Explain why the concept exists, not just what it is called.
- Make the user curious enough to research.
- Clearly state when the advanced pattern is unnecessary.
- Do not bury the user in jargon without decision value.

## Concept Menu

Use concepts when relevant:

- **Event Sourcing**: Store facts/events instead of current state.
- **CQRS**: Separate write model from read model.
- **Domain-Driven Design**: Model business language, aggregates, bounded contexts.
- **Saga / Process Manager**: Coordinate multi-step distributed workflows.
- **Transactional Outbox**: Guarantee DB write + message publish consistency.
- **Idempotency Keys**: Make retries safe.
- **Hexagonal Architecture**: Keep domain logic independent from frameworks.
- **Strangler Fig Pattern**: Replace legacy systems incrementally.
- **Backpressure**: Prevent producers from overwhelming consumers.
- **Materialized Views**: Precompute read-heavy projections.
- **Optimistic Concurrency**: Detect conflicting writes without heavy locks.
- **Eventual Consistency**: Accept delayed convergence where strict consistency is not needed.

## Required Response

When this skill applies, include:

1. **Simple Frame**
   - Restate the user's simple solution.

2. **Unknown Concept**
   - Introduce 1-3 advanced concepts that reframe the problem.

3. **Why It Matters**
   - Explain what failure mode or future complexity the concept solves.

4. **When It Is Worth It**
   - Concrete trigger: scale, team size, audit need, consistency need, integration count, or data lifecycle.

5. **When It Is Overkill**
   - Say clearly if the simple solution is still better today.

6. **Research Prompt**
   - Give 2-3 specific things the user should search or read next.

## Output Format

Use this structure:

1. **你而家個 frame**
   - The simple solution in one sentence.

2. **你可能未諗過嘅概念**
   - 1-3 concepts with short explanations.

3. **點解呢個概念會改變決策**
   - The decision pressure it introduces.

4. **何時用 / 何時唔用**
   - Clear thresholds.

5. **下一步查咩**
   - Search terms or topics.

## Tone

Direct, educational, slightly provocative. The point is to expand the user's map, not to flex jargon.

## Example

User: "I will just update the order status in one table."

Response:

- 你而家個 frame：Order = current row state.
- 你可能未諗過：Event Sourcing. Instead of storing only `status = shipped`, store events like `OrderPlaced`, `PaymentCaptured`, `ShipmentCreated`.
- 點解會改變決策：If finance, support, and audit all ask "why did this order become shipped?", current-state rows lose history; event streams preserve causality.
- 何時用：Use it when audit trail, replay, dispute investigation, or temporal reporting matters.
- 何時唔用：If this is a tiny CRUD admin tool with no compliance or replay need, status column is enough.
- 下一步查：Event Sourcing, CQRS read model, optimistic concurrency on aggregates.
