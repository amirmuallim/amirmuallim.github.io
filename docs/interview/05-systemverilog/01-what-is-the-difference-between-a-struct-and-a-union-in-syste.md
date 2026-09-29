---
tags:
  - SystemVerilog
title: "What is the difference between a struct and a union in\u2026"
---

# What is the difference between a struct and a union in SystemVerilog, and why would you use a tagged union in verification or RTL?

## Answer

In SystemVerilog, a **struct** is a composite data type to group multiple variables of diff data types under a single name, it allocates separate memory for every member, so all members coexist simultaneously. total size is the sum of all members.

A **union** shares a single memory space equal to the size of its largest member; updating one member overwrites the others.

Tagged union enforces that the last written member is accessed , preventing invalid memory reads. Whereas std unions allow raw , untyped bit interpretation, which can cause silent bugs.

??? question "Follow-up: Are SystemVerilog structs packed or unpacked by default, and how does that impact synthesis?"

    "By default, structs are **unpacked**, meaning members are stored in unaligned memory words. For RTL synthesis and vector operations, we must explicitly declare them as packed struct. A packed struct is laid out as a continuous, bit-wise vector, allowing vector operations, slicing, and clean RTL logic synthesis.
