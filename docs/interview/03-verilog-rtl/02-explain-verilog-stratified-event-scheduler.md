---
tags:
  - Verilog
title: "Explain verilog stratified event scheduler?"
---

# Explain verilog stratified event scheduler?

## Answer

The Verilog stratified event scheduler defines how simulation events are ordered and processed within a simulation time step. Verilog divides events into different scheduling regions rather than executing everything simply from top to bottom.

Active

always blocks triggered by an event, blocking assignments =, evaluation of RHS of nonblocking assignments \<= , continuous assignment updates , $display $write

→ Inactive

**zero-delay \#0 assignments**. → NBA → Monitor $strobe, $monitor
