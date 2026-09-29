---
tags:
  - Verilog
title: "Illustrate the side-effects of a function return type without a\u2026"
---

# Illustrate the side-effects of a function return type without a range

## Answer

If the range of the function return type is not specified, Verilog assumes it to be a 1 bit scalar value. There would not be any compilation errors but it will result in a functional error.
