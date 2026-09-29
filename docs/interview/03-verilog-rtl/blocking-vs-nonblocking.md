---
tags:
  - Verilog
  - Easy
---

# Blocking vs non-blocking assignments

## Short answer

Blocking (`=`) executes in order and updates immediately, so it models combinational logic. Non-blocking (`<=`) samples right-hand sides first and updates at the end of the time step, so it models sequential logic and avoids races between flops.

## Code

=== "Non-blocking (correct shift register)"

    ```verilog title="shift_nb.v" linenums="1"
    always @(posedge clk) begin
      q1 <= d;   // RHS sampled at the clock edge
      q2 <= q1;  // sees the OLD q1
      q3 <= q2;  // sees the OLD q2
    end
    ```

=== "Blocking (common mistake)"

    ```verilog title="shift_b.v" linenums="1"
    always @(posedge clk) begin
      q1 = d;
      q2 = q1;   // sees the NEW q1
      q3 = q2;   // collapses to a single flop
    end
    ```

## Explanation

With blocking assignments each line sees the value just written, so `d` reaches `q3` in one clock and synthesis produces one flop. With non-blocking assignments all right-hand sides are sampled before any update, giving three flops in a chain.

!!! warning "Common trap"
    Do not mix blocking and non-blocking assignments to the same variable in one always block.

!!! tip "Rule to remember"
    Sequential `always @(posedge clk)` uses `<=`. Combinational `always @(*)` uses `=`.

??? question "Likely follow-up: what is a race condition here?"
    If flops in different blocks use `=`, the simulator may evaluate them in either order, so results can differ between tools.
