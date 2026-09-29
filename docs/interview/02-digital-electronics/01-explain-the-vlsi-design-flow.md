---
tags:
  - Digital-Electronics
title: "Explain the VLSI design flow"
---

# Explain the VLSI design flow

## Answer

The VLSI design flow starts with the specification, where the required functionality and performance are defined. Then we develop the architecture and microarchitecture and implement it as RTL using Verilog or SystemVerilog. The RTL is functionally verified using simulation, assertions, coverage, formal methods and methodologies such as UVM.

After verification, the RTL is synthesized into a gate-level netlist using a target technology library. The physical design flow then starts with floorplanning, followed by placement, clock tree synthesis and routing. After routing, parasitic R and C values are extracted and used for accurate static timing analysis.

Finally, physical verification such as DRC, LVS and ERC, along with timing, power, IR-drop and electromigration checks, are performed during signoff. Once the design passes signoff, the final layout database such as GDSII is sent for tapeout and fabrication.

Specification \> Arch & Micro Arch \> RTL \> Verification (sim, assertions, coverage, formal methods, uvm) \> Synthesized \> Gate level netlist \> dft insertion \> floorplanning \> placement \> ctc \> routing \> sta \> physical verification( drc, lvs, electrical rule check, timing are performed during signoff) \>final layout database as GDSII is sent for tapeout and fabrication.
