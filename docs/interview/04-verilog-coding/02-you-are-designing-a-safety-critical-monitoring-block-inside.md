---
tags:
  - Verilog
---

# Parity-safe counter (safety-critical block)

## Question

You are designing a safety-critical monitoring block inside an SoC used for industrialcontrol. The block includes a counter whose output is continuously observed byfault-detection logic. Any violation of the expected parity on the counter output is treatedas a fatal system error.The counter operates under the following constraints:

- It is an N-bit synchronous counter clocked on the rising edge of clk
- A synchronous active-low reset initializes the counter to a value that is guaranteedto be parity-correct
- A runtime configuration input determines which parity class (odd or even) thecounter output must always satisfy
- The configuration input may change while the counter is running
- The counter must never output an illegal parity value, even for a single clock cycle
- The counter must continue progressing forward across configuration changes
- Natural wrap-around on overflow is allowed
- The design must be fully synthesizable and glitch-free

## Code (from your notes)

```verilog title="parity_safe_counter.v" linenums="1"
module parity_safe_counter #(
    parameter N = 4
)(
    input  wire         clk,
    input  wire         rst_n,       // Synchronous active-low reset
    input  wire         cfg_parity,  // Required parity (0 = even, 1 = odd)
    output reg  [N-1:0] count
);

    always @(posedge clk) begin
        if (!rst_n) begin
            // Reset to a guaranteed parity-correct value (LSB enforces parity, upper bits = 0)
            count <= cfg_parity;
        end else begin
            // Runtime parity enforcement
            if (count[0] != cfg_parity) begin
                // Immediate correction on configuration change
                count <= count + 1'b1;
            end else begin
                // Normal operation: preserve parity
                count <= count + 2'b10;
            end
        end
    end

endmodule
```

!!! danger "Check this before an interview"
    This treats *parity* as the LSB (`count[0]`). Parity of the counter output means the XOR of **all** bits (odd/even number of 1s). Example with `N=4`, odd parity: reset gives `0001` (odd, good), then `+2` gives `0011`, which has two 1s (even, illegal). It also lets the output be illegal for a cycle after `cfg_parity` changes, because the register is only corrected on the next clock. The fix needs a parity-aware next-state and a combinational output correction; ask me and I will write and simulate a corrected version.
