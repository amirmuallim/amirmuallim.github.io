---
tags:
  - UVM
title: "What is factory registration in UVM, and why is it important?"
---

# What is factory registration in UVM, and why is it important?

## Answer

**Factory registration means registering a UVM class with the UVM factory so that the factory knows about that class and can create and override objects or components of that type.**

We normally do this using macros such as uvm_object_utils for objects and uvm_component_utils for components.

Once registered, instead of directly creating an object using new(), we can use type_id::create(). This allows the UVM factory to decide which actual class should be created.

The main advantage is **reusability and flexibility**.
