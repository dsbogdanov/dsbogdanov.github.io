---
title: "Data quality for APC and RTO systems"
layout: post
date: 2024-04-03 15:00
image: /assets/images/markdown.jpg
headerImage: false
tag:
- APC
- IIoT
star: true
category: blog
author: dmitrybogdanov
description: Data quality for APC and RTO systems
---

Advanced process control is a wrapper around standard PID process control. Main golas of APC systems are:

1. Stabilize controlled variables (CVs) of the process
2. Shift setpoints of CVs closer to most performant/effective/optimized values


PCLs of standard processs control working in real-time directly with measurements signals and actuators. Processing of sensors data and modulation of control are executed in PLC's hardware and low level software modules. PLCs provide statuses of connected sensors and actuators to application level. 

If something go wrong it is alarming operators and events propagets higher. Redundancy and duplication allow to mitigates these problems. Some fallback actions could be executed includint shutdown controlled equimpent.

APC working with preprocessed data and get statuses alerady calcualted on low level PLCs. But communication link between PLCs and APC software could bring some issues in operations. If something go wrong APC should gave some fallback tactics like disconnecton from control loop or transition to operate in open loop (provide operators control on the actions). 

So for data-driven control strategies implemented in APC it is even more crutial to diagnose data and feedback loop. We done it with:
1. Analyze standart deviaton of measurements
2. Sticking of measurement on a single value
3. Control that measurement is on sensor range or it is clipped by range limits
4. Measurements delay
5. Control actions (setpoints) applied into PLCs
6. Diagnose communication link with PCLc/SCADA withing heartbeats and counters 

