# Talking points · Agentic use cases 01 to 04

*For the presenter. One sentence per bullet, plain language, about five minutes per use case. The decks carry the detail; these are the words to say. Figures are only those from the stakeholder briefs.*

---

## Use Case 01 · Endpoint Elevated Approval

*What it is about: requests to allow an application to run on an ABB laptop, desktop or server, raised in ServiceNow, and the people who approve them.*

**The problem today**
- Every request to allow an application waits for a person to gather the evidence and decide.
- The answer depends on how well the business justification is written, not on the file's reputation, the device's state or the requester's history.
- Two similar requests can get two different answers, depending on who approves them.
- There is no single, consistent record of why an application was allowed, so we cannot compare, audit or learn from past decisions.
- Speed depends on who is available; outside office hours, work waits.

**What we propose**
- A small team of AI agents, each with one job, handles the routine part of the work and sorts every request into green, orange or red.
- One agent reads our policy and finds the rules that apply to the request.
- One agent gathers the evidence from systems we already have: the file's reputation from Google Threat Intelligence, the device's security score and open alerts from Defender, application and organisational details from SharePoint, and the requester's history from ServiceNow.
- The Company Portal, Intune's application catalogue, tells us whether the application is already packaged and who else uses it.
- One agent brings in our existing approval criteria and the record of past manual decisions, so the system starts from how we decide today.
- One agent weighs it all: green is approved automatically and the allow-list entry written; orange goes to a named reviewer with the evidence attached, under a review process we still have to define together; red is escalated to the relevant security team with the full context.
- Every outcome is written to a record and back to the ServiceNow ticket, with the evidence and the reasoning.
- We build on the proof of concept the team already has for checking file hashes rather than replacing it.

**The safeguards we are adding**
- Everyone and everything is identified: requesters, approvers and each AI agent has its own identity and only the permissions it needs.
- The business justification is free text written by the requester, so it is the one input someone could craft to steer the AI; it is treated as information, never as instructions, and every classification must point to the policy rule and the evidence it relied on.
- The agents can look up evidence but cannot change anything in those systems; the only change they make is the approved allow-list entry, with a scoped credential that is recorded and reversible.
- Personal and device details are masked before they reach any AI model or leave the decision process.
- Everything is logged in a way that cannot be altered and feeds our security monitoring, so there is evidence for audits and investigations.
- Our records and policies are classified and their access is reviewed continuously; the agents only see what the person asking is allowed to see.

**What the business gains**
- No application is approved on reputation alone: an unknown or flagged file never goes green.
- Red requests reach the security team with the evidence already gathered, so they start from facts rather than from a ticket.
- One standard applied to every request, with the rule cited; a change to the policy changes every decision from that moment.
- A defensible record for every decision, so audit questions are answered from the record rather than from mailboxes.
- Reviewers spend their time on the orange requests only.
- Faster turnaround around the clock without lowering the bar, measured against today's manual baseline.

**How we start, and what stays in your hands**
- We start in shadow mode: the agents run alongside the current process on past tickets and decide nothing live until the team is satisfied.
- Policy owners keep the policy; the thresholds between green, orange and red and the reviewer lists are set by the team.
- Any agent can be stopped instantly by disabling its identity.
- We claim no figures in advance; the before-and-after comes from the manual decision history in ServiceNow.

---

## Use Case 02 · Endpoint Security Compliance & Remediation

*What it is about: the team that keeps more than 140,000 laptops, desktops and servers compliant, and the leaders who need to know where we stand.*

**The problem today**
- Security and device data sit in separate consoles; no single view says which devices matter today.
- Four recurring reports take 16 to 20 hours of expert time every week, assembled by hand from exports.
- The reported compliance of about 97 percent is an estimate; it has not been independently checked.
- Around 5,000 to 6,000 devices may need attention at any time, and answering "which ones first?" takes one to two hours.
- Simple fixes on laptops wait in the same queue as server changes that rightly need change control.

**What we propose**
- One agent collects the data from Defender and Intune on a schedule and merges it into one current view of the estate; a third source can be added once it is confirmed.
- One agent analyses that view using the reconciliation rules and exception lists our experts already use.
- One agent ranks the findings, separating urgent security concerns from routine drift.
- One agent produces the four recurring reports from their existing definitions, plus on-demand answers in minutes.
- A proposed add-on would let people ask questions of the reports in plain language.
- For eligible low-risk fixes on workstations, an agent applies the approved fix and checks the result; servers always stay under change control and manager approval.
- Failures are reported, not hidden, and the updated status flows into the next cycle.

**The safeguards we are adding**
- The agents read from our tools through identities that can only read; the one identity allowed to make changes is limited to approved fixes and can be switched off at once.
- Every connection goes through a gateway that only allows pre-approved calls.
- The AI treats device data as information, never as instructions, and every finding must point to the data it came from.
- Sensitive device and user details are masked before reports leave the system, and reports go only to their intended audience.
- Every collection, analysis, approval and fix is logged in a way that cannot be altered and feeds our security monitoring.
- The consolidated data store is classified and its access is reviewed continuously.
- A person approves every change; nothing is fixed on a server without change control.

**What the business gains**
- One current view of the estate, refreshed every cycle, with its freshness as a number we can watch.
- Priority questions answered in minutes instead of one to two hours.
- Urgent concerns ranked above routine drift, using the experts' own rules.
- Fixes inside change control, verified afterwards, with failures visible.
- The experts' 16 to 20 reporting hours a week return to investigation and fixing.
- A compliance figure we can defend, measured rather than estimated.
- On money: the deck shows the hours from the brief; once Finance gives us the loaded hourly cost and the working weeks, we type them in and the saving appears live, so we are not quoting a number we did not receive.

**How we start, and what stays in your hands**
- Reporting first; automated fixes are switched on per category after the pilot, workstations before anything else.
- Report definitions, ranking rules, eligibility rules and approver roles stay with the team.
- Everything runs on cloud services we already use and scales down to nothing when idle; the hosting workbook lists every component.

---

## Use Case 03 · OEM Intelligence Agent

*What it is about: the Security Technology Services team keeping up with what three to five vendors change, and whether ABB's contracts already cover it.*

**The problem today**
- Vendor releases, security advisories and end-of-life notices arrive through portals, feeds, mailboxes and blogs, with no single trusted feed.
- Whether something gets noticed depends on who is subscribed, who is available and who checks the portal that week.
- Important updates can be missed while generic alerts create noise, and there is no record of what was reviewed, published or held back.
- Whether a new feature or fix is covered by the contracts we already hold is known to a few Service Experts and confirmed case by case.

**What we propose**
- An agent reads an approved list of vendor sources on a schedule and captures each announcement once, with a reference to where it came from.
- Repeated items are recognised and recorded, so the same change does not raise the same alert twice.
- An AI step summarises what the vendor said, in the vendor's own words for severity and versions, and tags it for the right audience.
- A rating step checks the announcement against a licence register that our Service Experts maintain: covered, not covered, or unclear and sent to an expert.
- Routing rules let routine items publish directly and send security advisories and anything unclear to a named reviewer, who sees a prepared record.
- Published items go to a searchable repository and a targeted Teams notification for the pilot group, and people can ask questions over the published records in Copilot.
- We start with three to five vendors and one pilot group, using the team's existing monitoring notes and history as the starting point.

**The safeguards we are adding**
- Vendor content is cleaned and treated as information, never as instructions, before any AI step sees it, so a vendor page cannot steer the system.
- Every summary must cite its source and may not invent a severity or a version; anything untraceable is not published.
- Each agent has its own identity and only the permissions it needs; Copilot answers within the asking person's own permissions.
- Pending and held-back material is kept apart from published knowledge, so nothing unreviewed surfaces as fact.
- Every collection, rating, review decision and publication is logged in a way that cannot be altered and feeds our security monitoring.
- Notifications go only to their intended audience, and sensitive details are masked before anything leaves the system.

**What the business gains**
- Every vendor announcement is seen once, in one place, with its source.
- The licence position is known before anyone asks.
- Summaries cite their source and never invent a severity.
- People review where it matters; routine items flow.
- Service teams are told, not left to search.
- Answers come from published records only.

**How we start, and what stays in your hands**
- The approved source list, the licence register, the routing rules and the reviewer list stay with the team.
- Anything unclear or security-related waits for a person before it is published.
- Any agent can be stopped instantly by disabling its identity.
- We claim no figures in advance; the pilot group's own records are the baseline.

---

## Use Case 04 · Archon, the AI context engine for Solution Architects

*What it is about: the weeks a Solution Architect spends gathering standards, controls and requirements before design can start.*

**The problem today**
- For every new initiative an architect reads and correlates our 30 to 35 ABB standards and policies, our reference architectures and the external frameworks (NIST, IEC, CIS) by hand to find what applies.
- Establishing that context and producing the initial architecture takes three to four weeks, about 160 hours per initiative, and depends on who does it.
- New architects need a long time to learn their way around our standards and guidance before they are fully effective.
- Manual interpretation leads to inconsistent outcomes and missed requirements, and those become compliance and design gaps later.

**What we propose**
- Archon: a set of AI agents that take the new requirement and build the architecture context, with the architect reviewing at every stage.
- One agent understands the architecture question and the intended outcome and confirms them with the architect.
- One agent searches the ABB standards, policies and reference architectures and lists the applicable controls, each with the clause it comes from.
- One agent aligns those controls to NIST, IEC and CIS, so every ABB requirement carries its global reference.
- One agent derives the use cases and the functional and non-functional requirements, each traced to its source control.
- One agent produces the data for the evaluation criteria and first drafts: the business case, applicable controls, requirements, use cases, building blocks, risks, dependencies, and the HLD and SDP first drafts.
- Previous HLDs, LLDs, SOPs, concept documents and white papers are indexed once, so every initiative starts from what the team has already designed.
- On the stakeholders' figures, context arrives in one to two days instead of three to four weeks, and 10 architects release 1,440 to 3,040 hours a year for design, stakeholder work and risk decisions.

**The safeguards we are adding**
- Every control, requirement and draft statement must cite the document and clause it comes from; if it cannot, it is not produced.
- The documents Archon reads are treated as information, never as instructions, so a document cannot steer the system.
- Each agent has its own identity and only the permissions it needs, and it can only retrieve what the requesting architect is allowed to read.
- Solution documents can describe sensitive designs, so sensitive content is masked before any AI model sees it and outputs go only to the requesting architect.
- Licensed standards such as IEC are used only under the terms of the subscription we already hold.
- Every retrieval, generated statement, review decision and delivered document is logged in a way that cannot be altered and feeds our security monitoring.

**What the business gains**
- Architecture-ready context in days instead of weeks.
- Architect capacity released to higher-value design work.
- One interpretation of the standards, whoever the architect is.
- Every requirement traceable to its source control, so gaps show before design starts.
- Faster onboarding, because new architects work from the same assembled context.
- Enterprise knowledge becomes a reusable asset instead of living in a few experts' heads.

**How we start, and what stays in your hands**
- Shadow mode first: Archon runs on completed initiatives and its context is compared with what the architects produced.
- The architect validates each stage and remains accountable for the final design decision.
- Policy owners keep the standards; what enters the knowledge base and who may read it is the team's call.
- Any agent can be stopped instantly by disabling its identity.

---

## If they ask

- **"Does the AI decide on its own?"** It gathers facts and applies our own rules; people decide anything unclear or high-risk, and every server change goes through change control.
- **"Can it be manipulated?"** Requests and data are treated as information, not instructions, and every decision must cite its source.
- **"What does it cost?"** Each deck's hosting workbook lists every component and quantity; pricing follows once volumes are confirmed.
- **"Why these four?"** Each replaces manual, repetitive judgement with evidence we already hold, and each keeps a person in charge of the exceptions.
- **"What if it goes wrong?"** Every agent has its own identity; disable it and it stops, and nothing it did is missing from the log.
