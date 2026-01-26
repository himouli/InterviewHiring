Below are **model, medium-level answers** to each of the 12 questions I gave you — written at the level you should expect from a **good-fit Data Path / Filesystem engineer** (not a bar-raiser, but clearly relevant and productive).

You can use these as:

* Benchmark answers
* Calibration for interviewer expectations
* A scoring reference during debrief

---

## 1. Write Path of a Block in a Journaling Filesystem

**Expected Answer**

A typical flow is:

1. Application issues write
2. Data goes into page cache / buffer cache
3. Metadata updates are written to the journal (log) first
4. Data blocks are written to disk
5. Metadata is updated on disk
6. Journal transaction is committed

The commit point is when the journal entry is safely on disk.

**Good Follow-up Answer**

* We journal metadata to reduce overhead; data journaling is optional.
* `fsync` forces data and metadata ordering before returning.

---

## 2. Crash Consistency Basics

**Expected Answer**

Possible states:

* Transaction not committed → ignored during recovery
* Transaction committed → replayed from journal
* Orphaned blocks cleaned by fsck or background cleaner

Recovery:

* Scan journal
* Replay committed transactions
* Roll back incomplete ones

If metadata is committed but data is not, filesystem may expose stale data unless ordered or data journaling is used.

---

## 3. Compression in the Data Path

**Expected Answer**

Compression is usually placed:

* After buffering
* Before writing to disk

Trade-offs:

* Saves IO bandwidth and disk space
* Costs CPU
* May increase write latency

Compression must happen before checksumming so checksum matches compressed data.

---

## 4. Checksums and Data Integrity

**Expected Answer**

* Each block has a checksum stored in metadata
* On read, recompute checksum and compare
* Detect disk, memory, or network corruption

Checksums cannot detect:

* Logical bugs writing wrong data consistently
* Application-level semantic corruption

---

## 5. Replication Ordering

**Expected Answer**

Ordering is important because:

* Metadata must not be applied before data
* Newer versions must not be overwritten by older ones

Preserved by:

* Sequence numbers / transaction IDs
* Apply in commit order
* Idempotent replays

If applied out of order, filesystem may lose updates or corrupt metadata.

---

## 6. Buffer Cache & Performance

**Expected Answer**

Buffer cache:

* Absorbs small writes
* Coalesces IO
* Reduces disk seeks
* Serves repeated reads from memory

Under memory pressure:

* Pages are evicted
* Write-back is triggered
* Performance may degrade due to synchronous IO

---

## 7. Partial Writes & Atomicity

**Expected Answer**

Prevented by:

* Write-ahead logging
* Copy-on-write
* Atomic metadata updates

For torn writes on power failure:

* Use sector atomicity
* Journaling
* Checksums to detect torn blocks

---

## 8. Read Path Optimization

**Expected Answer**

Common optimizations:

* Read-ahead
* Prefetching sequential blocks
* Caching hot data
* Async IO

Avoid cache pollution by:

* Adaptive read-ahead
* Bypassing cache for streaming workloads

---

## 9. Block Relocation / Rebalancing

**Expected Answer**

Used for:

* Defragmentation
* Load balancing
* Wear leveling

Risks:

* Metadata inconsistency
* Data loss if crash mid-move

Invariant:

* Either old location or new location must always be valid
* Never expose half-moved data

---

## 10. Debugging a Slow Write Path

**Expected Answer**

Steps:

1. Measure end-to-end latency
2. Check disk IO wait vs CPU usage
3. Look for lock contention
4. Profile hot functions
5. Check queue depths

Distinguish:

* IO-bound → high IO wait, low CPU
* CPU-bound → high CPU, low IO wait

---

## 11. Concurrency in the Data Path

**Expected Answer**

Common issues:

* Lock contention on inode / extent maps
* Deadlocks between metadata locks
* Races in allocation

Fine-grained locks used in:

* Per-inode or per-extent structures

Coarse-grained locks used for:

* Global metadata or rare operations

---

## 12. Hardest Part of the Filesystem Data Path

**Expected Answer**

Typical good answers:

* Crash consistency
* Metadata correctness
* Recovery logic
* Ensuring invariants under failure

Reason:

* Bugs here cause silent corruption and are hard to detect.

---

## How to Use This in Interviewing

Use this as your **fit benchmark**:

| Level          | What You’ll Hear                                     |
| -------------- | ---------------------------------------------------- |
| **Good Fit**   | Clear pipelines, journaling, crash recovery, caching |
| **Borderline** | High-level concepts, weak recovery details           |
| **Not Fit**    | Only cloud abstractions, no filesystem reasoning     |

---

If you want, next I can give you:

* A **scoring sheet with expected answers per question**
* A **sample debrief write-up** for this candidate
* Or a **follow-up advanced round** for strong filesystem candidates.
