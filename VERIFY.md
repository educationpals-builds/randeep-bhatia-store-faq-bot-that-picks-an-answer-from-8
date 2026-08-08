# Verify: Store FAQ bot that picks an answer from the help center

## What this check confirms

A stranger can run their own FAQ bot specimen through `/play` and the tool will:

1. Surface the deciding-check finding (the pattern that no part of the system owns)
2. Demand a numeric measurement for that finding

---

## Stranger verification steps

### 1. Open `/play` with your own FAQ bot specimen

Paste a description of your failing FAQ bot setup:
- What the bot is supposed to do
- Who gets hurt when it fails
- Three real messages where it fails

### 2. Confirm the tool walks all five checks

The tool should ask about each check and propose findings with measurements. For the builder's specimen (Store FAQ bot that picks an answer from the help center), the deciding check was **unowned** — no part of the system currently treats refund/return/cancel words as a priority signal.

### 3. Verify the tool demands a numeric measurement

For the deciding check, the tool must ask for a specific number that would confirm the finding. Example from the builder's audit:

> Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.

The tool should not accept vague statements like "keep an eye on it" — it must surface a number, a danger line, and a watcher.

### 4. Confirm the output includes

- A scored audit with all five checks rated
- A severity story grounded in a real failing input
- A call (ship / ship-with-conditions / hold) with an owner on any condition
- A tripwire with a number, a danger line, and who watches it

---

## Builder's specimen as reference

**Specimen:** Store FAQ bot that picks an answer from the help center

**Standard:** The answer matches the shopper's real ask — not a nearby FAQ about the same product

**Deciding check:** unowned (rated 4 — the worst score)

**Call:** Hold. No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.

**Tripwire:** Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.

---

## Pass criteria

A stranger's run passes verification when:

- [ ] The tool identifies which check is the decider for their specimen
- [ ] The finding names a measurement (not a category)
- [ ] The call has an owner if conditions are attached
- [ ] The tripwire has a number, a danger line, and a watcher
