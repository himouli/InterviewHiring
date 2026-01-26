Below is a **15-minute, high-intensity deep-dive storage interview script** specifically designed for a **Senior MTS / Staff-level storage & distributed systems candidate** with **NetApp / WAFL experience**.

This script is meant to:

* Rapidly surface **true storage system design depth**
* Expose understanding of **correctness, crash consistency, replication, and recovery**
* Produce a **clear Hire / No-Hire signal in 15 minutes**

You can run this verbatim.

---

## 0–2 min — Calibration & Ownership Check

**Question 1: Scope & Ownership**

> “In your NetApp role, which exact part of the write path or replication pipeline did you personally design end-to-end?”

**What You Want to Hear**

* Names a concrete pipeline: e.g.,
  *“Compressed extent transfer in BRE destination path”*
* Mentions **design decisions**, not just tickets.

**Red Flags**

* Vague: “Worked on compression features”
* No clear ownership boundary.

---

## 2–6 min — Core Write Path Correctness (Hard)

**Question 2: Write Path Invariants**

> “Walk me through the write path for a compressed, replicated block in WAFL.
> At which exact points can correctness be violated?”

**Expected Structure**

1. Client write
2. Log / journal
3. Compression
4. Checksum
5. Replication
6. Metadata commit

**Must Hear**

* Atomic commit point
* Ordering between data & metadata
* Crash windows

**Probe Hard**

* “What if crash happens *after* data write but *before* metadata update?”
* “What invariant defines a committed write?”

**Hire Signal**

* Talks in **invariants, commit points, crash windows**

---

## 6–9 min — Crash Consistency & Recovery

**Question 3: Mid-Transfer Crash**

> “A node crashes halfway through transferring a compressed extent.
> On restart, how does the system decide whether to resume, rollback, or replay?”

**Strong Answer Covers**

* Persisted transfer state
* Idempotent apply
* Checksum validation
* Replay vs restart logic

**Probe**

* “What state must *always* be durable before starting transfer?”
* “How do you avoid double-applying data?”

**Red Flag**

* “System retries” without state machine reasoning.

---

## 9–12 min — Replication & Divergence

**Question 4: Divergence Detection**

> “How do you detect and repair silent divergence between source and destination volumes?”

**Expect**

* Checksums per extent
* Version vectors / epochs
* Periodic scrub
* Reconciliation algorithm

**Probe**

* “Which corruption is hardest to detect?”
* “How do you distinguish old data vs corrupt data?”

**Hire Signal**

* Thinks in **end-to-end integrity model**

---

## 12–14 min — Performance vs Correctness Trade-off

**Question 5: Optimization Judgment**

> “Tell me one optimization you deliberately did *not* ship because it risked correctness.”

**Strong Answer**

* Names a concrete optimization
* Explains risk (reordering, batching, async)
* Explains why correctness won

**Red Flag**

* “We optimized everything”
* No example of restraint.

---

## 14–15 min — Bar Raiser Question

**Final Question**

> “What is the single most subtle corruption bug you think a storage system can have?”

**Strong Answers Often Mention**

* Metadata/data mismatch
* Lost update under crash
* Reordered commit
* Checksum validated wrong data

**Assessment**

* Depth of paranoia = seniority signal.

---

## 15-Minute Decision Rubric

Use this immediately after the interview.

Score each 1–5.

| Dimension   | Hire Bar                           |
| ----------- | ---------------------------------- |
| Ownership   | Designed write/replication path    |
| Correctness | Defines invariants & commit points |
| Recovery    | Step-by-step crash recovery        |
| Integrity   | End-to-end corruption model        |
| Judgment    | Knows when not to optimize         |

### Decision Guide

* **Strong Hire**

  * Names invariants
  * Enumerates crash windows
  * Clear recovery state machine

* **Borderline**

  * Good concepts, weak recovery details

* **No-Hire**

  * Feature-level only
  * No crash consistency reasoning

---

If you want, I can next give you:

* A **one-page interviewer cheat sheet**
* A **10-minute whiteboard storage design problem**
* Or a **debrief template** to align interviewers to hire/no-hire quickly.
