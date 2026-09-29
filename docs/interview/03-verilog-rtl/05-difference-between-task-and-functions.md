---
tags:
  - Verilog
---

# Difference between Task and functions


Both are ways to encapsulate reusable code inside a module, but they differ in what they can do and how they behave in simulation timing.

| **Aspect**                        | **Function**                                                                                                         | **Task**                                                                                                              |
|-----------------------------------|----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| **Return value**                  | Returns exactly one value (via the function name)                                                                    | Can return zero, one, or multiple values (via output/inout arguments)                                                 |
| **Time-consuming statements**     | Cannot contain \#delay, @(posedge clk), wait, or other timing controls — executes in **zero simulation time**        | Can contain timing controls — can consume simulation time                                                             |
| **Arguments**                     | Only input arguments allowed (no output/inout)                                                                       | Can have input, output, and inout arguments                                                                           |
| **Calling other tasks/functions** | Can call other functions, but **cannot call a task** (since tasks may consume time, and functions must be zero-time) | Can call other tasks and functions freely                                                                             |
| **Usage in expressions**          | Can be used directly inside an expression, e.g. y = my_func(a,b) + 1;                                                | Cannot be used inside an expression — called as a standalone statement                                                |
| **Typical use case**              | Combinational logic helpers: parity calculation, checksum, bit-counting, address decoding                            | Sequential/behavioral code: driving a clock, generating a reset pulse, applying a sequence of stimulus in a testbench |
