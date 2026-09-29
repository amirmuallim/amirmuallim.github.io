---
tags:
  - Digital-Electronics
---

# What is overflow? Under what conditions will it occur?


Overflow occurs when the mathematically correct result cannot be represented using the available number of bits.

For unsigned addition, overflow occurs when there is a carry out of the MSB. For signed 2's-complement addition, overflow occurs when two numbers having the same sign produce a result with the opposite sign. So positive plus positive producing negative, or negative plus negative producing positive indicates overflow. Hardware can detect signed overflow using XOR of the carry into and carry out of the MSB

For signed 2s complement addition

$$\boxed{Overflow = C_{in\text{~}to\text{~}MSB}\oplus_{}^{}C_{out\text{~}from\text{~}MSB}}$$

## Follow-up: Can carry-out and overflow be different

Yes. Carry-out and signed overflow are different. For example, −4 + −2 gives 1010, which is −6, with a carry-out of 1 but no signed overflow. Conversely, +5 + +6 gives 1011, which is −5, with no carry-out but signed overflow
