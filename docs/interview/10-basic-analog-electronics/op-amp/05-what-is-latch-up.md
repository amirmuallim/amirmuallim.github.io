---
tags:
  - Analog-Basic-Electronics
---

# What is Latch-up?


**Definition:**

Latch-up is a condition in CMOS circuits where a parasitic structure creates a low-impedance path between power (VDD) and ground (VSS), leading to excessive current flow and potential chip damage.

**Cause:**

- **Parasitic PNPN structure** (forming an unintended thyristor/SCR).

- Triggered by excessive voltage spikes, high temperature, or improper biasing.

- Results in **uncontrolled current flow** once triggered.

**Prevention Techniques:**

- **Guard rings:** Adding N-well and P-well guard rings to break the parasitic path.

- **Proper substrate and well contacts:** Ensuring low resistance to prevent unwanted potential differences.

- **Design Rule Checks (DRC):** Following proper spacing guidelines for wells and transistors.

- **Using SOI (Silicon-On-Insulator):** Reduces latch-up susceptibility by eliminating the substrate connection.
