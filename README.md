# Store FAQ bot that picks an answer from the help center

**Specimen:** Store FAQ bot that picks an answer from the help center

**Situation:** Shoppers ask about refunds, but the FAQ bot answers with shipping times because it latched onto the product name. Fix that before the busy sale week.

---

## Verdict

**Hold.** No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.

---

## Tripwire

Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.

---

## The problem

Shoppers get the wrong policy and leave the cart.

The standard for "fixed":  
The answer matches the shopper's real ask — not a nearby FAQ about the same product.

---

## One-paste rebuild block

Copy this into your audit tracker or sprint planning:

```
SPECIMEN: Store FAQ bot that picks an answer from the help center
STAKES: Shoppers get the wrong policy and leave the cart
STANDARD: The answer matches the shopper's real ask — not a nearby FAQ about the same product

FAILING INPUTS (from Store help-desk chat logs):
- how long do i have to return the Nova Buds after they ship
- Nova Buds delivery says Friday — can i still cancel
- refund for wrong size on the Trail Jacket, not a shipping question

DECIDING CHECK: unowned (score 4/5 — worst)
CALL: Hold — engineering lead adds dedicated refund/return/cancel check before Black Friday
TRIPWIRE: >10 refund-misroutes/day during sale week → CX manager escalates to engineering
```

---

## Full audit

See [charter.md](charter.md) for the complete five-check audit with all ratings, the severity story, and the detailed call.

## Method

See [METHOD.md](METHOD.md) for the five checks used in this audit.

## Verification

See [VERIFY.md](VERIFY.md) to run a stranger's FAQ bot specimen through the same audit discipline.

<!-- educationpals-build-verified -->
