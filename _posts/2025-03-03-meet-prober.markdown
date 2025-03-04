---
layout: post
title:  "Meet prober! A simple tool to tech some k8s behaviors"
date:   2025-03-03 17:40:58 +0000
categories: k8s prober
---

Some months ago, I created `prober` – a tool designed to help developers understand the behavior of Kubernetes probes. I used it to simulate both success and failure cases while exploring different configurations and scenarios.

Later, the need arose to demonstrate the functionality of Kubernetes’ `preStop` and `terminationGracePeriodSeconds` to ensure that applications shut down properly. So, I added new features to prober that simulate scenarios with both fast and slow requests, generating examples of varying behaviors for these processes.

More recently, I needed a tool that could generate metrics in Prometheus to create examples of dashboards and alerts for tools handling web requests. Once again, prober evolved, gaining the ability to generate and make these metrics available.


Today, prober has proven to be an excellent way to share knowledge and demonstrate specific scenarios. That’s why I decided to share it here – who knows, it might help someone! If you have suggestions for new features to simulate everyday situations, I’m totally open to ideas!


[prober repository](https://github.com/hpettenuci/prober)