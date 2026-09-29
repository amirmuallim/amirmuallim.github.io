---
tags:
  - Verilog
title: "60% duty cycle code"
---

# 60% duty cycle code

## Code

```verilog title="clock_60_percent.v" linenums="1"
module clock_60_percent (
    input  wire clk,
    input  wire rst_n,
    output wire clk_60_percent
);

    // Parameters
    parameter MAX_COUNT      = 4; // Counter: 0 to 4 (5 states)
    parameter HIGH_THRESHOLD = 3; // HIGH for counts 0, 1, 2 – 3/5 = 60%

    reg [2:0] counter;

    // Output logic
    assign clk_60_percent = (counter < HIGH_THRESHOLD) ? 1'b1 : 1'b0;

    // Counter logic
    always @(posedge clk or negedge rst_n) begin
        if (!rst_n) begin
            counter <= 3'd0;
        end else begin
            if (counter == MAX_COUNT)
                counter <= 3'd0;
            else
                counter <= counter + 1'b1;
        end
    end

endmodule
```

## Explanation

The counter runs 0 → 4 (five states) and the output is high while `counter < 3`, i.e. for counts 0, 1, 2. That is 3 of 5 input clock cycles high, so the duty cycle is 3/5 = 60% and the output frequency is `clk / 5`.

!!! warning "Common trap"
    Here the output is a combinational compare on the counter, so it can glitch when the counter bits change. For a real clock output, register it (`always @(posedge clk) clk_60 <= (next_counter < 3)`) or drive it from a flop.

??? question "Likely follow-up: how do you get 50% with an odd divider?"
    Use a posedge-triggered and a negedge-triggered divider and OR their outputs (the standard odd-divide-by-N technique).
