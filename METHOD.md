# The Five Checks: PRISM

When a store FAQ bot picks answers from the help center, it can fail in predictable ways. This method walks five checks to find where the routing breaks down.

---

## P — Partition the Space

Does the system divide the question space into distinct, non-overlapping categories?

A FAQ bot that treats "refund" and "shipping" as separate partitions can route correctly. One that lumps them together because they share a product name (like "Nova Buds") will confuse the two.

**What to measure:** Count how many category boundaries exist, and whether a question can fall into more than one.

---

## R — Run in Parallel

Does the system evaluate multiple possible answers simultaneously, or does it commit too early?

When a shopper asks about returning the Nova Buds, the bot should consider refund policies, shipping policies, and product specs in parallel — then pick the best match. If it locks onto "Nova Buds = shipping FAQ" before considering "return," it fails this check.

**What to measure:** How many candidate answers does the system score before committing?

---

## I — Individuate the Pattern

Does the system recognize that different question types require different handling, even when they mention the same product?

"Nova Buds delivery says Friday — can I still cancel" is a cancellation question, not a delivery question. The bot must individuate the cancel pattern from the delivery pattern, even though both mention delivery timing.

**What to measure:** Given two questions about the same product with different intents, does the system route them differently?

---

## S — Stitch the Spectra

Does the system combine signals from multiple dimensions (product, intent, urgency) into a coherent routing decision?

A question like "refund for wrong size on the Trail Jacket, not a shipping question" contains explicit intent ("refund," "not a shipping question") plus product ("Trail Jacket") plus context ("wrong size"). The bot must stitch these signals together, not just match on product name.

**What to measure:** How many distinct signal types does the system weigh before routing?

---

## M — Map What Each Head Sees

Does the system make visible which signals drove the routing decision?

When the bot answers a refund question with shipping times, you need to see why. Did it weight "Nova Buds" higher than "return"? Did it ignore "cancel" entirely? Mapping what each component saw reveals the failure point.

**What to measure:** Can you trace the routing decision back to specific input tokens and their weights?

---

## The Anti-Pattern: Collapse to Monochrome

When a system treats all questions about a product as the same question, it collapses the spectrum of intents into a single color. The shopper asks about refunds; the bot sees "Nova Buds" and returns shipping times.

This is the collapse-to-monochrome failure: the system had multiple signals (product name, intent words, explicit negations) but flattened them into one dimension.

The five checks above detect where this collapse happens and what measurement would confirm the fix.
