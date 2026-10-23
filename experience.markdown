---
layout: page
title: Experience
permalink: /experience/
description: Scope, decisions, complexity and impact from a career in DevOps, SRE and technology leadership.
---

This page focuses on scope, decisions, complexity and impact rather than lists of responsibilities. For a traditional chronological history, see the [full curriculum]({{ '/curriculum/' | relative_url }}).

## Current role: DevOps & SRE Manager

**Since 2021**

**Scope.** I lead the DevOps and SRE function: planning and priorities, alignment between engineering and business teams, high-level technical reviews, and mentoring the people on the team.

**Decisions.** What the team builds, what it standardizes and how its roadmap supports broader business objectives.

### Selected work

#### Building an incident-management practice and an SRE team

- **Scope:** built the process and the team from scratch and rolled it out across the technical teams over several months.
- **Decisions:** selected the incident tool, defined technical patterns and automation, and set the SRE team's mission and vision.
- **Complexity:** adoption had to happen across many teams, so training and knowledge transfer mattered as much as the tooling.
- **Impact:** a common process for incidents, and consistent postmortems and follow-up actions for major incidents.

#### An infrastructure-as-code lifecycle

- **Scope:** a framework that lets teams operate infrastructure as code through a clear development lifecycle, reused across many Terraform modules.
- **Decisions:** explored tooling and defined shared terminology so teams could talk about infrastructure changes the same way.
- **Complexity:** making a repeatable process fit many modules and teams without slowing delivery.
- **Impact:** automated drift detection, versioning and releases, hands-off operation of critical production components, and an easier path to roll out security and compliance improvements.

#### A zero-downtime Kubernetes migration

- **Scope:** coordinated and helped implement the move of cluster management from eksctl to Terraform, with Argo CD and a structured GitOps repository.
- **Decisions:** how to change cluster management without interrupting services.
- **Complexity:** zero downtime was a hard requirement.
- **Impact:** a migration with no downtime, better observability, faster node startup, right-sized components and a more predictable way to roll out Kubernetes changes.

#### AI-assisted engineering workflows

- **Scope:** led the team's adoption of AI in how it works day to day.
- **Decisions:** where AI helps most: ticket refinement, documentation of changes and pull request review, including scaffolding agents.
- **Impact:** faster feedback and review cycles, and less review effort.

## Earlier roles

- **Staff DevOps Engineer and tech lead:** made technical decisions on projects, guided other DevOps engineers, negotiated schedules with other teams and planned the roadmap for CI/CD tooling and application environments.
- **DevOps Engineer:** built CI/CD pipelines and automation, worked with software architects on practices and development processes, and helped collect delivery metrics such as MTTR and change failure rate.
- **Tech Lead and Cloud Engineer:** ran infrastructure on AWS, helped migrate legacy applications to the cloud, kept infrastructure as code under version control and took part in the technology board that set architectural standards.
- **Support and development roles (2009–2019):** administered a large warehouse management platform, supported development and operations teams, and worked on payment-system queues, ATM software and ERP and network servers.

{% include cta.html %}
