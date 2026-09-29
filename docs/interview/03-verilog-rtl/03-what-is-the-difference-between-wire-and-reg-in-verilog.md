---
tags:
  - Verilog
title: "What is the difference between wire and reg in Verilog?"
---

# What is the difference between wire and reg in Verilog?

## Answer

**The main difference between wire and reg is how they are driven in Verilog.**

A wire is a **net**. It represents a connection between hardware elements and must be driven by something such as a continuous assignment, a module output, or a gate output. It cannot be assigned inside a procedural block like an always block.

A reg is a **variable** that can be assigned inside procedural blocks such as always or initial. It retains its assigned value until it is updated again.

One important point is that reg does not necessarily mean a physical register or flip-flop. For example, if I use a reg in a combinational always @(\*) block, it can synthesize to combinational logic. If I use it in an edge-triggered always block, it can synthesize to a flip-flop.

So, in simple terms, wire is mainly used for continuously driven signals, while reg is used for signals assigned procedurally.
