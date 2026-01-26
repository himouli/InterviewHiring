Below is a **60-minute, high-signal interview plan** tailored specifically to **Harsh Tiwari’s resume** (Senior MTS / Staff-level backend & distributed systems profile), with:

* Time-boxed schedule
* **Project-anchored questions** mapped to his experience (Intel, VMware, NetApp, Adobe)
* **Expected STAR-style answer patterns** (data-driven, outcome-focused)
* **Probing follow-ups** to separate surface answers from deep ownership
* **Assessment rubric** to drive a **Hire / No-Hire** decision

All questions are grounded in the resume you shared. 

---

## 60-Minute Interview Structure (Senior MTS)

| Time      | Segment                      | Goal                                  |
| --------- | ---------------------------- | ------------------------------------- |
| 0–5 min   | Context & framing            | Set expectations, calibrate seniority |
| 5–20 min  | Deep project walkthrough     | Ownership, impact, decision making    |
| 20–35 min | Systems & domain design      | Distributed systems depth             |
| 35–50 min | Failure analysis & execution | Judgment under ambiguity              |
| 50–60 min | Leadership & hire signals    | Seniority, scope, independence        |

---

## 0–5 min — Framing & Seniority Calibration

**Question 1: Role & Scope Calibration**

> “In your last role at Intel and VMware, what was *your* ownership boundary — what were you personally accountable for delivering end-to-end?”

**Strong STAR Answer Should Include**

* **S**: конкрет project (e.g., Intel Audit Record System, Concord BFT)
* **T**: clear ownership (state transfer protocol, BFT client, Docker modernization)
* **A**: design decisions he drove himself
* **R**: metrics (throughput improved X%, build time reduced Y%, reliability gains)

**Probe**

* “What design decision here was controversial or non-obvious?”
* “What part would have failed if you weren’t involved?”

**Assessment Signal**

* ✅ Senior MTS: articulates **scope, trade-offs, and system boundaries**
* ❌ Weak: describes tasks, not ownership

---

## 5–20 min — Deep Project Walkthrough (Core Signal)

### Project 1: Intel Distributed Ledger – State Transfer Optimization

From resume: modularized state sync, built controllers, improved throughput. 

**Question 2: Architecture & Outcome**

> “Walk me through the original state synchronization design, the bottleneck you found, and how your modularization changed system behavior. Use numbers.”

**Expected STAR Pattern**

* **S**: Monolithic state transfer causing low throughput / fragility
* **T**: Improve maintainability + performance
* **A**:

  * Broke into Sync Controller, Events Manager, Transmission Manager
  * Defined interfaces, failure handling
* **R**:

  * Throughput ↑ (expect % or latency numbers)
  * Reliability ↑ (reduced retries, fewer sync failures)

**Hard Probes**

* “What invariants must always hold during state transfer?”
* “What race condition did you explicitly design against?”
* “How did you test correctness under partial failures?”

**Assessment**

| Signal          | Hire                              | No-Hire                  |
| --------------- | --------------------------------- | ------------------------ |
| System thinking | Defines invariants, failure modes | Talks only about modules |
| Data            | Gives metrics                     | Vague “improved a lot”   |
| Ownership       | Designed protocol                 | Just implemented tickets |

---

### Project 2: BFT REST Client (Intel / VMware Blockchain)

**Question 3: BFT Client Design**

> “Design your BFT REST client on the whiteboard. Where can safety or liveness be violated?”

**Expected Topics**

* Quorum, leader vs follower reads
* Read redirection to primary
* Idempotency, retries, timeouts
* Client-side vs server-side fault handling

**Probes**

* “How do you prevent stale reads?”
* “How do you detect Byzantine behavior at the client?”
* “What happens if 1/3 nodes are slow but correct?”

**Assessment**

* ✅ Strong: reasons in terms of **safety, liveness, quorum math**
* ❌ Weak: treats it as a normal REST service

---

## 20–35 min — Tough Systems & Domain Design

### Question 4: Design — Replicated Log with Checkpointing

Inspired by VMware + RocksDB checkpointing. 

> “Design a replicated log with periodic checkpointing for fast node recovery.
> How do you guarantee consistency during checkpoint + live writes?”

**Look For**

* Log truncation after snapshot
* Copy-on-write or double buffering
* Coordination with consensus layer
* Catch-up protocol

**Probes**

* “What if a node crashes mid-checkpoint?”
* “How do you detect divergent state after recovery?”
* “What’s the time complexity of recovery?”

**Assessment**

| Dimension   | Hire Bar                      |
| ----------- | ----------------------------- |
| Correctness | Explicit ordering & atomicity |
| Recovery    | Clear fast-path & slow-path   |
| Trade-offs  | Space vs recovery time        |

---

### Question 5: Storage Efficiency – NetApp Compression

From WAFL compression & BRE workflows. 

> “In container compression with replication, where do you place decompression, and why?”

**Expected Discussion**

* Source vs destination side
* Network bandwidth vs CPU trade-off
* Checksum placement
* Impact on deduplication

**Probes**

* “What corruption scenario is hardest to detect?”
* “How do you make this idempotent across retries?”

**Assessment**

* ✅ Thinks in **data integrity + performance + failure**
* ❌ Only performance-centric

---

## 35–50 min — Failures, Debugging, Execution Judgment

### Question 6: Production Failure Deep Dive

> “Tell me about the worst production issue you personally owned in a distributed system. Walk through detection → isolation → fix → prevention.”

**Strong STAR**

* **S**: e.g., state transfer stuck, checkpoint corruption
* **T**: restore service under SLA
* **A**:

  * Metrics used
  * Hypothesis testing
  * Rollback strategy
* **R**:

  * MTTR reduced
  * Regression test added
  * New invariant enforced

**Probes**

* “What wrong assumption caused this?”
* “What signal did you miss initially?”
* “What permanent guardrail did you add?”

**Assessment**

| Signal      | Hire                  | No-Hire                |
| ----------- | --------------------- | ---------------------- |
| Debug skill | Structured hypothesis | Random trial-and-error |
| Ownership   | Owns root cause       | Blames infra/others    |
| Learning    | Clear prevention      | No systemic fix        |

---

### Question 7: Performance Optimization

> “Pick one optimization you did that improved throughput. Show me the before/after pipeline.”

**Expect**

* Profiling method
* Critical path reduction
* Batching, async, zero-copy, lock removal
* Measured improvement

**Probe**

* “What optimization did you *not* do because it hurt correctness?”

---

## 50–60 min — Leadership & Hire Decision Signals

### Question 8: Seniority & Leverage

> “If I put you as tech lead of a 6-engineer distributed systems team tomorrow, what would you change in the first 90 days?”

**Look For**

* Architecture review
* Reliability roadmap
* Testing strategy
* Hiring & mentoring

---

### Question 9: Bar Raiser Question

> “What is the hardest distributed systems problem you think most engineers misunderstand?”

**Assessment**

* Depth of conceptual clarity
* Ability to generalize beyond resume

---

## Final Assessment Rubric (Use This to Decide)

Score each on 1–5.

| Dimension               | What Hire Looks Like                        |
| ----------------------- | ------------------------------------------- |
| **System Design**       | Defines invariants, failure modes, recovery |
| **Distributed Systems** | Safety, liveness, quorum, ordering          |
| **Execution**           | Data-driven, metrics, reproducible fixes    |
| **Ownership**           | Designed, not just implemented              |
| **Judgment**            | Knows when *not* to optimize                |
| **Seniority**           | Talks about systems, not tickets            |

### Hire Recommendation Guidelines

* **Strong Hire**

  * Independently designed protocols
  * Speaks in invariants, metrics, and trade-offs
  * Owns failures end-to-end

* **Borderline**

  * Good implementation, weaker architecture ownership

* **No-Hire**

  * Task-level answers
  * No metrics
  * No deep failure stories

---

If you want, next I can provide:

* A **one-page interviewer scorecard template**
* A **30-minute decision-round script** tailored for Senior MTS
* A **debrief rubric** to align multiple interviewers to a hire/no-hire decision.
