Chandramouli, based on the attached resume of **Muppana Lalita Prasad (Senior MTS / Staff-level kernel & storage engineer)** , here is a **tight 30-minute decision-round interview plan** designed to drive toward a clear **Hire / No-Hire** outcome.

This is optimized for a **Senior MTS / Staff IC** bar: depth, ownership, design judgment, and production impact.

---

## Overall Structure (30 Minutes)

| Time      | Segment                        | Goal                               |
| --------- | ------------------------------ | ---------------------------------- |
| 0–3 min   | Context Setting                | Set expectations, scope            |
| 3–12 min  | Project Deep Dive (STAR)       | Validate real impact & ownership   |
| 12–20 min | System Design & Kernel Domain  | Test architecture & judgment       |
| 20–26 min | Failure, Debugging, Resilience | Test production maturity           |
| 26–30 min | Signal Consolidation           | Probe gaps, calibrate hire/no-hire |

---

## 1. Project Deep Dive (3–12 min)

### Q1. End-to-End Integrity in Storage Spaces Direct (Linux)

**Question**

> Walk me through the end-to-end integrity feature you implemented in Storage Spaces Direct on Linux.
> Focus on the problem, design choices, and measurable outcomes.

**Strong STAR Answer Signals**

* **Situation**: Multi-node replication with corruption risk across SPDK/BlobFS/Minstore.
* **Task**: Ensure consistency across active-passive K8 cluster.
* **Action**:

  * Added checksums / versioning at write path.
  * Validated before ack and during replication.
  * Integrated with SPDK user-space I/O.
* **Result (Data-driven)**:

  * Reduced silent corruption incidents to near-zero.
  * Improved recovery success rate (e.g., from X% to Y%).
  * Passed fault-injection scenarios.

**Probing**

* Where exactly in the I/O path did you place integrity checks?
* How did you balance latency vs safety?
* What metrics proved this was working?

**Assessment**

| Signal    | What to Look For                             |
| --------- | -------------------------------------------- |
| Ownership | Uses “I designed”, not “we”                  |
| Depth     | Mentions block layer, replication boundaries |
| Data      | Mentions error rates, perf impact            |

---

### Q2. ASR Kernel Module – Open Sourcing & Day-0 Kernel Support

**Question**

> You open-sourced the ASRDFD kernel module for day-0 kernel support.
> What was the technical and organizational problem, and what changed after this?

**Strong STAR Answer**

* **Situation**: New kernels breaking DR support.
* **Action**:

  * Abstracted kernel dependencies.
  * Designed KABI-safe interfaces.
  * Automated CI across distros.
* **Result**:

  * Reduced kernel bring-up time from weeks to days.
  * Increased supported kernels per quarter.
  * Fewer customer escalations.

**Probing**

* How did you handle KABI breaks across vendors?
* What was rejected upstream and why?

**Assessment**

This distinguishes **Staff vs Senior**: upstream thinking, ecosystem impact.

---

## 2. System Design & Domain Questions (12–20 min)

These are **hard, kernel/storage-specific**.

---

### Q3. Design: Write Replication in Active-Passive K8 Storage

**Question**

> Design a write replication pipeline for an active-passive K8 storage system using SPDK in user space.
> Where do you enforce ordering, durability, and failure handling?

**Expected Depth**

* Path: User → SPDK → NVMe → Replication thread → Peer nodes
* Ordering:

  * Sequence numbers / barriers
* Durability:

  * Ack only after local + quorum persisted
* Failure:

  * Split-brain handling
  * Rebuild on rejoin

**Probing**

* What happens if active crashes after local write but before remote ack?
* Where would you add fencing?

**Assessment**

| Hire Signal                        | No-Hire Signal              |
| ---------------------------------- | --------------------------- |
| Talks about WAL, barriers, fencing | Only high-level replication |
| Mentions consistency models        | Avoids failure cases        |

---

### Q4. Chain BIO Handling in Linux

**Question**

> You mentioned solving chain BIO handling.
> Explain what chain BIOs are, why they are tricky, and how you fixed it.

**Strong Answer**

* Explains:

  * BIO chaining for large I/O.
  * Completion propagation.
  * Refcounting bugs.
* Fix:

  * Proper end_io handling.
  * Avoid double completion / memory leaks.

**Probing**

* How did you detect the bug?
* What kernel version behavior changed?

This tests **true kernel engineer depth**.

---

### Q5. Design: Root Filesystem Protection During Boot

**Question**

> You modified initrd / boot phase to capture root FS writes.
> Design this from scratch for Linux and AIX.

**Expected**

* Linux:

  * Driver in initrd
  * Hook before fsck + mount rw
* AIX:

  * Boot LV integration
  * Phase-1 vs Phase-3 loading

**Probing**

* How do you avoid deadlocks during early boot?
* How do you persist captured writes if panic occurs?

---

## 3. Failure, Debugging, Resilience (20–26 min)

### Q6. Debugging a Corruption Bug in Production

**Question**

> Tell me about the hardest corruption or data-loss bug you debugged in production.

**Strong STAR**

* **Situation**: Customer data mismatch / crash on recovery.
* **Action**:

  * Used crash dumps, GDB, tracepoints.
  * Reproduced via fault injection.
* **Result**:

  * Fixed root cause.
  * Added regression tests.
  * Prevented recurrence.

**Probing**

* What invariant was violated?
* What permanent guardrail did you add?

---

### Q7. Error Injection Strategy

**Question**

> You implemented error injection.
> What failure classes did you model, and which ones mattered most?

**Expected**

* I/O timeout, partial writes, reorder, bit flips, ENOSPC.
* Prioritizes:

  * Crash between journal commit & replication.
  * Split-brain scenarios.

**Assessment**

Looking for **resilience engineering mindset**.

---

## 4. Staff-Level Judgment & Leadership (26–30 min)

### Q8. Technical Leadership Decision

**Question**

> As tech lead in ASR/Oracle, describe a design decision where you overruled or changed the team’s approach.

**Strong Answer**

* Mentions trade-offs:

  * Performance vs safety
  * Short-term vs upstream correctness
* Result:

  * Reduced incidents
  * Simplified long-term maintenance

**Probing**

* Who disagreed and why?
* What would you do differently now?

---

## Final Hire / No-Hire Calibration Rubric

Use this in your notes.

### Must-Have Hire Signals

| Area      | Strong Hire                                    |
| --------- | ---------------------------------------------- |
| Depth     | Can reason at block layer, BIO, boot, MD, SPDK |
| Ownership | Designed, not just implemented                 |
| Data      | Mentions metrics, rates, regressions           |
| Design    | Anticipates failures, not just happy path      |
| Judgment  | Balances correctness vs performance            |

### No-Hire Red Flags

* Talks only at feature level, not I/O path level.
* Cannot explain failure modes.
* No upstream / ecosystem thinking despite seniority.
* Avoids concrete metrics.

---

## Decision Question (Final 2 minutes)

This is your **tie-breaker**.

> If I give you ownership of the Linux write interception layer for our next DR product,
> what are the **first 3 design risks** you would mitigate in the first 90 days?

**Hire Answer**

* Mentions:

  1. Ordering & crash consistency
  2. Kernel compatibility / KABI
  3. Observability & fault injection

---

If you want, next I can:

* Convert this into a **printable interview scorecard**, or
* Create a **Hire/No-Hire decision template** with weighted scoring for Senior MTS.
