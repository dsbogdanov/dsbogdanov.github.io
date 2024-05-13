---
title: Industrial cybersecurity from the developers's perspective
layout: post
date: 2024-05-13 12:00
image: /assets/images/markdown.jpg
headerImage: false
tag:
    - iiot
    - cybersecurity
category: blog
author: dmitrybogdanov
description: Industrial cybersecurity from the developers's perspective
---

### Introduction

To note, I'm not a cybersecurity expert, and this entire article is based on my experience in developing and delivering industrial software within IT/OT environments of industrial sites.

In my job, I often encounter a poor perception of cybersecurity requirements among developers, engineers, and managers. In most cases, they fail to grasp why these requirements are necessary and complain that implementing them is overwhelming and unnecessary. This work may not seem to directly contribute value or profit, as it incurs significant costs and appears excessive to them. The underlying reason for such sentiments is that few people understand the full context of cybersecurity activities.

Hereafter, I'll try to fix that. 

### The source of requirements

Any system deployed in an IT or OT environment is a source of risks. There are numerous threats and vulnerabilities surrounding your system that should be managed by your customer.

Potential major consequences of poor cybersecurity management for industrial operations could include production shutdowns, equipment damage, staff injuries, and fatalities. Therefore, all requirements come from management policies.

Basically, cybersecurity activities could be classified according to their functions: 

1. Identify: 
	- asset inventory
	- software inventory
	- connections inventory
	- ...
1. Protect: 
	- securing connections
	- setup access restrictions
	- ...
1. Detect: 
	- establish monitoring of incidents
	- ...
1. Respond: 
	- build response plan to incidents
	- test response plan
	- ...
1. Recover: 
	- build backup strategies for software and equipment
	- build disaster recovery plan (DRP) and test it

The specific requirements for any system depend on this list and the system's functionality (DCS, SCADA, APC, RTO, industrial CV, etc.). There will be many more requirements if the system can control equipment (automatically writes setpoints, turning equipment on and off) compared to system deployed in a corporate network just for processing and visualizing production or energy data.

Implementing these requirements into software and solutions is the first step in establishing such activities. Therefore, if someone asks you to document each network connection and the versions of all components and libraries/packages, it's not about bureaucracy, it's about mitigating risks. Without such documentation, the next level of protection could fail during an attack due to open TCP ports or the use of libraries with critical vulnerabilities.

### How customer use implemented requirements
After the customer provides requirements, the developers and delivery team implement them. And then what's next? Here are examples of cybersecurity requirements implementation:

| #   | Your work | Customer activities | Purpose |
| --- | --- | --- | --- |
| 1   | Build an inventory of servers, workstations, operating systems, your software, and connections to PLCs/SCADA and IT services | Use it to establish monitoring of vulnerabilities and make updates | Enables the prevention of attacks using undocumented functionality, gray zones, and known issues |
| 2   | Protect connections to WEB UI, databases and other components with SSL/TLS and restrict access to resources | Manage certificates, test it periodically, maintain accounts | Protect from man-in-the-middle attacks |
| 3   | Setup audit logs and integrations with SIEM | Setup monitoring of user and service activities | Allows identification of hidden scanning activities and prevention of subsequent attacks |
| 4   | Setup backup and define DRP | Customer will maintain, test and manage it | Provides clear and fast system recovery and reduces downtime |


### Attention to details

Some vendors and system integrators highlight in their decks: "We pay major attention to cybersecurity". If you are one of them, check that you at least:

1. Use versions of components and libraries without critical vulnerabilities. 
2. Know cybersecurity issues of current versions and build strategies to mitigate them.
3. Have a proactive release and update policy, enabling customers to stay informed about critical issues and update software to resolve them.
4. Document connections, versions, close unused ports, use DMZ, ACL and other methods of connection restrictions. 
5. Use only secure connections whenever possible.
6. Understand, implement and document concepts of account classification, permissions and access restrictions. Block default accounts. 
7. Use authentication and authorization for each resource/component whenever possible. Setup strong password policies.
8. Provide flexibility in configuring user idle session timeouts.
9. Use antivirus solutions on each server and user workstation.
10. Have audit logs, integration logs and integrate your software into SIEM.
11. Develop a DRP for your system. Setup backup policies. 
12. Build test, pre-production and production environments on customer site and use them properly.

Of course provided lists of threats, activities and solutions are not full and depend on many factors, but I hope this overview help you with understanding of industrial cybersecurity context.

