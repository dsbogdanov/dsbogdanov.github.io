---
title: When and why data driven solutions for industrials and energy rocks
layout: post
date: 2024-05-22 12:00
image: /assets/images/markdown.jpg
headerImage: false
tag:
    - iiot
category: blog
author: dmitrybogdanov
description: When and why data driven solutions for industrials and energy rocks
---

### Introduction
Here, I use the term "data-driven" instead of the hyped "AI/ML" because it allows for a better understanding of the topic's roots. When we call them "data-driven solutions," we distinguish them from "human-only-driven solutions". Starting from a human perspective, we can build a framework to use.

In most cases, people continue to handle operations of data-driven solutions. So, "data-driven" is not equivalent to "without-human." Of course, there is a lot of automation and expert systems supporting human decisions, but for simplicity, I am not going to delve into that.

### Human approach
When we talk about people planning and controlling technological processes, we need to highlight some features:
- People understand the physics of technological processes. They are experts in the domain.
- People's control is based on their experience ("what worked earlier is what I am doing now").
- People love stability. If the process variables are stable, they will not take any actions to "step on the gas".
- People naturally fail to find optimal values when the objective is non-linear and uncertainty is high.
I leave it to you to think a little bit about the restrictions of human nature and continue the list.

### Ways to build a solution
When you want to build a data-driven solution or product for industrials, you could start with:

1. Gaining expertise in the domain
    For example, you will fail to decrease power losses in a grid by 1-3% if you don't understand how it works, even if you know how to measure losses or have a PhD degree in statistics. Additionally, nobody will talk to you on site if you don't speak their professional slang.
2. Building a bridge between technological indicators and money
    Find out how are revenue and costs related to the technological indicators.
3. Identifying and improving weak points of human-only solutions
    Look for areas where human-only solutions are not performing well and improve them with data. Focus on areas where uncertainty in processes is high. Beating human-only solutions on efficiency is not about being better all the time. Your solution could be better on average over a given time window.

**Advanced Process Control (APC)** commonly uses data to build models predicting process controlled variables (CVs) and utilizes these predictions to stabilize CVs. This approach allows for operating "on the edge," where operators may not be comfortable with disturbances, but the quality, output, or other indicators are higher.

**Real-Time Optimization (RTO)** systems extensively use data models of processes and equipment (both hybrid and surrogate models) for predicting environmental indicators. These models are then incorporated into an optimization objective. The better an RTO predicts system behavior over a time interval, the more optimal production becomes in terms of output, quality, and efficiency.

**Predictive Maintenance** commonly uses two types of models: one that predicts the remaining useful life and another that identifies anomalies in behavior that could lead to equipment failures.
### How to check if data driven solution actually works
If you are a customer of a data-driven solution in the industrial sector, here’s how you can check if the vendor’s solution actually works:
- First, ban vendors who declare very high numbers of effects, such as "we reduce energy consumption by 40%". Seems like they will shut down or destroy 40% of your equipment to achieve that. Even 10-15 % is very strange for me. Typically, in the energy and industrial sectors, 0.5 to 3% improvements are achievable with a single data-driven solution. Achieving around 10% improvement usually requires many years and a combination of multiple solutions.
- Second, remember that impressive metrics of machine learning models, like MAPE or ROC-AUC, are not solution exactly. The true measure of success is real technological indicators and the ability to extract economic value. Amateurs often fail to understand the concept of overfitting and its implications.
- Third, only A/B testing allows to check if any solution works better than others and shows what it's worth. Ask vendors how they plan experiments, clean results from other factors and proof the effect.
- Lastly, ensure that the models are robust. Check how the solution performs when there are changes in processes, environments, or raw materials.

### Explainability and Change Management
Building a data-driven solution in the industrial and energy sectors is not about deploying state-of-the-art neural networks or advanced boosting algorithms. It's about incorporating these, or even simpler models, into processes where people need to understand the decisions made by the models. It should be easy to apply. While it's true that you can't always explain every single prediction made by the models, operators and other site staff need to understand the main idea at least.

Without an explanation of principles, predictability, and integration into everyday life, the models will be useless. And that's just one problem. Delivering a data-driven solution requires extensive work in change management, which is another story altogether.
