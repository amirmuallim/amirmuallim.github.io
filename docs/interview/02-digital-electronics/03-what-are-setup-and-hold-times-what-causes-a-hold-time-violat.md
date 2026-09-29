---
tags:
  - Digital-Electronics
---

# What are Setup and Hold times? What causes a Hold Time violation, and how can you fix it in RTL versus physical design?


Setup time is the min time for which the i/p signal must be stable before active clk edge and hold time is the min time for which the i/p signal must be stable after active clk edge. IN A FF TO AVOID ANY VIOLATIONS AND FOR CORRECT Behaviour of the ff.

What causes a hold violation: the data path between the launch flop and the capture flop is too fast relative to the clock skew between them

**In RTL**: you generally can't fix hold violations through RTL coding style — hold is a physical/timing issue, not a functional one.

**In Physical Design / Backend:** We insert delay buffers into the data path or adjust clock skew (positive skew) to delay the clock edge reaching the capture register."

## Follow-up: Can you resolve a Hold Time violation by slowing down or speeding up the clock frequency? Why or why not?

No, changing the clock frequency has zero effect on hold time violations. Hold time stability depends purely on internal propagation delays ($T_{\text{cq}} + T_{\text{comb}} \ge T_{\text{hold}}$). Because both the launch and capture edges shift together when frequency changes, the timing window between them remains constant."
