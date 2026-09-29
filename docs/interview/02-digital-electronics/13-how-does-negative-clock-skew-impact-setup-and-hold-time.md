---
tags:
  - Digital-Electronics
title: "How does negative clock skew impact setup and hold time?"
---

# How does negative clock skew impact setup and hold time?

## Answer

**Negative skew → capture comes early → less setup time, but more hold margin.**

Negative clock skew means the capture clock arrives earlier than the launch clock. This reduces the time available for data to travel from the launch flip-flop to the capture flip-flop, so it hurts setup timing and makes setup violations more likely. For hold timing, the launch edge occurs later relative to the capture edge, so the new data starts changing later. This gives more hold margin, so negative skew generally helps hold timing. In short, negative skew hurts setup but helps hold, while positive skew has the opposite effect.
