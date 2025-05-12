Here’s a focused 60-minute interview plan for only System Design and Behavioral evaluation of Sarthak Koherwal, along with a sample role-play for each section.

🎯 Interview Goal (Revised)
To evaluate system design ability and behavioral competencies of Sarthak Koherwal for a backend engineering role.

⏳ 60-Minute Interview Structure (System Design + Behavioral)
Time	Section	Focus	Sample Prompts
0–5 min	Intro & Context Setting	Set expectations	"Hi Sarthak, today we'll focus on system design and your past experiences collaborating and handling challenges. Ready?"
5–30 min	System Design	Scalability, abstraction, APIs, data modeling	Prompt: "Design a system for managing audit logs for a SaaS product with 1B+ events/month. Logs should be queryable by admin and support alerting for suspicious activity."
30–55 min	Behavioral Deep Dive	Teamwork, ownership, handling failures	Prompts:
1. "Tell me about a time you handled a high-priority incident or bug."
2. "Describe a time you disagreed with a teammate or PM on a design decision."
3. "When did you go beyond your role to help a project succeed?"
55–60 min	Wrap-Up	Candidate questions & final impression	"Any questions for me or about the team/company?"

🔧 Sample Role-Play — System Design
Interviewer:
"Imagine we’re building an audit logging system for enterprise software like Google Workspace. Every login, change, or admin action is logged. The system must support 1B+ entries/month, be searchable (by user, time range), and support alerts for unusual activity. How would you design it?"

What to Probe:

Storage: Would they use something like BigQuery, Elasticsearch, or columnar stores?

API: How would reads/writes scale? How would alerts be triggered?

Fault tolerance & partitioning

Schema/versioning of logs

Follow-up:

“How would you optimize for cost?”

“How would you handle GDPR/retention?”

“What would you do differently if latency was a critical factor?”

🧠 Sample Role-Play — Behavioral
Q1: High-priority Incident

Interviewer:
"Tell me about a time you were involved in resolving a production incident or a customer-facing bug. What was your role and how did you approach it?"

Look for:

Ownership mindset

Communication under pressure

Root cause analysis and preventive action

Q2: Conflict/Disagreement

Interviewer:
"Can you share a time you disagreed with a colleague over a technical solution? What happened and how was it resolved?"

Look for:

Ability to listen and persuade constructively

Willingness to compromise

Focus on outcomes over ego

Q3: Going Beyond Role

Interviewer:
"Was there a time you had to step outside your usual responsibilities to help a project succeed?"

Look for:

Initiative

Collaboration

Product thinking

🧾 Decision Guidelines
Category	Strong Signal	Weak Signal
System Design	Balances tradeoffs, uses scalable/realistic architecture, handles edge cases	Vague, no tradeoff analysis, overengineered or too simplistic
Ownership	Clear impact on real issues, proactive handling	Only played a support role or lacks clarity
Team Fit	Collaborative, open-minded, values feedback	Defensive, solo-oriented, dismissive
Growth Mindset	Reflects on mistakes, mentions learning	Blames others or avoids tough questions

