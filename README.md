# Cloud Systems Playbook

**The Flagship Repository** — Where senior cloud engineering judgment meets production reality.

---

## What This Is (And What It's Not)

This isn't another tutorial. It's not a collection of "hello world" examples. It's not interview prep disguised as a portfolio.

**This is a production-grade cloud system**—fictional but realistic, constrained but ambitious, evolving but stable. It's treated as if it's always-on, always-critical, always under scrutiny.

Think of it as a **time machine for engineering judgment**: you can see how decisions were made, why tradeoffs were accepted, and what constraints shaped the outcome. Every choice has a rationale. Every compromise has a story.

### What You Won't Find Here

❌ Step-by-step tutorials  
❌ Isolated lab exercises  
❌ "Build X in 30 minutes" demos  
❌ Technology showcases without context  

### What You Will Find

✅ **Ownership under constraints** — Real budgets, real timelines, real team sizes  
✅ **Decision-making over time** — Architecture that evolves, not just initial design  
✅ **Tradeoffs explained with rigor** — Why we chose X over Y, and what we gave up  
✅ **Systems that survive** — Failure, change, growth, and the unexpected  

---

## The Questions This Repository Answers

When you're building production systems, the hard questions aren't about which tool to use. They're about:

- **How do I think about systems?** Not just what to build, but how to reason about it
- **Why this architecture?** What constraints made this the right choice (for now)?
- **How do constraints shape decisions?** Budget, team size, compliance—they all matter
- **How do systems evolve?** What changes when requirements shift or scale increases?
- **What happens when things fail?** Because they will. How do we handle it?

This repository encodes those realities **explicitly**. No hand-waving. No "it depends" without explanation.

---

## Repository Structure

This repository is organized the way senior engineers actually think about systems—not by technology, but by concerns:

```
cloud-systems-playbook/
├── SOURCE_OF_TRUTH.md          # The golden standard—read this first
├── README.md                    # You are here
├── 00-context/                  # The problem, the constraints, the goals
├── 01-architecture/             # The big decisions and why they matter
├── 02-infrastructure/           # How the foundation is built
├── 03-platform/                 # Kubernetes, GitOps, observability—the platform layer
├── 04-delivery/                 # How code becomes production
├── 05-reliability/              # SLOs, runbooks, and the art of staying up
├── 06-security/                 # Security that's built in, not bolted on
└── 07-cost/                     # Because money matters, and it shows
```

Each section tells part of the story. Together, they show how a system comes to life.

---

## The System: DataFlow Platform

This repository is anchored to **one system**—the DataFlow Platform, a B2B SaaS customer data platform that processes millions of events per day.

Why one system? Because depth beats breadth. Because context matters. Because you can't demonstrate judgment with toy examples.

This system is:
- **Realistic** — Not a toy, not a tutorial, not a proof-of-concept
- **Constrained** — Real budgets, real teams, real compliance requirements
- **Evolving** — It changes over time, accumulates failures, learns from mistakes
- **Always-on** — Treated mentally as production, even if it's fictional

The system definition starts in [`00-context/`](./00-context/)—the problem, the constraints, and what success looks like.

---

## Ecosystem Context

This repository is the **Flagship / Beacon** of a larger ecosystem. It's the center of gravity.

- **This repository** (cloud-systems-playbook): The canonical source of truth, the mental model, the narrative
- **Satellite repositories**: Focused proof and practice (cloud-coding-drills, cloud-system-design, cloud-troubleshooting-labs)
- **Studio repositories**: Deep reference implementations (implementation-studio, devops-studio)

Think of it like a solar system: this is the sun. Everything else orbits around it.

See [`SOURCE_OF_TRUTH.md`](./SOURCE_OF_TRUTH.md) for the complete ecosystem structure and operating rules.

---

## The Quality Bar

This ecosystem succeeds when:

- **A hiring manager** can understand senior judgment in 15 minutes
- **A staff or principal engineer** can go deep for an hour and still find value
- **You** can use this as a professional reference for years

This is **professional signal**, not interview prep. It's the difference between "I know Kubernetes" and "I know how to make Kubernetes work under constraints."

---

## Owner

**Ben Hankins**

---

## Status

**Canonical** — This is the single authoritative reference. If any other document conflicts with this repository, this repository wins.

Last Updated: 2026-01-22

---

## Getting Started

Ready to dive in? Here's the path:

1. **Start with the source of truth**: Read [`SOURCE_OF_TRUTH.md`](./SOURCE_OF_TRUTH.md) to understand the ecosystem and operating rules
2. **Understand the problem**: Go to [`00-context/`](./00-context/) to see what we're building and why
3. **Follow the narrative**: Work through each section to see how the system is designed, built, and operated

The story unfolds section by section. Each decision builds on the last. Each constraint shapes what comes next.

---

## Principles

These principles guide every decision in this repository:

- **🎯 Judgment over novelty**: We prioritize sound engineering judgment over cutting-edge technology. The right tool for the job, not the newest tool in the box.

- **🧠 Systems over tools**: We focus on system thinking, not tool familiarity. Understanding why matters more than knowing how.

- **🔗 Link, don't duplicate**: Every artifact has one home. We link rather than copy. DRY applies to documentation too.

- **📖 Narrative over artifacts**: Code and configs support the story, not the other way around. The why comes before the what.

---

## What Makes This Different

Most engineering portfolios show **what** you built. This shows **how** you think.

Most tutorials show you the happy path. This shows you the constraints, the tradeoffs, the failures.

Most examples are isolated. This is a complete system, end-to-end, with all the messiness that comes with real production.

**This is how senior engineers actually work.** Not in isolation, but under constraints. Not with perfect information, but with judgment. Not with unlimited resources, but with tradeoffs.

Welcome to the playbook.
