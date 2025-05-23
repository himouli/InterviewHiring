https://claude.ai/public/artifacts/723cdbd8-b719-46b2-a06e-31f0d3977244

# 60-Minute Hiring Manager Interview Schedule - Saurav Kumar

## Candidate Background Summary
- **Current Role**: MTS 3 at Nutanix (3+ years)
- **Total Experience**: 6+ years in distributed systems, backend services
- **Key Technologies**: Go, C++, Python, Kubernetes, Kafka, PostgreSQL
- **Notable Achievements**: Led full service development, 50% performance improvements, architectural redesigns

---

## Interview Structure (60 minutes)

### **Opening & Rapport Building** (5 minutes)
- Welcome and brief introductions
- Overview of interview structure
- Any questions about the role/company before we begin

---

### **Past Experience Deep Dive** (20 minutes)

#### **Primary Questions:**

**1. Intelligent Assist Service Leadership (8 minutes)**
> "You led the entire development of the Intelligent Assist service at Nutanix. Walk me through how you approached this from initial requirements to production deployment."

**Follow-up probes:**
- How did you scope requirements with PMs when technical and business needs conflicted?
- What architectural decisions did you make early on that proved most critical?
- How did you achieve the 50% response time improvement?

**2. Cross-Platform Migration Challenge (7 minutes)**
> "You've worked across multiple technology stacks - from Java at VMware to Go at Nutanix, and even ported Python processes to Go at nference with 13x performance gains. Tell me about the most challenging migration you led."

**Follow-up probes:**
- What factors drove the decision to rewrite vs refactor?
- How did you manage risk during the transition?
- What would you do differently knowing what you know now?

**3. Ownership in Crisis (5 minutes)**
> "Describe a time when a service you owned had a critical production issue. How did you handle it?"

---

### **System Design** (15 minutes)

**Core Challenge:**
> "Design a distributed notification system that can handle 100K notifications per second across email, SMS, and push notifications, with guaranteed delivery and deduplication."

**Evaluation Focus:**
- Initial approach and component identification
- Scalability considerations (given his Kafka/messaging experience)
- Trade-offs between consistency and availability
- How he handles failure scenarios
- Queue management and backpressure handling

**Follow-up based on his background:**
- "Given your experience with Kafka at Nutanix, how would you structure the message flow?"
- "How would you handle partial failures across different notification channels?"

---

### **Leadership Principles Assessment** (15 minutes)

#### **Ownership (4 minutes)**
> "You currently own multiple services at Nutanix. Tell me about a time when you had to take ownership of something outside your immediate area of responsibility to ensure project success."

**Look for:**
- Taking initiative beyond job description
- Long-term thinking vs quick fixes
- Accountability for outcomes

#### **Deep Dive (4 minutes)**
> "Describe your process for troubleshooting the startup time issue you solved at nference - going from 15 minutes to 2 minutes. How did you identify the root cause?"

**Look for:**
- Systematic investigation approach
- Data-driven decision making
- Persistence in finding root causes

#### **Setting High Standards (4 minutes)**
> "You mentioned pushing UT coverage to 90% and defining coding standards. How do you balance high standards with delivery timelines when the team is under pressure?"

**Look for:**
- Non-negotiable quality standards
- Influence without authority
- Process improvement mindset

#### **Learn and Be Curious (3 minutes)**
> "You've worked with emerging technologies like Kubernetes early on with Project Tanzu. How do you stay current with technology trends and decide what's worth investing time in?"

**Look for:**
- Continuous learning habits
- Technology evaluation criteria
- Knowledge sharing with team

---

### **Scenario-Based Decision Making** (3 minutes)

**Quick Scenario:**
> "Your team is split between two architectural approaches for a critical service. One is tried-and-tested but may not scale long-term, the other is innovative but carries more risk. You have 2 weeks to decide. How do you approach this?"

---

### **Closing & Questions** (2 minutes)
- Candidate questions about role/team/company
- Next steps in process
- Thank you and wrap-up

---

## Evaluation Criteria & Decision Framework

### **Hire Indicators:**

**Technical Excellence:**
- [ ] Demonstrates deep understanding of distributed systems
- [ ] Shows clear architectural thinking in system design
- [ ] Explains trade-offs effectively
- [ ] Learns from past technical decisions

**Leadership & Ownership:**
- [ ] Takes end-to-end responsibility for outcomes
- [ ] Shows initiative beyond assigned tasks
- [ ] Balances quality with delivery pragmatically
- [ ] Influences through technical expertise

**Problem-Solving:**
- [ ] Uses systematic approach to investigate issues
- [ ] Drives to root causes, not just symptoms
- [ ] Makes data-driven decisions
- [ ] Adapts approach based on constraints

**Growth Mindset:**
- [ ] Continuously learns new technologies
- [ ] Applies learnings to improve team/processes
- [ ] Shows intellectual curiosity
- [ ] Mentors others effectively

### **No-Hire Red Flags:**
- Cannot articulate technical decisions clearly
- Blames others for project failures
- Shows rigid thinking without considering alternatives
- Lacks curiosity about new approaches
- Cannot balance quality with pragmatic delivery
- Poor communication of complex technical concepts

### **Borderline Cases - Additional Probes:**
- "Tell me about a technical decision you made that you later regretted"
- "How do you handle disagreement with senior stakeholders on technical direction?"
- "Describe how you've grown technically in the past year"

---

## Post-Interview Assessment

**Overall Recommendation:** [ ] Strong Hire [ ] Hire [ ] No Hire [ ] Strong No Hire

**Key Strengths:**

**Areas of Concern:**

**Specific Examples Supporting Decision:**

**Recommended Follow-up:** (if borderline)
