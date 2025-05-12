Here is a 60-minute interview role-play plan tailored to Hemant Mungad, focusing solely on System Design and Behavioral skills based on his resume.

🎯 Interview Focus
Evaluate Hemant's system design skills in the context of scalable backend systems and his behavioral traits related to ownership, collaboration, and problem-solving.

⏳ 60-Minute Interview Structure (System Design + Behavioral)
Time	Section	Focus	Sample Prompts
0–5 min	Introduction	Set agenda, ease candidate	“Hi Hemant, today we’ll focus on system design and your experiences around collaboration, scaling challenges, and ownership.”
5–30 min	System Design	Backend architecture, scalability, resiliency, Kubernetes	Prompt: “Design an object storage system like AWS S3 that supports bucket-level encryption, versioning, and legal holds, and can scale to petabytes of data across regions.”
30–55 min	Behavioral Deep Dive	Ownership, team handling, incidents	Prompts:
1. “Tell me about a time you improved reliability in a production system.”
2. “When did you have to push back on a decision or redesign something under pressure?”
3. “How do you manage tradeoffs between performance, cost, and complexity?”
55–60 min	Wrap-Up	Questions from candidate	“Do you have any questions for me about the team or role?”

🔧 Sample Role-Play — System Design
Interviewer:
"You’ve worked on object storage systems with encryption and autoscaling. Design an S3-like system with support for object tagging, retention policies, legal holds, and encryption. The system should be available across multiple availability zones."

What to Probe:

Storage layout (object metadata, blocks, buckets)

Encryption model (per-object vs. bucket-level)

Multi-region replication

Versioning and retention enforcement

APIs and lifecycle management

Use of Kubernetes for scaling or HA

Tradeoffs in availability, cost, and durability

Follow-ups:

“How would you ensure encryption keys are securely managed?”

“How would HPA help scale your services under 1000+ concurrent PUT/GET operations?”

🧠 Sample Role-Play — Behavioral
Q1: Improving Production Reliability

Interviewer:
"Tell me about a time you implemented something that directly improved system reliability or uptime."
→ Expect examples like MDCAP scaling or object service uptime.

Q2: Navigating Tradeoffs

Interviewer:
"Give an example where you had to choose between performance and maintainability. What did you decide and why?"

→ Look for cases like Rust-based refactoring or encryption performance.

Q3: Cross-Team Communication or Pushback

Interviewer:
"Have you ever disagreed with a technical direction proposed by a senior or team? What did you do?"

→ Explore assertiveness, rationale, and compromise.

✅ Evaluation Guide
Category	Strong Signal	Weak Signal
System Design	Modular, resilient, considers security and scale	Misses critical components, no thought for scaling/failures
Ownership	Clear impact and accountability on outcomes	Vague answers, unclear role
Team Fit	Communicates well, adaptable, growth-minded	Rigid thinking, poor collaboration examples
Resilience & Initiative	Shows proactivity under stress or constraints
