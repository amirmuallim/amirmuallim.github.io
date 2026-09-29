---
tags:
  - Verilog
---

# Explain how multipliers and dividers are synthesized from rtl to hardware


"When we write multiplication or division operators in RTL, synthesis recognizes them as arithmetic operations and infers appropriate hardware. For multiplication, the basic implementation involves generating partial products and adding them, and the synthesis tool can optimize this using structures such as carry-save or Wallace/Dadda trees, or map the operation to a dedicated multiplier resource on an FPGA.

Division is generally more complex. Hardware can use algorithms such as restoring or non-restoring division, involving comparison, subtraction and shifting. It can be implemented as combinational logic or as an iterative multi-cycle datapath that reuses hardware, giving an area-versus-latency tradeoff.

The final implementation depends on operand width, timing, area and power constraints and the target technology. Also, constant multiplications or divisions can often be optimized into shifts, additions or other simpler logic. So the **\*** or **/** operator at RTL is an arithmetic description, and synthesis determines the actual hardware implementation.

## Follow-up: What happens if I write a * 8 instead of a * b?

Because 8 is a constant power of two, synthesis can optimize the multiplication into a left shift, essentially a \<\< 3 for unsigned arithmetic. This is much simpler than implementing a general variable multiplier. Similarly, unsigned division by 8 can be implemented as a right shift by 3, subject to the usual signedness and rounding considerations.
