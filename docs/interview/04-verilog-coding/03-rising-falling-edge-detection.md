---
tags:
  - Verilog
---

# Rising/falling/ Edge Detection


## Code (rising edge)

```systemverilog title="edge_detect.svh" linenums="1"
module edge_detect (
    input  logic clk,
    input  logic rst_n,
    input  logic sig_in,
    output logic pulse
);

    logic sig_d;

    always_ff @(posedge clk or negedge rst_n) begin
        if (!rst_n) begin
            sig_d <= 1'b0;
            pulse <= 1'b0;
        end
        else begin
            sig_d <= sig_in;
            pulse <= sig_in & ~sig_d;
        end
    end

endmodule
```

## Explanation

`sig_d` holds the previous sample of `sig_in`. A rising edge is the condition "now 1 and before 0": `sig_in & ~sig_d`. `pulse` is registered, so it is a clean one-cycle pulse that appears one clock after the edge.

=== "Falling edge"

    ```systemverilog
    pulse <= ~sig_in & sig_d;
    ```

=== "Both edges"

    ```systemverilog
    pulse <= sig_in ^ sig_d;
    ```

!!! warning "Common trap"
    `sig_in` must be synchronous to `clk`. An asynchronous input needs a 2-flop synchronizer first, otherwise metastability can corrupt `sig_d` and `pulse`.

