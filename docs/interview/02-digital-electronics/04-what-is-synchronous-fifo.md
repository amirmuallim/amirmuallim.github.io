---
tags:
  - Digital-Electronics
---

# What is Synchronous FIFO?


**A synchronous FIFO (First-In, First-Out) is a memory-based data buffer where both the read and write operations are controlled by the same clock. Data is written into the FIFO in a particular order and read out in the same order.**

It is mainly used to temporarily store data when the producer and consumer operate at different rates, but **within the same clock domain**.

A typical synchronous FIFO consists of **memory, write and read pointers, and status logic**. The write pointer indicates where the next data will be written, while the read pointer indicates where the next data will be read. The FIFO generates **full** and **empty** flags to prevent writing when the FIFO is full and reading when it is empty.

## Follow-up: How do you detect full and empty?

**Empty:** read pointer equals write pointer.

**Full:** the write pointer has caught up with the read pointer after the FIFO capacity is used.

Since the same pointer positions can also represent an empty FIFO, an additional wrap-around bit is typically used to distinguish full from empty.
