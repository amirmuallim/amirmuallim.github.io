---
tags:
  - UVM
title: "Can you explain the UVM execution phases?"
---

# Can you explain the UVM execution phases? Which ones are function phases versus task phases, and why is run_phase unique?

## Answer

UVM phases manage testbench execution in an orderly sequence. They are divided into three main groups:

1.  **Build Phases:** build_phase (top-down), connect_phase (bottom-up), end_of_elaboration_phase, and start_of_simulation_phase. These are all **function phases**—they execute in zero simulation time.

2.  **Run Phase:** run_phase (and its sub-phases like reset_phase, main_phase). This is a **time-consuming task phase** that executes in parallel across all components using simulation time.

3.  **Clean-up Phases:** extract_phase, check_phase, report_phase, and final_phase. These are **function phases** executing bottom-up in zero time.

The run_phase is unique because it is the only phase where actual simulation time advances and driver/monitor activity occurs, governed by UVM objections (raise_objection / drop_objection).

??? question "Follow-up: Why is the build_phase executed top-down, but the connect_phase executed bottom-up?"

    build_phase runs **top-down** so parent components (like the test environment) can create and configure child components (like agents and drivers) using the UVM Configuration Database.

    connect_phase runs **bottom-up** because lower-level components must first instantiate their local TLM ports/exports before parent components can bind those connections upward to scoreboards or virtual sequencers.
