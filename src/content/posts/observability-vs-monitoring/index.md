---
title: 'Monitoring vs Observability'
published: 2025-10-26
draft: false
tags: ['observability', 'monitoring', 'devops']
description: 'Summary of key differences between monitoring and observability explained by Better Stack.'
---

Summary of key differences between monitoring and observability explained by **Better Stack** in YouTube: [*Observability vs Monitoring - Whats the difference?*](https://www.youtube.com/watch?v=ytx6jr2TyxI).

## 1. Monitoring
Monitoring is the process of **collecting, analyzing**, and using data to **track the performance and health** of systems. It typically involves predefined metrics and alerts to notify when something goes wrong.

![Monitoring Example](./monitoring-example.png 'Monitoring Example')

It is the practice of **continuously tracking system performance/health** through **metrics, logs, and traces** to ensure reliability and availability.

![Example of Key Metrics](./key-metrics.png 'Example of Key Metrics')

## 2. Key Monitoring Metrics
1. **CPU Usage**: The percentage of CPU capacity being used by your application.
2. **Memory Usage**: The amount of RAM being consumed by your application.
3. **Disk I/O**: The rate of read and write operations on your disk.
4. **Network Traffic**: The amount of data being sent and received over the network.
5. **Error Rates**: The frequency of errors occurring in your application.
6. **Response Times**: The time it takes for your application to respond to requests.
7. **Uptime/Downtime**: The amount of time your application is available and operational versus the time it is not.
8. **Throughput**: The number of requests your application can handle per unit of time.
9. **Latency**: The delay between a request being made and the response being received.

And more...

## 3. Limitations of Monitoring
Monitoring focuses on **known issues** and **predefined metrics**. That means, it is designed to alert you to **problems that you've anticipated in advance**. Therefore, you **can't really monitor the unexpected issues** that you haven't defined metrics for.

Also, monitoring **cannot provide deep insights into the root causes of complex issues**, as it often lacks context and correlation between different data sources. Questions like "***Why the CPU just went above 80%?***" or "***What caused the sudden spike in latency?***" may remain unanswered with traditional monitoring alone.


## 4. Observability
Observability is a measure of how well you can **understand the internal state of a system** based on the data it produces, such as **logs, metrics, and traces**. It enables you to **investigate and diagnose issues**, even those that were not anticipated.

![Observability Tools](./observability-key-tools.png 'Observability Tools')

Observability provides **context** allowing you to know **why** something is happening in your system, **how** it got there, and **when** & **where** exactly it occurred.

![Issue Context](./issue-context.png 'Issue Context')

# 5. Key Observability Pillars
1. **Logs**: Detailed records of events that happen within your system, providing insights into specific actions and errors.
2. **Metrics**: Quantitative data that measures various aspects of system performance, such as response times, error rates, and resource utilization.
3. **Traces**: End-to-end records of requests as they flow through different services, helping to identify bottlenecks and latency issues.

![Structured Logs Example](./structured-logs.png 'Structured Logs Example')


## 6. Key Differences Between Monitoring and Observability
1. Monitoring is your **early warning system**, but observability is your **detective** that helps you **investigate and solve problems**.
2. Monitoring tells you if **something is wrong** (e.g. high CPU usage), while observability helps you understand **why it's wrong** (e.g. a memory leak in a specific service).
3. Monitoring is the "**what**" (e.g. high error rates) and "**when**" (e.g. the error occurred at 2 PM), while observability is the "**why**" (e.g. a recent deployment introduced a bug) and "**how**" (e.g. the specific code path that led to the error).