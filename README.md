# Cloud Systems Playbook

**The Flagship Repository** — A production-grade cloud system that demonstrates senior cloud engineering judgment.

---

## What This Is

This repository represents a fictional but realistic cloud system, treated as a long-lived production platform. It serves as a vehicle for expressing how senior cloud engineers think about systems, make decisions, and navigate constraints over time.

This is **not**:
- A tutorial or step-by-step guide
- A collection of isolated labs
- A "build X from scratch" demo
- Interview prep material

This **is**:
- A demonstration of ownership under constraints
- A record of decision-making over time
- An explanation of tradeoffs with rigor
- A system designed to survive failure, change, and growth

---

## Purpose

This repository answers:
- How do I think about systems?
- Why do I choose certain architectures?
- How do constraints shape decisions?
- How do systems evolve over time?
- What happens when things fail?

It encodes the realities of senior cloud engineering explicitly.

---

## Repository Structure

This repository is organized to reflect how senior engineers reason about systems:

```
cloud-systems-playbook/
├── SOURCE_OF_TRUTH.md          # Canonical reference for this ecosystem
├── README.md                    # This file
├── 00-context/                  # Problem, constraints, success metrics
├── 01-architecture/             # Design decisions and ADRs
├── 02-infrastructure/           # Infrastructure structure and philosophy
├── 03-platform/                 # Platform design (K8s, GitOps, observability)
├── 04-delivery/                 # CI/CD and change management
├── 05-reliability/              # SLOs, SLIs, runbooks, postmortems
├── 06-security/                 # Security model and controls
└── 07-cost/                     # Cost awareness and sustainability
```

Each section contains the narrative, decisions, and select artifacts essential to understanding the system.

---

## The System

This repository is anchored to **one system**—a realistic, constrained, evolving platform that is treated mentally as "always-on." All frameworks, checklists, and artifacts are expressed through the context of this single system.

The system definition begins in [`00-context/`](./00-context/).

---

## Ecosystem Context

This repository is the **Flagship / Beacon** of a larger ecosystem:

- **This repository** (cloud-systems-playbook): The canonical source of truth, mental model, and system narrative
- **Satellite repositories**: Focused proof and practice (cloud-coding-drills, cloud-system-design, cloud-troubleshooting-labs)
- **Studio repositories**: Deep reference implementations (implementation-studio, devops-studio)

See [`SOURCE_OF_TRUTH.md`](./SOURCE_OF_TRUTH.md) for the complete ecosystem structure and operating rules.

---

## Quality Bar

This ecosystem is successful when:
- A hiring manager understands senior judgment in 15 minutes
- A staff or principal interviewer can go deep for an hour
- This system remains useful as a professional reference for years

This is professional signal, not interview prep.

---

## Owner

**Ben Hankins**

---

## Status

**Canonical** — This is the single authoritative reference. If any other document conflicts with this repository, this repository wins.

Last Updated: 2026-01-22

---

## Getting Started

1. Read [`SOURCE_OF_TRUTH.md`](./SOURCE_OF_TRUTH.md) for the complete context and operating rules
2. Start with [`00-context/`](./00-context/) to understand the problem, constraints, and success metrics
3. Follow the narrative through each section to see how the system is designed, built, and operated

---

## Principles

- **Judgment over novelty**: We prioritize sound engineering judgment over cutting-edge technology
- **Systems over tools**: We focus on system thinking, not tool familiarity
- **Link, don't duplicate**: Every artifact has one home; we link rather than copy
- **Narrative over artifacts**: Code and configs support the story, not the other way around
