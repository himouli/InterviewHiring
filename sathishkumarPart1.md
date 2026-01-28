Below is a **30-minute, high-signal interview plan** tailored specifically to the attached resume of the **Senior MTS / Principal-level storage engineer**. It is **outcome-focused, data-driven**, uses **STAR framing**, and includes **assessment signals + probing** to drive a **clear Hire / No-Hire decision**.

> Candidate context is drawn directly from the resume (HPE X10K Object Storage, replication, event logs, RAG pipelines, WAFL, snapshots, DR, scale-out FS) 

---

# ⏱️ 30-Minute Senior MTS Interview Plan (Decision Round)

---

## 0–3 min | Context Setting & Depth Calibration

**Goal:** Establish scope, scale, and seniority quickly.

### Question

> “Pick **one project** you personally owned end-to-end that best represents your technical depth and leadership. What was the **problem size**, **scale**, and **business impact**?”

### Strong Answer Should Include (STAR)

* **Situation:** Customer pain (RPO/RTO, scale limits, latency, operability)
* **Task:** Clear ownership (architect, driver, decision-maker)
* **Action:** Architectural tradeoffs, rejected options
* **Result (metrics):**

  * Scale (nodes, objects, TB/PB)
  * Latency/throughput gains
  * RPO/RTO improvement
  * Customer adoption / GA success

### Probe (if vague)

* “What metric convinced leadership this design was correct?”
* “What would have failed if your design assumptions were wrong?”

### Assessment Signal

* **Hire:** Talks in numbers, tradeoffs, owns outcomes
* **No-Hire:** Describes team effort, no metrics, no clear ownership

---

## 3–10 min | Deep Dive: Distributed Replication & DR (Resume-Aligned)

### Core Question

> “Walk me through the **event-log-based replication system** you designed for X10K Object Storage. How did you ensure **ordering, consistency, and failure recovery** across geo-distributed sites?”

### Expected STAR Answer

**Situation**

* Enterprise backup / DR across geo sites

**Task**

* Build reliable async replication with heterogeneous destinations

**Action**

* Event log design (append-only, ordered)
* Checkpointing & replay
* Idempotency guarantees
* Failure scenarios:

  * Network partitions
  * Partial replication
  * Duplicate events

**Result (Metrics)**

* RPO achieved (seconds/minutes)
* Recovery success rate
* Throughput under load
* Production incidents avoided/reduced

### Tough Probes

* “How did you handle **log divergence** or **replay storms**?”
* “What happens if the destination applies events out of order?”
* “How did you cap replication lag under sustained write bursts?”

### Assessment Signal

* **Hire:** Understands distributed failure modes deeply
* **No-Hire:** High-level replication talk, no concrete mechanisms

---

## 10–16 min | System Design: Storage Metadata & Scale

### Design Question

> “You designed a **Root Bucket Database (RBDB)** for bucket metadata. How would you design metadata to scale to **billions of objects** with **low-latency access**?”

### What a Strong Answer Covers

* Metadata sharding strategy
* Hot-spot avoidance
* Caching layers (read-through / write-back)
* Consistency vs availability tradeoffs
* Schema evolution strategy

### Mandatory Probes

* “What breaks first at 10× scale?”
* “How do you handle **bucket rename or delete** at scale?”
* “How do you recover metadata after partial corruption?”

### Assessment Signal

* **Hire:** Thinks in failure domains + operational reality
* **No-Hire:** Purely theoretical or DB-centric answer

---

## 16–21 min | Domain Depth: File / Object / Block Tradeoffs

### Question

> “You’ve worked across **WAFL, scale-out file systems, and object storage**. When would you **not** use object storage even if scale is required?”

### Expected Answer

* Metadata-heavy workloads
* Low-latency POSIX semantics
* Small-file performance
* Transactional consistency needs

### Probe

* “How would you adapt object storage to support small-file workloads?”
* “What WAFL concepts don’t translate well to object storage?”

### Assessment Signal

* **Hire:** Nuanced understanding, not dogmatic
* **No-Hire:** Overgeneralizes storage models

---

## 21–25 min | Modern Systems: RAG, Event Streams & AI Pipelines

### Question

> “You integrated real-time ingestion for **RAG/LLM pipelines** using event logs and Milvus. What were the **hard systems problems**, not the ML part?”

### Strong Answer Includes

* Event freshness guarantees
* Back-pressure handling
* Vector consistency vs data consistency
* Storage growth management
* Failure isolation between AI pipeline and core storage

### Probe

* “How do you prevent AI ingestion from impacting storage SLOs?”
* “What happens during re-embedding or model upgrades?”

### Assessment Signal

* **Hire:** Systems thinker, not hype-driven
* **No-Hire:** Talks mostly about ML buzzwords

---

## 25–28 min | Production Excellence & Escalations

### Question

> “Describe the **worst production incident** you owned. What data did you use to debug it, and what permanent fix did you drive?”

### Expected STAR

* Clear incident timeline
* Signal vs noise debugging
* Root cause isolation
* Preventive fix (not workaround)
* Post-mortem learning

### Probe

* “What metric would have caught this earlier?”
* “What design debt did this expose?”

### Assessment Signal

* **Hire:** Owns failures, fixes systems
* **No-Hire:** Blames infra or customers

---

## 28–30 min | Hire / No-Hire Calibration Question

### Final Question

> “If you joined my team, what is the **first subsystem you would redesign**, and what data tells you it’s the right target?”

### Evaluation Rubric

| Dimension | Hire Signal        | No-Hire Signal       |
| --------- | ------------------ | -------------------- |
| Ownership | End-to-end         | Scoped to tasks      |
| Depth     | Failure-aware      | Happy-path only      |
| Data      | Metrics driven     | Opinion driven       |
| Design    | Tradeoffs explicit | One-solution mindset |
| Seniority | Raises bar         | Matches team         |

---

# 🎯 Final Hiring Guidance

**Strong Hire If:**

* Demonstrates *systems thinking + operational realism*
* Talks in metrics (RPO, scale, latency)
* Anticipates failure before being prompted
* Connects design decisions to business outcomes

**No-Hire If:**

* Over-indexes on architecture diagrams
* Avoids failure discussions
* Cannot articulate “why this design, not others”

---

If you want, I can:

* Convert this into a **scorecard** (yes/no signals per question)
* Create a **follow-up 60-min loop** for Staff/Architect bar
* Add **red-flag answers** per question for fast calibration
