---
tags:
  - Digital-Electronics
---

# What is Metastability in digital circuits? Why does it occur, and how does a 2-flip-flop synchronizer mitigate it?


**Metastability is a condition where a flip-flop temporarily fails to resolve to a valid logic 0 or 1.**

It usually occurs when the input of a flip-flop changes too close to its active clock edge and violates the flip-flop's **setup or hold time**

A **2-Flip-Flop Synchronizer** mitigates this by passing the signal through two cascaded flip-flops clocked by the destination clock domain. The first flop absorbs the asynchronous transition and may enter metastability. However, giving it a full clock cycle allows the metastable state to settle to a stable 0 or 1 before the second flop captures it.

While it does not eliminate metastability 100%, it dramatically increases the Mean Time Between Failures (MTBF) to decades or centuries
