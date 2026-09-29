---
tags:
  - Digital-Electronics
---

# What is the difference between a flip-flop and a latch?


**The main difference between a latch and a flip-flop is how they are triggered.**

A **latch is level-sensitive**, whereas a **flip-flop is edge-triggered**.

For example, in a positive-level D latch, when the enable signal is HIGH, the latch is transparent, meaning the output can follow the input. When the enable goes LOW, it holds the last value.

In contrast, a positive-edge-triggered D flip-flop samples the input only at the rising edge of the clock and holds that value until the next active edge.

## Follow-up: Why are flip-flops generally preferred over latches in synchronous RTL design?

The main reason is timing predictability.
