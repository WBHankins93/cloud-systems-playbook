# Cloud Engineering Ecosystem — Single Source of Truth (SSOT)

Owner: Ben Hankins  
Status: Canonical  
Last Updated: 2026-01-22  

This document defines the structure, intent, boundaries, and operating rules
for the Cloud Engineering Ecosystem.

It is the single authoritative reference.
If any other document conflicts with this one, this document wins.

---

## 1. Purpose

This ecosystem exists to codify and demonstrate **senior cloud engineering judgment**.

Not tool familiarity.  
Not tutorials.  
Not isolated labs.

Senior cloud engineering is defined by:
- Ownership under constraints
- Decision-making over time
- Tradeoffs explained with rigor
- Systems that survive failure, change, and growth

This ecosystem encodes those realities explicitly.

---

## 2. High-Level Model (Final, Locked)

The ecosystem consists of:

- **1 Flagship / Beacon Repository**
- **3 Satellite Repositories**
- **Existing Studio Repositories (linked assets, not duplicated)**

There is **one** flagship.  
There are **three** satellites.  
Everything else supports or links into this structure.

---

## 3. The Flagship / Beacon Repository (Unified Entity)

### Identity

The Beacon and the Flagship are the **same repository**.

Working name:

**cloud-systems-playbook**

This repository is:
- The canonical source of truth
- The mental model
- The system narrative
- The artifact that is pinned and shared publicly

---

### Purpose

The Flagship repository represents:

A fictional but realistic cloud system, treated as a long-lived production
platform, through which senior cloud engineering judgment is expressed.

This repository answers:
- How do I think about systems?
- Why do I choose certain architectures?
- How do constraints shape decisions?
- How do systems evolve over time?
- What happens when things fail?

---

## 4. The Flagship System (Core Concept)

The Flagship repository is anchored to **one system**.

This system:
- Is realistic, not a toy
- Has explicit constraints
- Evolves over time
- Accumulates failures and tradeoffs
- Is treated mentally as “always-on”

It is **not**:
- A generic tutorial
- A collection of unrelated labs
- A “build X from scratch” demo

All frameworks, checklists, and artifacts in the Flagship repository are expressed
**through the context of this single system**.

---

## 5. Responsibilities of the Flagship Repository

The Flagship repository owns:

- Problem statement and business context
- Explicit constraints (technical, organizational, regulatory)
- Architecture decisions and ADRs
- Infrastructure structure and philosophy
- Platform design (Kubernetes, GitOps, observability)
- CI/CD and change management approach
- Reliability practices (SLOs, SLIs, runbooks, postmortems)
- Security model and controls
- Cost awareness and sustainability
- Narrative over time (iteration, refactor, failure, improvement)

It may include:
- Select Terraform
- Select pipeline definitions
- Select Kubernetes manifests or configs

Only when those artifacts are essential to the system narrative.

---

## 6. Canonical Flagship Repository Structure

```text
cloud-systems-playbook/
├── SOURCE_OF_TRUTH.md
├── README.md
├── 00-context/
│   ├── problem-statement.md
│   ├── constraints.md
│   └── success-metrics.md
├── 01-architecture/
│   ├── initial-design.md
│   ├── alternatives-considered.md
│   └── decision-records/
├── 02-infrastructure/
├── 03-platform/
├── 04-delivery/
├── 05-reliability/
├── 06-security/
├── 07-cost/
```

This structure reflects how senior engineers reason about systems.

---

## 7. Satellite Repositories (Supporting, Focused Proof)

Satellite repositories exist to:

- Isolate practice
- Keep the Flagship readable
- Demonstrate skill without bloating the system narrative

They are supporting actors, not competing centers of gravity.

### The Three Satellite Repositories

**cloud-coding-drills**  
Interview-style scripting and automation exercises

**cloud-system-design**  
Standalone architecture prompts and reasoning  
Alternate designs and tradeoffs

**cloud-troubleshooting-labs**  
Failure scenarios, debugging walkthroughs, incident-style work

---

## 8. Existing Repositories (Linked Assets)

The following repositories already exist and remain valid:

- implementation-studio
- devops-studio

### Rules:

- If strong content exists there, link to it
- Do not duplicate it in the Flagship or satellites
- Add context in the Flagship explaining why it matters

---

## 9. Linking Rules (Non-Negotiable)

Every artifact has one home

- Flagship = narrative and judgment
- Satellites = focused execution
- Studios = deep reference implementations

Link rather than copy whenever possible

If unsure where something belongs:

- Default to the Flagship
- Link outward instead of duplicating

---

## 10. Build Order (Locked)

- Build and complete the Flagship repository first
- Only then create satellite repositories
- Satellites evolve incrementally as needed
- Studio repositories remain stable references

No exceptions.

---

## 11. Quality Bar

This ecosystem is successful when:

- A hiring manager understands senior judgment in 15 minutes
- A staff or principal interviewer can go deep for an hour
- This system remains useful as a professional reference for years

This is not interview prep.  
It is professional signal.

---

## 12. Final Agreement

- One Flagship / Beacon repository
- Three Satellite repositories
- One Single Source of Truth
- Link, don't duplicate
- Judgment over novelty
- Systems over tools


---

### ✅ You are clear to proceed

You can now:
- Paste this into Cursor
- Commit it as-is
- Scaffold empty directories
- Move forward without revisiting structure again

**Next correct step:**  
Write `00-context/problem-statement.md`

When you’re ready, we’ll define the system itself.
