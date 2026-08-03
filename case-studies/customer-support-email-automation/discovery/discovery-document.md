# Discovery Document — Customer Support Email Automation

| Property            | Value                                                                                                   |
| -------------------- | -------------------------------------------------------------------------------------------------------- |
| Case Study            | [Customer Support Email Automation](../README.md)                                                       |
| Work Order            | [WO-101 — Customer Support Discovery](../../../work-orders/delivery/WO-101-Customer-Support-Discovery.md) |
| Prepared By           | Senior Business Analyst                                                                                  |
| Reviewer              | Chief Methodology Officer                                                                                 |
| ACM Phase             | Assess                                                                                                    |
| Status                | Draft — Pending Client Review                                                                             |
| Version               | 1.0                                                                                                        |
| Date                  | 2026-08-03                                                                                                 |

---

## Table of Contents

- [1. Executive Summary](#1-executive-summary)
- [2. Business Problem Statement](#2-business-problem-statement)
- [3. Current-State Assessment](#3-current-state-assessment)
- [4. Stakeholder Analysis](#4-stakeholder-analysis)
- [5. Current Process Overview](#5-current-process-overview)
- [6. Pain Point Analysis](#6-pain-point-analysis)
- [7. Business Objectives](#7-business-objectives)
- [8. Success Metrics](#8-success-metrics)
- [9. AI Opportunity Assessment](#9-ai-opportunity-assessment)
- [10. Risks and Constraints](#10-risks-and-constraints)
- [11. Assumptions](#11-assumptions)
- [12. Executive Recommendations](#12-executive-recommendations)
- [13. Readiness for Next Phase](#13-readiness-for-next-phase)

---

## 1. Executive Summary

The client operates a growing SaaS business that receives approximately **8,000 customer support emails per day**. Every email is currently read, categorized, prioritized, routed, and drafted for response manually by support agents. This manual model has scaled with the business until now, but continued growth is exposing it to slower response times, rising operational cost, inconsistent prioritization, and limited management visibility into support performance.

Leadership has asked Eyuna to determine, through a structured discovery engagement, where AI can responsibly improve the efficiency and quality of the support operation without compromising data protection, compliance, or the human oversight required for sensitive customer communications.

This document presents the findings of that discovery effort: the business problem, the current-state operation as documented by the client, the stakeholders affected, the pain points driving cost and customer dissatisfaction, a prioritized set of AI opportunities, and the risks, assumptions, and constraints that must inform any future solution design.

**Headline finding:** the core issue is not a lack of AI technology — it is that high-volume, repetitive cognitive work (reading, classifying, prioritizing, and drafting) is being performed entirely by humans with no automated first pass. This creates a linear relationship between email volume and labor cost, and it caps how fast the team can respond regardless of how many agents are added.

**Recommendation:** proceed to the Create phase with a phased automation approach that keeps a human in the loop for sensitive and high-risk communications, targeting classification, prioritization, and routing first, followed by AI-assisted response drafting.

---

## 2. Business Problem Statement

> **The client's customer support operation cannot scale efficiently because every incoming email requires full manual handling, and support volume is growing faster than the team's capacity to process it at consistent speed and quality.**

This manifests as three linked business problems:

1. **Speed** — customers wait longer for a first response as volume increases, because triage capacity is fixed by headcount.
2. **Cost** — operational cost scales linearly with email volume, since there is no automated first pass to absorb repetitive work.
3. **Visibility** — management lacks reliable, real-time data on support trends, volumes, and performance, which limits its ability to plan staffing or identify systemic issues early.

Left unaddressed, these problems put customer satisfaction, retention, and support cost efficiency at risk as the business continues to grow.

---

## 3. Current-State Assessment

### 3.1 Basis for this assessment

The current-state information below is drawn from the documented business scenario in the [Customer Support Email Automation case study](../README.md). It has **not yet been validated through direct stakeholder interviews, process observation, or system data extracts**. It should be treated as the client's own characterization of the problem, not as independently verified fact. Validation is recommended before solution design begins (see [Section 13](#13-readiness-for-next-phase)).

### 3.2 Operating environment

| Dimension                 | Current State                                                                 |
| -------------------------- | ------------------------------------------------------------------------------- |
| Channel                    | Email only, for the process in scope of this engagement                        |
| Volume                     | Approximately 8,000 customer support emails per day                            |
| Triage method              | Fully manual — every email is read and categorized by a support agent          |
| Prioritization method      | Manual, agent judgment; no documented standard was provided                    |
| Routing method              | Manual, based on agent interpretation of the request                          |
| Response drafting          | Manual, written individually by the assigned agent                             |
| Escalation                | Manual identification and handoff by the handling agent                        |
| Reporting and analytics    | Limited; management lacks visibility into support trends and operational load |
| Supporting tooling         | Existing customer support platform(s) remain in place (not itemized by client) |

### 3.3 Observed effects of the current model

- Response times increase as volume grows, since triage throughput is bound by available agent hours.
- Prioritization is inconsistent because it depends on individual agent judgment rather than a shared standard.
- Support agents spend a significant share of their time on repetitive, low-complexity work (reading and categorizing) rather than resolving complex customer issues.
- Operational cost scales roughly linearly with volume, since headcount is the primary lever for capacity.
- Demand spikes are difficult to absorb without a proportional, and often temporary, increase in staffing.

---

## 4. Stakeholder Analysis

| Stakeholder Group                | Role in Current Process                                    | Interest in the Outcome                                                       | Discovery Status                  |
| ---------------------------------- | -------------------------------------------------------------- | --------------------------------------------------------------------------------- | ------------------------------------ |
| Support Agents                     | Read, categorize, prioritize, route, draft, and escalate emails | Reduced repetitive workload; concern about role change and tool trust           | Not yet interviewed — recommended    |
| Support Team Leads / Supervisors   | Manage queues, monitor agent performance, handle escalations   | Consistent prioritization; visibility into team workload and bottlenecks        | Not yet interviewed — recommended    |
| Customer Support Leadership        | Owns support KPIs and department budget                        | Faster response times, lower cost per ticket, improved CSAT, scalable operations | Primary sponsor of this engagement   |
| Customers                          | Submit support requests via email                              | Fast, accurate, relevant responses; trust that sensitive issues are handled well | Represented indirectly via CSAT data |
| Compliance / Data Protection       | Owns PII and regulatory obligations                             | Any automation must protect PII and preserve auditability                        | Not yet interviewed — recommended    |
| IT / Platform Owners                | Maintain existing support platform(s)                          | Minimal disruption; clean integration with current tooling                       | Not yet interviewed — recommended    |
| Executive Sponsor                  | Approves investment and strategic direction                    | Demonstrable ROI, responsible AI adoption, competitive customer experience        | Audience for this document           |

**Recommendation:** the stakeholder groups marked "not yet interviewed" should be engaged directly before solution design begins. Support agents in particular hold first-hand knowledge of edge cases, informal prioritization rules, and workflow exceptions that are not visible in summary-level business documentation, and their early involvement will also support change management and adoption.

---

## 5. Current Process Overview

The current support-email process, as documented, follows six manual steps for every inbound email:

1. **Receive** — the email arrives in the shared support inbox or platform.
2. **Read** — an agent opens and reads the email to understand the request.
3. **Categorize** — the agent determines the type of issue (e.g., billing, technical, account).
4. **Prioritize** — the agent judges urgency based on individual experience.
5. **Route** — the agent assigns or forwards the ticket to the appropriate team.
6. **Respond or Escalate** — the agent either drafts a reply directly or escalates complex/high-risk cases to a specialist or supervisor.

**Observation:** every step in this process is a candidate for AI-assisted acceleration, but the process as documented has no formal decision criteria (e.g., a defined priority matrix or routing rulebook) — prioritization and routing currently rely on tacit agent knowledge. This absence of documented business rules is itself a discovery finding, not just an implementation detail: it means future solution design will need explicit input from support leads to encode decision logic that today exists only in agents' heads.

---

## 6. Pain Point Analysis

| Pain Point                                   | Likely Root Cause                                                       | Business Impact                                                             |
| ----------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Slow first-response time                        | No automated triage; response speed is bound by manual reading and sorting  | Lower customer satisfaction; risk of churn; competitive disadvantage             |
| Inconsistent ticket prioritization              | No documented, standardized priority criteria; reliance on agent judgment    | Urgent or high-risk issues may be delayed; inconsistent customer experience        |
| High operational cost per ticket                | Fully manual handling of high-volume, repetitive work                       | Cost scales linearly with volume; limits margin as the business grows            |
| Repetitive, low-value agent workload            | No automation absorbs routine classification and drafting work              | Agent fatigue and attrition risk; less time for high-value customer interactions |
| Limited reporting and operational insight       | No systematic capture of categorization, volume, or performance data        | Leadership cannot proactively plan staffing or identify systemic issues          |
| Difficulty scaling during demand spikes         | Capacity is tied to headcount, which cannot flex quickly                    | Service degradation during peak periods; potential SLA breaches                   |

These pain points are presented as **client-reported issues** pending validation; see [Section 11 — Assumptions](#11-assumptions).

---

## 7. Business Objectives

The following objectives were validated against the business scenario and should be confirmed with executive sponsors before proceeding:

| # | Objective                                                       | Type        |
| - | ------------------------------------------------------------------ | ------------- |
| 1 | Reduce first-response time by at least 70%                          | Measurable   |
| 2 | Automatically classify incoming support emails                     | Measurable   |
| 3 | Detect urgent and high-risk customer requests                      | Measurable   |
| 4 | Route requests to the correct support team with improved accuracy  | Measurable   |
| 5 | Generate AI-assisted response drafts for agent review              | Measurable   |
| 6 | Maintain human approval for sensitive or high-risk responses       | Governance   |
| 7 | Improve Customer Satisfaction (CSAT)                                | Measurable   |
| 8 | Reduce operational cost per support ticket                          | Measurable   |
| 9 | Increase support agent productivity and time on high-value work     | Measurable   |

**Note:** Objective 1 ("reduce first-response time by at least 70%") is stated as a client target. It has not been independently validated against current baseline data and should be re-confirmed once baseline FRT is measured (see [Section 11](#11-assumptions)).

---

## 8. Success Metrics

| Metric                                | Definition                                                                 | Current Baseline           | Target                          |
| ---------------------------------------- | ------------------------------------------------------------------------------ | ----------------------------- | ---------------------------------- |
| First Response Time (FRT)                | Time from email receipt to first agent/AI response                            | Not yet measured — to confirm | ≥ 70% reduction from baseline      |
| Average Resolution Time (ART)            | Time from receipt to final resolution                                          | Not yet measured — to confirm | Reduction, target to be defined     |
| Customer Satisfaction (CSAT)             | Post-interaction customer satisfaction score                                   | Not yet measured — to confirm | Measurable improvement              |
| Percentage of Emails Automated           | Share of emails classified, routed, or drafted with AI assistance             | 0% (fully manual today)        | To be defined in solution design    |
| Agent Productivity                       | Tickets resolved, or high-value interactions handled, per agent per period    | Not yet measured — to confirm | Measurable improvement              |
| Routing Accuracy                         | Percentage of tickets routed correctly on first attempt                        | Not yet measured — to confirm | Improvement over manual baseline    |
| Escalation Accuracy                      | Percentage of high-risk/urgent cases correctly identified and escalated       | Not yet measured — to confirm | Improvement over manual baseline    |
| Cost per Support Ticket                   | Fully loaded operational cost divided by ticket volume                        | Not yet measured — to confirm | Measurable reduction                |

**Recommendation:** establish a measurement baseline for each metric above before solution design begins. Targets expressed only as "improvement" cannot be validated as successful without a documented starting point.

---

## 9. AI Opportunity Assessment

The following opportunities are assessed for business value and priority. This assessment is **capability-level and technology-neutral**; it intentionally does not recommend specific tools, models, or architectures, which are out of scope for this Work Order.

| AI Opportunity                          | Business Value                                                          | Priority   | Human Oversight Required                          |
| ------------------------------------------ | ----------------------------------------------------------------------------- | ------------ | ----------------------------------------------------- |
| Email classification                       | Removes the slowest manual step; foundation for all downstream automation      | High         | Spot-check / quality sampling                          |
| Priority / urgency detection                | Directly addresses inconsistent prioritization pain point                       | High         | Review for high-risk or ambiguous cases                |
| Intelligent routing                        | Reduces misrouted tickets and rework; speeds handoff to the right team          | High         | Spot-check / quality sampling                          |
| Escalation recommendation                  | Helps ensure urgent/high-risk cases reach a human specialist faster              | High         | Human decision required before escalation is finalized |
| AI-assisted response drafting              | Reduces agent drafting time; agent reviews and edits before sending             | Medium-High  | Mandatory human approval before send                    |
| Sentiment analysis                          | Supports prioritization and escalation; early signal of dissatisfaction         | Medium       | Feeds into human/AI prioritization, not a standalone action |
| Knowledge base retrieval (for drafting)    | Improves relevance/accuracy of drafted responses                                | Medium       | Reviewed as part of response approval                  |
| Duplicate ticket detection                  | Reduces redundant agent effort on repeat inquiries                              | Medium       | Low — informational, agent confirms                     |
| Operational analytics / reporting          | Gives leadership visibility into volume, trends, and performance                | Medium       | None — reporting only                                    |

**Sequencing guidance for solution design:** opportunities that reduce triage effort (classification, prioritization, routing) deliver the most direct impact on the client's stated objectives (FRT, cost per ticket, agent productivity) and carry lower governance risk than response generation, since they do not produce customer-facing content. Response drafting delivers high value but requires the strongest human-approval controls given its direct customer communication impact. A phased sequence — triage automation first, response assistance second — is a reasonable default for solution design to evaluate, but the definitive sequencing decision belongs to the Create phase.

---

## 10. Risks and Constraints

### 10.1 Risks

| Risk                                                     | Likelihood | Impact | Mitigation Direction                                                          |
| ------------------------------------------------------------ | ------------ | -------- | ---------------------------------------------------------------------------------- |
| Incomplete understanding of current processes                | Medium       | High     | Conduct direct stakeholder interviews and process observation before design         |
| Business assumptions not validated with stakeholders          | Medium       | High     | Validate all assumptions in [Section 11](#11-assumptions) prior to Create phase     |
| Stakeholder alignment issues (agents, leadership, compliance) | Medium       | Medium   | Engage all stakeholder groups identified in [Section 4](#4-stakeholder-analysis) early |
| Regulatory or compliance constraints not fully surfaced        | Medium       | High     | Involve Compliance / Data Protection stakeholders directly in validation           |
| Unrealistic automation expectations (e.g., full automation)   | Medium       | Medium   | Set expectations that human oversight remains mandatory for sensitive communications |
| Undocumented business rules (priority, routing) hard to encode | High         | Medium   | Capture tacit agent knowledge through structured interviews and workshops           |
| Baseline metrics unavailable, making success hard to measure   | High         | Medium   | Establish measurement baselines before solution design begins                       |

### 10.2 Constraints

The following constraints were provided by the client and must be respected in all future solution design work:

- Human approval is required for sensitive customer communications.
- Personally identifiable information (PII) must remain protected throughout any automated process.
- Existing customer support platforms remain in place; automation must work within that environment.
- Recommendations arising from this engagement should remain technology-neutral unless a specific technology choice is necessary.

---

## 11. Assumptions

The following assumptions were made during this discovery engagement and require validation before proceeding to solution design.

| # | Assumption                                                                                   | Why It Matters                                                                    |
| - | -------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| 1 | Current-state process information reflects actual day-to-day operations accurately                 | This discovery is based on a documented scenario, not direct interviews or observation  |
| 2 | The 8,000 emails/day figure is a representative average, not a peak or seasonal figure               | Peak-load behavior materially affects scalability and staffing recommendations            |
| 3 | No formal, documented prioritization or routing rules currently exist                                | If undocumented rules do exist, they must be captured before automation design            |
| 4 | Support agents have no prior automation tooling in this workflow today                               | Affects the scale of change management required and the realistic automation baseline    |
| 5 | The existing customer support platform(s) can support future integration                             | Affects feasibility of downstream solution design; platform details were not provided     |
| 6 | "Sensitive communications" requiring human approval will be defined jointly with Compliance later    | The scope of what counts as sensitive is not yet formally defined                          |
| 7 | Baseline values for FRT, ART, CSAT, and cost per ticket are not yet available internally             | Without a baseline, improvement targets cannot be objectively measured                     |

**These are assumptions, not verified facts.** They should be confirmed or corrected through direct stakeholder engagement before the Create phase begins.

---

## 12. Executive Recommendations

Based on the discovery findings above, the Senior Business Analyst recommends the following actions to the executive team:

1. **Validate current-state findings with direct stakeholder engagement.** Conduct structured interviews with support agents, team leads, compliance, and IT before solution design begins. This closes the gap between the documented business scenario and verified operational reality.
2. **Establish measurement baselines now.** Capture current FRT, ART, CSAT, routing accuracy, and cost per ticket before any automation is introduced, so that improvement can be objectively demonstrated later.
3. **Prioritize triage-stage automation (classification, prioritization, routing) ahead of response generation.** These opportunities directly address the highest-impact pain points, carry lower governance risk, and create the foundation that response-drafting automation will depend on.
4. **Preserve mandatory human approval for sensitive and high-risk communications.** This constraint should be treated as non-negotiable in solution design, both for compliance and for maintaining customer trust during the transition.
5. **Formally define "sensitive communication" with Compliance.** The current definition is directional, not operational; solution design cannot proceed safely without a clear, agreed scope.
6. **Document today's tacit prioritization and routing knowledge.** Much of the current process depends on individual agent judgment. Capturing this knowledge explicitly is a prerequisite for any automated decision logic.
7. **Proceed to the Create phase**, using this Discovery Document, its validated updates, and the AI Opportunity Assessment as the primary inputs to Business Requirements and Solution Architecture.

---

## 13. Readiness for Next Phase

| Readiness Criterion                                       | Status                                                        |
| ------------------------------------------------------------- | ------------------------------------------------------------------ |
| Business problem clearly documented                            | Complete                                                            |
| Current-state operations understood                            | Complete at a summary level; direct validation recommended         |
| Stakeholders identified                                        | Complete; direct interviews recommended before design               |
| Business objectives defined and measurable                     | Complete; targets require baseline confirmation                     |
| AI opportunities identified and prioritized                    | Complete                                                            |
| Risks and assumptions documented                                | Complete                                                            |
| Executive recommendations produced                             | Complete                                                            |

**Overall assessment:** this engagement has sufficient business clarity to proceed into the Create phase, provided the recommended stakeholder validation and baseline measurement activities in [Section 12](#12-executive-recommendations) are scheduled early in that phase. No architecture, technology selection, or implementation decisions have been made as part of this discovery, consistent with the scope of [WO-101](../../../work-orders/delivery/WO-101-Customer-Support-Discovery.md).

---

> The quality of every AI solution is determined by the quality of the discovery that precedes it.

This Discovery Document establishes the shared business understanding required to move the Customer Support Email Automation engagement into solution design.
