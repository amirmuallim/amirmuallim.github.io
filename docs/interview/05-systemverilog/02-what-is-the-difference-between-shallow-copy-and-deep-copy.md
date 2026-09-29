---
tags:
  - SystemVerilog
---

# What is the difference between Shallow copy and Deep copy?


**The main difference is how nested objects are copied.**

In a shallow copy, a new object is created, but if the original object contains a handle to another object, only the handle is copied. So both the original and copied objects point to the same nested object.

In a deep copy, a new object is created and the nested objects are also separately created and copied. Therefore, the original and copied objects are completely independent.

For example, suppose a transaction object contains another object called header. With a shallow copy, both transactions will have handles pointing to the same header. If one transaction modifies that header, the other transaction sees the modification too.x

With a deep copy, each transaction gets its own header object, so modifying one doesn't affect the other.

## Follow-up: 
