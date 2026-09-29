---
tags:
  - Digital-Electronics
title: "What is the race-around condition?"
---

# What is the race-around condition? Explain it in case of J-K Latch and solution to avoid that?

## Answer

The race around condition means: the output oscillates between 0s & 1s

Race-around condition occurs in a level-sensitive JK latch when J and K are both 1 and the latch remains enabled for a sufficiently long time.

We can avoid it by using an **edge-triggered JK flip-flop** or a **master-slave JK flip-flop**, where the feedback cannot cause repeated toggling during the same active clock period

JK LATCH ↓ J = K = 1 ↓ Toggle mode ↓ Latch is level-sensitive ↓ Q changes ↓ Q feeds back ↓ Q changes again ↓ Repeated toggling during same clock pulse ↓ RACE-AROUND CONDITION ↓ Use EDGE-TRIGGERED or MASTER-SLAVE FF
