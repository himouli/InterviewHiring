Below is a 60-minute interview role‐play tailored to Dev Kant Chouhan’s background 
. You’ll get a time-boxed script, sample prompts (with interviewer “M” and candidate “C”), and an evaluation guide to land on Hire / No Hire.

⏳ 60-Minute Interview Agenda
Time	Section	Focus	Lead
0–5 min	Intro & Framing	Build rapport, set expectations	M: “Hi Dev, today we’ll deep-dive into your Go/K8s work, do a system design, then hit some behavioral questions. Ready?”
5–25 min	Technical Deep Dive	Go concurrency & K8s operator internals	M: “Walk me through your custom Kubernetes operator: its architecture, how you handled reconciliation loops and thread-safety.”
25–45 min	System Design	ConfigManagement Service	M: “Design a multi-tenant Configuration Management Service that persists settings in Postgres, supports dynamic updates without deploys, and isolates tenants.”
45–58 min	Behavioral & Leadership	Deliver Results, Dive Deep, Ownership	M: “Tell me about a time you owned a P1 production issue on your installer CLI—how did you troubleshoot and resolve it?”
58–60 min	Wrap-Up & Candidate Q&A	Clarify next steps	M: “Any questions for me? Thanks, Dev!”

🎤 Sample Role-Play Script
0–5 min: Intro & Framing
M:

“Dev, great to meet you. We’ll start with a technical deep dive into your Go/Kubernetes work, then a system-design exercise, and finish with behavioral questions around ownership and delivery. How does that sound?”

C:

“Sounds perfect—thanks for the overview!”

5–25 min: Technical Deep Dive (Go & K8s Operator)
M:

“You built custom operators to monitor cluster health. Can you walk me through its reconciliation loop from a high level?”

C:

Describes: operator scaffold → Informer cache → Reconcile() signature → handling Add/Update/Delete events.

M Probes:

Concurrency: “How do you ensure your controllers handle multiple parallel Reconcile calls safely?”

Rate-Limiting & Backoff: “What happens when the API server is overloaded? How do you throttle?”

State Storage: “Where do you store intermediate state—annotations, ConfigMaps, or external DB?”

Error Handling: “How do you detect and recover from a failed reconciliation (e.g., Pod crash during update)?”

(Look for: use of workqueues, mutexes or per-key locking, context deadlines, structured logging.)

25–45 min: System Design (Config Management Service)
M:

“Let’s design a Configuration Management Service for Pure Storage multi-tenant users. Requirements:

Store arbitrary JSON/YAML configs per tenant

Dynamic reload by downstream services without restart

Strict tenant isolation (no cross-leak)

Audit logs of changes

How would you architect it?”

C Walkthrough Should Cover:

API Layer (Go + Gin or gRPC): CRUD endpoints, auth via JWT with tenant claims.

Persistence:

Postgres with a configs table: (tenant_id, config_key, payload JSONB, version, updated_at)

Version history stored in an append-only audit table.

Change Propagation:

Event Bus (e.g., NATS or Kafka) to publish ConfigUpdated events per tenant.

Downstream services subscribe to only their tenant topic.

Dynamic Reload:

Services embed a client library that maintains a long-lived WebSocket or watches a Redis pub/sub channel for updates.

Isolation & Security:

Row-level security in Postgres (current_setting('tenant.id')).

mTLS between services for event bus.

Scaling & HA:

API behind Kubernetes Deployment + HPA.

Postgres in primary-replica mode, read-only replicas for audit queries.

M Deep Probes:

“How do you handle schema migrations of the JSON payload?”

“What happens if a config update fails to propagate to a subscriber?”

“How would you rollback a faulty config across thousands of services?”

45–58 min: Behavioral & Leadership
M:

“Tell me about a time you owned a P1 incident when your installer CLI failed in production.”

C (STAR) Should Include:

Situation: On-prem installs were failing due to a missing namespace label.

Task: You were on-call and needed to restore installs within 1 hour.

Action: Added schema validation in CLI, rolled out a hotfix under a feature flag, ran backfill job for stuck clusters.

Result: Restored 100% success rate within 45 min and added automated integration tests.

M Probes:

“How did you coordinate with support and SRE teams?”

“What metrics or dashboards did you use to detect ongoing failures?”

“What post-mortem actions did you take to prevent recurrence?”

58–60 min: Wrap-Up & Candidate Q&A
M:

“Thanks, Dev. Can you briefly summarize your top two strengths and one area you’d like to improve?”

C:

Provides concise self-reflection.

M:

“Great. Do you have any questions for me?”

🗳️ Decision Guide
Dimension	Strong Signal	Weak Signal
Technical Depth	Deep understanding of Go internals, operator patterns, race-free designs	Vague on concurrency, no locking/queueing details
Design Rigor	Clear multi-tier architecture, event-driven reload, failover/rollback strategies	Skips audit/versioning, naive polling for reload, no tenancy isolation
Ownership & Impact	STAR with metrics & clear impact, cross-team coordination, post-mortems	Generic stories, no measurable outcomes
Problem Solving	Probes failure modes, anticipates edge cases (network, schema drift, replay)	Misses error handling, no rollback or scaling concerns
Communication	Structures answers, asks clarifying questions, diagrams key components	Rambling, doesn’t seek clarity, unclear flow
