# Store FAQ Bot That Picks an Answer from the Help Center — Conversational Auditor

## What this auditor does

A stranger describes their own FAQ bot that routes shopper questions to help-center answers. They paste a few real failing inputs. This auditor walks five checks conversationally, proposes findings with the measurement that would confirm each, and returns a scored audit with a severity story, a ship/hold call, and a tripwire.

---

## The problem this auditor targets

Shoppers ask about refunds, but the FAQ bot answers with shipping times because it latched onto the product name. Fix that before the busy sale week.

**Stakes:** Shoppers get the wrong policy and leave the cart

**Pass standard:** The answer matches the shopper's real ask — not a nearby FAQ about the same product

**Real input shape:** Short mobile questions with product names in the middle

---

## The five checks

| Check | What it tests | Measurement |
|-------|---------------|-------------|
| **Unowned** | Does any part of the system own the distinction between refund/return/cancel intent vs. shipping intent? | Count of refund-word queries that route to shipping answers |
| **Copies** | Are there duplicate or near-duplicate FAQ entries that compete for the same query? | Number of FAQ entries that could plausibly match a single query |
| **Room** | Does the routing logic have enough signal to distinguish intent when product names appear? | Accuracy on held-out queries containing product names |
| **Stitch** | Do the components (intent detection, FAQ retrieval, answer selection) hand off cleanly? | Count of queries where intent was correct but final answer was wrong |
| **Ablation** | If you remove one component, does the system degrade predictably? | Performance delta when disabling each routing stage |

---

## Worked example: the builder's own audit

### Specimen

Store FAQ bot that picks an answer from the help center

### Failing inputs (from store help-desk chat logs)

```
how long do i have to return the Nova Buds after they ship
Nova Buds delivery says Friday — can i still cancel
refund for wrong size on the Trail Jacket, not a shipping question
```

### Ratings

| Check | Score (1–5) |
|-------|-------------|
| Unowned | 4 |
| Copies | 2 |
| Room | 1 |
| Stitch | 2 |
| Ablation | 1 |

### Top crack

**Unowned** — No part of the system currently treats refund/return/cancel words as a priority signal.

### Ship call

Hold. No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.

### Tripwire

Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.

---

## How a stranger uses this auditor

1. **Describe your FAQ bot** — What it routes, who it serves, what goes wrong when it fails.
2. **Paste 3+ real failing inputs** — Actual shopper questions where the bot gave the wrong answer.
3. **State your pass standard** — How will you know it's fixed?

The auditor will:

- Walk each of the five checks against your specimen
- Propose a finding for each check with the measurement that would confirm it
- Rate each check 1–5
- Identify the top crack (the check that decides)
- Return a ship/hold call with an owner on any condition
- Set a tripwire: a number, a danger line, and who watches it

---

## Acceptance criteria

- Auditor walks all five checks for a stranger's FAQ bot routing failures
- Every finding names the measurement that would confirm it
- Each result includes a call with an owner on any condition
- Each result includes an alarm with a number, a danger line, and a watcher
- The builder's own audit (Store FAQ bot, Nova Buds/Trail Jacket examples, Hold call, 10/day tripwire) is visible as the worked example
