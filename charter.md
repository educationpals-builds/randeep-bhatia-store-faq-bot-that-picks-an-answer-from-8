# Store FAQ bot that picks an answer from the help center

## Audit Charter

**Specimen under review:** Store FAQ bot that picks an answer from the help center

**What goes wrong if this never gets fixed:** Shoppers get the wrong policy and leave the cart

---

## Standard

The answer matches the shopper's real ask — not a nearby FAQ about the same product

---

## Real inputs

**What the real inputs look like:** Short mobile questions with product names in the middle

**Source:** Store help-desk chat logs

### Pasted specimen sentences

```
how long do i have to return the Nova Buds after they ship
Nova Buds delivery says Friday — can i still cancel
refund for wrong size on the Trail Jacket, not a shipping question
```

---

## Five-check findings

| Check | Rating | Notes |
|-------|--------|-------|
| Unowned | 4 | Highest severity — no part of the system treats refund/return/cancel words as a priority signal |
| Copies | 2 | Some duplication in how product names get matched |
| Room | 1 | Low concern |
| Stitch | 2 | Moderate issue with how signals combine |
| Ablation | 1 | Low concern |

---

## Deciding check

**Top crack:** unowned

The "unowned" check is the decider. The bot has no dedicated logic to recognize refund, return, or cancel intent — so when a shopper mentions a product name alongside a refund question, the bot latches onto the product name and returns shipping content instead.

---

## Severity story

When a shopper types "refund for wrong size on the Trail Jacket, not a shipping question," the bot sees "Trail Jacket" and pulls up shipping FAQs for that product. The shopper explicitly said "not a shipping question" — but no part of the system currently treats refund/return/cancel words as a priority signal. The CX team then handles an escalation that the bot should have resolved, and the shopper may abandon the cart entirely.

---

## Call

**Verdict:** Hold

Hold. No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.

---

## Tripwire

Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.

| Metric | Danger line | Watcher |
|--------|-------------|---------|
| Tickets with refund/return/cancel word answered with shipping content | 10 per day during sale week | CX manager |

---

## Reopen conditions

1. Engineering lead adds a dedicated check that prioritizes refund/return/cancel words over product-name matching
2. All three specimen sentences route correctly with refund words present
3. Retest before Black Friday launch
