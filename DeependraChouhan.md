Below is a 60-minute interview role-play tailored to Deependra Singh Chouhan’s resume 
. It’s broken into segments to thoroughly probe technical depth, system design, and behavioral fit, so you can confidently decide Hire / No Hire.

⏳ 60-Minute Interview Structure
Time	Section	Focus	Sample Prompts
0–5 min	Intro & Framing	Build rapport, set expectations	“Hi Deependra, today we’ll cover a deep technical dive, a system-design exercise, and some behavioral questions. Ready?”
5–25 min	Technical Deep Dive	Dive into one of his Dremio or VMware features	“Walk me through your Apache Arrow solution for complex runtime table fields—how did you design, implement, and test it?”
Probes: memory/layout, vector choices, performance trade-offs, testing strategy
25–40 min	System Design	High-level architecture & trade-offs	“Design a generic Job-History Retention Service that keeps 7 days of data in KV-store and purges older records without spikes.”
Probes: scheduling/staggering, back-pressure, monitoring, failure recovery, multi-tenant isolation
40–55 min	Behavioral & Leadership	Ownership, Deliver Results, Collaboration	“Tell me about a time you drove a cross-team change—how did you align stakeholders, break down work, and measure impact?”
Probes: STAR specifics, metrics, roadblocks, learnings
55–60 min	Wrap-Up & Candidate Q&A	Final impressions, answer candidate’s questions	“What questions do you have? Based on our discussion, what role do you see yourself playing here?”

🔍 Detailed Role-Play Flow
5–25 min: Technical Deep Dive
Project Selection:

Choose “Intermediate profile updates to KV-store” (heap → disk).

Walkthrough:

Architecture: How the disk-backed store integrates with the coordinator.

Implementation: Data structures, I/O patterns, thread safety.

Performance: Heap reduction by 40%, benchmarking approach.

Deep Probes:

“What crash scenarios did you simulate?”

“How did you ensure latency stayed within SLA?”

“How did you roll this out—feature flags, canaries?”

25–40 min: System Design
Prompt:

“Design a Job-History Retention Service for Dremio Cloud:

Stores query-job records for 7 days in MongoDB

Auto-purges older data without creating KV-store spikes or downtime

Supports thousands of tenants with isolated schedules”

Candidate Should Cover:

Scheduler design: Staggered cron vs. event-driven triggers

Back-pressure: Rate-limit deletes, batching strategies

Monitoring & Alerts: Slow-query retention lag, error rates

Multi-tenant isolation: Namespace sharding, per-tenant schedules

Failure recovery: Idempotent cleanup jobs, dead-letter queues

Follow-Ups:

“How would you autoscale the cleanup service under variable load?”

“What SLIs/metrics would you track to ensure 7-day retention?”

40–55 min: Behavioral & Leadership
Key Principles: Deliver Results, Customer Obsession, Dive Deep, Learn & Be Curious.

Ownership Story:

“Describe a time you owned a P1 incident (e.g., out-of-memory on Dremio pods). How did you drive resolution?”

Customer Focus:

“Tell me about when you implemented ‘Contains’ wildcard search for dashboards. How did you gather requirements and validate success?”

Learning & Simplification:

“You transitioned profile storage from heap to disk. What new skills or research did you undertake, and how did you simplify the solution over time?”

Probing for STAR:

Situation: What was at stake?

Task: What clear goal did you set?

Action: What steps, tools, or frameworks did you use?

Result: Quantify impact (e.g., memory down 40%, pods stable, customer uptick).

55–60 min: Wrap-Up
Interviewer: “Thank you, Deependra. Can you summarize your top two strengths and one area you’d like to improve?”

Candidate Questions: Assess passion, fit, and curiosity about your team’s challenges.

🗳️ Hire / No Hire Decision Guide
Dimension	Strong Signal	Weak Signal
Technical Mastery	Clear, in-depth explanations, benchmarks, and real-world roll-out details	Vague recollections, inability to discuss trade-offs or testing approach
Design Rigor	Thoughtful system decomposition, SLIs, failure modes, multi-tenant concerns	Overlooked edge cases, no monitoring strategy, naive assumptions about scale
Ownership & Impact	STAR examples with metrics, cross-team alignment, clear outcomes	Generic descriptions, no concrete metrics, low stakeholder engagement
Learning & Adaptability	References specific research, prototyping, iteration cycles, simplification over time	Claims “learned on the job” without details, no iterative improvements
Cultural Fit	Shows customer empathy, collaboration mindset, and curiosity about team’s context	Focuses solely on individual work, lacks curiosity about broader business or customer impact

Use this script and guide to run a consistent, structured 60-minute interview that drives to a clear hiring decision.


Sources
