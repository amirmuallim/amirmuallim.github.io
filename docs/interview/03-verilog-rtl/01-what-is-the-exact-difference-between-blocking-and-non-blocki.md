---
tags:
  - Verilog
---

# What is the exact difference between blocking (=) and non-blocking (<=) assignments in Verilog? What happens if you mix them inside a sequential always block?


**Blocking assignments (=)**: executes immediately and sequentially, in program order, blocking the next statement from executing until this one completes. Used correctly in **combinational logic**

**Non-blocking assignments (\<=)** evaluate the right-hand side (RHS) in the Active Region, but update the left-hand side (LHS) later in the Non-Blocking Assignment (NBA) region.

If you mix them in a sequential always @(posedge clk) block, you introduce **race conditions** and **simulation-synthesis mismatches**.

## Follow-up: How does the Verilog Event Queue schedule a non-blocking assignment (<=) during simulation?

When a posedge clk triggers, the simulator enters the **Active Event Region**. It evaluates the RHS expressions of all non-blocking statements using current values and queues the updates. Once all active events finish executing, the simulator moves to the **NBA Event Region** and applies the updated values to the LHS variables simultaneously.
