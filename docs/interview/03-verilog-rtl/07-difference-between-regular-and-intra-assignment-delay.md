---
tags:
  - Verilog
---

# Difference between regular and intra assignment delay


**So regular delay is effectively wait-then-evaluate, while intra-assignment delay is evaluate-then-wait**

The difference is when the RHS is evaluated. In a regular assignment delay like \#5 q = d, the process waits for 5 time units and then evaluates d and assigns it to q. In an intra-assignment delay like q = \#5 d, the RHS is evaluated immediately and its value is saved, then the assignment to q occurs after 5 time units.."

## Follow-up: What happens if d changes during the delay?

For an intra-assignment delay, the change doesn't affect the pending assignment because the RHS value was already evaluated when the statement executed. For a regular assignment delay, the RHS is evaluated only after the delay, so the new value of d at that time is used

In a continuous assignment with delay, every change in the RHS causes a new output update to be scheduled after the specified delay; the RHS isn't simply evaluated after waiting for the delay.
