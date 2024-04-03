---
title: Data quality for APC
layout: post
date: 2024-04-03 12:00
image: /assets/images/markdown.jpg
headerImage: false
tag:
- iiot
- apc
- rto
category: blog
author: dmitrybogdanov
description: Data quality for APC and RTO systems
---

### Introduction

Advanced process control is a wrapper around standard PID process control. The main goals of APC systems are:

1. Stabilize controlled variables (CVs) of the process.
1. Shift setpoints of CVs closer to the most performant/effective/optimized values.

<div>
        <img class="image" src="{{ site.url }}/assets/images/apc_gain.png" alt="Alt Text">
        <figcaption class="caption">Classical APC explanation chart</figcaption>
</div>

PLCs of standard process control work in real-time directly with measurement signals and actuators. Processing of sensor data and modulation of control are executed in PLCs' hardware and low-level software modules. PLCs provide statuses of connected sensors and actuators to the application level.

If something goes wrong, it alarms operators and events propagate higher. Redundancy and duplication allow mitigating these problems. Some fallback actions could be executed, including shutting down controlled equipment.

### APC case

APC works with preprocessed data and gets statuses already calculated on low-level PLCs. But the communication link between PLCs and APC software could bring some issues in operations. If something goes wrong, APC should have some fallback tactics like disconnection from the control loop or transition to operate in an open loop (providing operators control over the actions).

So for data-driven control strategies implemented in APC, it is even more crucial to diagnose data and feedback loops.

What should be under monitoring:
1. Standard deviation of measurements.
1. Sticking of measurement on a single value.
1. Control that values are within sensor range or not clipped by range limits.
1. Measurement delay.
1. Setpoints from APC applied to PLCs.
1. Communication link with PLCs/SCADA using heartbeats and counters circulated between software.
