---
title: Traits of industrial software products
layout: post
date: 2024-05-15 12:00
image: /assets/images/markdown.jpg
headerImage: false
tag:
    - iiot
category: blog
author: dmitrybogdanov
description: Traits of industrial software products
---

### Introduction

Building software products for industrial, energy, and IoT applications needs major attention to practices established in OT over the last decades. Typical product teams from cloud, banking, financial, and e-commerce sectors face the ugly truth that engineers, operators, and site managers need products tailored to the specific problems of industry and energy.

Best practices from the rapidly evolving IT industry are difficult to apply here. Metrics that are used for massive user-centric products fail when you try to set up data-driven decisions for industrial product roadmaps.

In this article, I'm introducing the main traits that industrial products should have.
Hereafter, I'll try to fix that. 

### Traits

##### Trees over flat structures

A tree structure for organizing all information is the main distinguishing feature of industrial software. Industrial staff are used to looking at data organized in a tree that matches the organizational structure of the site or company. Almost every major product for industrial applications supports it. It's easy to navigate, search, and filter signals and assets. Another idea is that you can restrict access to different types of nodes in the tree or grant access only to some subtrees. Even modern industrial communication protocols incorporate hierarchy: OPC UA, MQTT, IEC 61850, etc.

##### Process Flow Diagrams over BI-like Dashboards

Another major feature of industrial software is the use of diagrams that reflect real equipment and connections between units. Such diagrams also contain:

- real-time values of measurements and discrete signals
- controls to write setpoints in PLCs or send commands to equipment
- trends
- gauges
- tables with real-time or aggregated data

PFDs allow operators and other site staff to view the whole process with all dependencies and connections. Such ideas come from old analog control rooms with lights, buttons, and gauges put on the "wall". The common IT approach with BI-like dashboards is not widely used as the primary UI. Often, elements of such functionality are incorporated inside PFDs instead of building a separate tool.

##### Raw Time Series/Events Data over OLTP Data

Building industrial software requires a lot of energy spent on developing tools and managing time series data. In common IT industries, transactional data is the core of all operations.

So if you work a lot with MS SQL, Oracle, and Postgres, you will need to deep dive into the world of time series databases like InfluxDB, Timescale, or columnar analytics databases like Clickhouse or Vertica. OT products commonly create proprietary databases with specific features, often called Historians.

There are many challenges in finding tradeoffs between write and read performance, backup strategies, and moving data to cold storage, all while trying to avoid bloating hardware and maintenance costs of your solution.

##### On-Prem over Cloud

I see a lot of wasted energy from cloud providers trying to promote their IoT and analytics services to industrials. Industrials nowadays carefully diversify their corporate-side services and infrastructure to cloud solutions, but they are absolutely not going to shift their raw operational data and tools there, even for smart digital advisors. Huge cybersecurity threats and UIs not focused on OT specifics are the main reasons for this.

In 99% of all cases, your only-cloud solutions for industrial applications will lose to solutions deployed on technological networks closely to operations.

##### Engineering-Focused vs. Code-Focused Platforms

When common IT tools based on modern "everything as code" and Linux-based approaches start to seep into the OT environment, I start to hear bad feedback about awkward tooling.

The OT environment is built 99% on Windows technologies lately. Here, all interaction is built with forms, not with config files. Engineers who will use and maintain your solutions want:

1. To launch something like setup.exe to install or update software, not `helm install...` or `helm upgrade...`.
2. To fill in 10 forms, not crunch through 500 lines of YAML or JSON file.
3. To enter `10.5*P/U` to calculate something for a time interval, and not maintain hard-to-read multiline SQL code with joins, unions, and lots of filter clauses.

##### Maintain Remote Sites over Cutting-Edge DevOps

You need to be prepared for the lack of image registries, package repositories, and CI tools you are used to. Of course, your team could create such an environment for your project, but you need to understand that local staff probably will not be able to use and maintain it. After you put it into operation, nobody will allow you to make frequent updates because of the "Don't Break What Works" mentality.

This problem is not so huge for corporate networks where new technologies are implemented exponentially in the next few years, but the closer your product is to the "field" the less tooling will be available.

Another feature of remote and territorially distributed sites where your product will be deployed is that as you scale your business up, 50% or more of projects will be delivered by system integrators, not by your team. Therefore, it's crucial to have perfect documentation on almost everything related to the product, from installation to SSL/TLS certificate updates.

##### A/B Testing of Processes, Not Buttons

A/B testing of industrial solutions has less in common with user-facing products. The main goals of A/B testing would be to understand if new functionality and versions of algorithms bring more value in terms of production amount, quality, energy efficiency, or costs.

A/B testing could be based on testing alternatives on identical production lines or units. But much more often, it will test alternatives on the same equipment in different time intervals. You will need to adapt your experience to plan experiments for such a setup.

There is no LTV or CTR here. You could measure NPS, but this would involve direct conversations with operators, engineers, and other professionals. Be prepared for it.

### Conclusions

I'm not a fan of conservative approaches and legacy software. Modern IT tooling and products are so cool and allow for cost reduction, fast development, and great quality. But we need to build a bridge towards the OT environment and adapt to it. Yes, there are a lot of challenges in the world of industrial solutions, but everybody who I work with on developing and delivering such products absolutely loves it. Just as I do.
