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

### What is APC?

Advanced process control (APC) utilizes advanced control techniques and strategies as the next level of control after basic PID-like process control. The main goals of APC systems are:

1. Stabilizing controlled variables (CVs) of the process
2. Shifting setpoints of CVs closer to the most performant/effective/optimized values

<div>
    <img class="image" src="{{ site.url }}/assets/images/01_apc_gain.png" alt="Alt Text">
    <figcaption class="caption">Classical APC explanation chart</figcaption>
</div>

APC utilizes measurements, current setpoints, and discrete signals from PLCs or data gateways of the control system. It then performs calculations and writes manipulated variable setpoints back to the PLCs or control system gateway. Thus, it operates within a closed control loop, with the entire cycle time interval typically ranging from 1 to 10 seconds.

### Basic process control

A basic control system interacts directly with sensors and actuators in real-time. Sensor data processing and control modulation occur on the hardware and low-level software modules of PLCs. PLCs diagnose and provide statuses of connected sensors and actuators to the application level. If an issue arises, operators are alerted through alarms. Redundancy and duplication in the control system help mitigate these problems. Additionally, some fallback actions, such as the shutdown of controlled equipment, can be executed at this level.

### APC case

Modern APC techniques rely heavily on data and require control over data quality and the feedback loop. APC operates with preprocessed data and may utilize statuses already calculated at the low-level PLCs. However, the communication link between PLCs/gateway and APC software can introduce additional operational challenges.

APC needs the following:

-   Availability of all signals
-   No gaps in the sequence of values
-   Authenticity of values (typical problems: sticking on the same value, outside of the sensor range, values are not stable)
-   Minimal latency in providing measurement values
-   Minimal latency in applying setpoints in PLCs

<div>
    <img class="image" src="{{ site.url }}/assets/images/01_gaps.png" alt="Alt Text">
    <figcaption class="caption">Example of a gap</figcaption>
</div>

<div>
    <img class="image" src="{{ site.url }}/assets/images/01_not_stable.png" alt="Alt Text">
    <figcaption class="caption">Examples of unstable sequence and out of range</figcaption>
</div>

<div>
    <img class="image" src="{{ site.url }}/assets/images/01_sticked_values.png" alt="Alt Text">
    <figcaption class="caption">Examples of sticked values</figcaption>
</div>

The real-time control of values and the feedback loop typically involves:

-   Measurement of latencies
-   Monitoring the control values sequence, its range, and standard deviation using sliding windows
-   Identification of whether setpoints are not applied within the timeout period

If something goes wrong, APC should:

-   Warn operators and, in some cases, continue to operate in a restricted mode or open loop, allowing operators to provide control actions.
-   Trigger alarms for operators and disconnect from the control loop.

This is just a basic overview of data quality for APC. I will provide examples of concrete problems and actions in future articles.
