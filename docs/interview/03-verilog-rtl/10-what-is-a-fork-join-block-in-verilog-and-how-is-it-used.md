---
tags:
  - Verilog
---

# What is a fork-join block in Verilog, and how is it used?


fork-join is used to create concurrent processes. All statements inside the fork execute in parallel, and with normal join, the parent process waits until all child processes complete. join_any allows the parent to continue when any one child completes, while join_none allows the parent to continue immediately without waiting.  
join_none and join_any are constructs of systemverilog
