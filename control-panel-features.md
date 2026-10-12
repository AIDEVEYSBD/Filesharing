# Control panel: the full feature set

A target state for the Agent Factory control plane, written as if it were finished. This is what the Control page and the panes around it should do for the people who run an estate of governed agents. It is a design ambition, not an inventory of what is built today; nothing here should be read as a claim about the current product.

The control panel has one job: let a small team run many agents safely, know what they are doing at every moment, stop or steer them in seconds, and prove afterwards what happened and why.

---

## 1. Situational awareness

- **Estate at a glance.** One screen that answers, without scrolling: what is running, what is waiting on a person, what failed in the last hour, what it is all costing, and whether any guardrail fired. Every figure opens its records.
- **Live flow of every run.** Each active run drawn as the shape it actually has: parallel branches, loops, sub-runs and gates, with the agent in flight lit and the next hand-off visible before it happens.
- **Attention queue.** A ranked list of the things that need a human now: approvals, refusals that stopped a run, budget breaches, drift alerts, failing health checks. Ordered by blast radius and age, not arrival.
- **Time travel.** Any dashboard view can be scrubbed back to any moment, so "what did the estate look like at 03:14 when the alert came in" is a drag, not a database query.
- **Window and comparison.** Every card has its own window (24h to all time) and a comparison window ("vs the previous 7 days"), with the deltas explained in words.
- **Narrated status.** A plain-language line at the top of the page, regenerated continuously from the records: "Quiet. Three runs in flight, one awaiting Priya, spend on track for the month."
- **Ambient signals.** A browser tab title, a favicon badge and an optional desktop notification that change state when something needs a person, so the panel can be left open on a side screen.
- **Agent heartbeat wall.** A tile per deployed agent showing its last run, its health over the last fourteen runs, its cost trend and whether its benchmark held on the latest eval.
- **Dependency map.** Which agents call which tools, connectors, peers and sub-agents, with the blast radius of any one of them going down shown by selecting it.

## 2. Fleet and lifecycle

- **Design to retire in one view.** Every agent's position on the lifecycle spine (designed, validated, benchmarked, deployed, observed, retired), each stage lit only by its own record.
- **Promotion gates.** Deploying to production requires a passing eval, a signed policy review and no open findings; the gate shows exactly which condition is unmet.
- **Versions and digests.** Every deployment pinned to a spec digest; a diff between any two versions in the vocabulary of the spec (nodes, grants, gates, guards), not JSON.
- **Canary and shadow runs.** A new version runs beside the old one on the same inputs for a chosen share of traffic; the panel shows the disagreement rate before anyone flips the switch.
- **Rollback in one click.** Any previous version can be reinstated, with the runs that happened in between flagged for re-review.
- **Drift watch.** The panel notices when an agent's outcomes shift (disposition mix, confidence, cost per run, tool mix) relative to its benchmark and raises it before anyone complains.
- **Retirement with provenance.** Retiring an agent records who, why and what replaced it; its runs stay replayable forever.
- **Templates and lineage.** New agents can be cut from a certified template; the panel shows which agents descend from which template and whether they have drifted from it.
- **Fleet actions.** Pause, resume, drain, reroute or kill across a selection of agents with one confirmation and one audit event.

## 3. Runs and live intervention

- **Steer a run.** Inject guidance to the agent in flight, add a constraint, swap the model for the next step, or hold it at the next gate, all recorded as operator actions in the journal.
- **Kill with a reason.** The kill switch asks for a reason, records the control it exercised, and shows what was abandoned.
- **Replay as it happened.** Every finished run replays through the same board and transcript it ran in, with the clock scrubbable and every tool call's request and response one click away.
- **Diff two runs.** Pick two runs of the same agent and see where they diverged: inputs, decisions, tools called, cost, time.
- **Re-run from a step.** Re-execute a run from any node with the same inputs, a changed input, or a different model, to answer "would it have decided differently".
- **Counterfactual preview.** Before resuming a suspended run, preview what the next step would do with the proposed answer.
- **Sub-run and peer visibility.** Agents invoked by agents, and peers reached over A2A, drawn inside the run that called them, with their own costs and refusals rolled up.
- **Attachments and artefacts.** Every file a run wrote, every ticket it raised and every message it sent, listed with links and previews, downloadable as one bundle.
- **Stuck detection.** A run whose current step has exceeded the agent's own historical p95 is flagged, with the tool call it is waiting on named.

## 4. Approvals and human-in-the-loop

- **One inbox.** Every gate across every agent in one list, with the evidence the agent gathered laid out the way a reviewer reads it, not the way the model emitted it.
- **Decide with context.** The gate shows the decision, the confidence, the evidence it rests on, the policy clauses cited, the precedents, and what the agent will do next for each possible answer.
- **Delegation and escalation.** Gates route to roles, not names; a gate unanswered within its window escalates up a defined chain and the panel shows where it is.
- **Batch decisions.** Approve or refuse a set of similar gates together, with a sample shown and a per-item override.
- **Decision assistance.** The assistant drafts a note for the reviewer summarising the case and the two or three facts that decide it, clearly marked as a draft.
- **Reviewer analytics.** Time to decision, overturn rate, agreement with the model, per reviewer and per agent, so the gate budget can be tuned with evidence.
- **Signed decisions.** Every approval is signed by the SSO identity, stamped with the control it exercised, and exportable as an attestation.

## 5. Guardrails and policy

- **Controls as the index.** Every refusal, taint, gate and kill in the estate is counted against the control that fired it; clicking a control shows its firings across all agents.
- **Policy in the vocabulary of frameworks.** Controls grouped by NIST SP 800-53, CSF 2.0 and ISO 27001 domains, with the evidence an assessor asks for generated from the records.
- **Policy simulation.** Change a grant, a gate threshold or a scope and see which past runs would have been refused or gated under the new policy before applying it.
- **Least-privilege advisor.** Tools an agent holds but has never used, sinks without a gate, and scopes wider than observed usage, each with a one-click tightening.
- **Taint lineage.** Any value derived from untrusted content can be traced forward to every place it was used and backward to where it entered.
- **Injection and exfiltration watch.** Detected prompt injections, blocked tainted writes and unusual egress listed with the content that triggered them, redacted for secrets.
- **Policy change control.** Every policy edit is a reviewed change with a diff, an approver and an effective time; rollbacks are first-class.
- **Emergency posture.** A single "lockdown" that raises every gate to read-only, drains the queue and holds all sinks, with the controls it exercised listed.

## 6. Identity and access

- **People, roles, permissions.** Who can view, run, approve, deploy, configure and administer, with every change signed and every session listed.
- **Non-human identity register.** Every agent, attached agent, MCP server, API key and vault credential with what authenticates it, what it may reach, when it last acted and who owns it.
- **Findings with fixes.** Unowned identities, unused keys, stale credentials, over-broad grants and ungated risky tools, each with a one-click remediation.
- **Credential rotation.** Rotate any credential from the panel with the agents that depend on it shown first and tested after.
- **Access reviews.** Scheduled attestations where owners confirm or revoke each identity they are responsible for, tracked to completion.
- **Step-up authorization.** Destructive fleet actions and policy changes require a fresh authentication within the last few minutes.

## 7. Cost and FinOps

- **Spend by anything.** Provider, model, agent, step, person, tool, hour of day, with every figure reproducible from journalled tokens and the price sheet.
- **Budgets that stop runs.** Per period, per agent and per team; the panel refuses new runs past the budget and says so where the run was started.
- **Forecast.** Projected month-end spend from the trailing run rate, with the confidence band and the three agents most responsible.
- **Routing economics.** Which steps could move to a smaller or local model with no loss on the eval, how much that would save, and a button that routes them.
- **What-if calculator.** Replay any window's workload on any model or provider, including hardware you do not own yet, priced by the token or by the hour.
- **Anomaly alerts.** A run or an agent spending beyond its own history is flagged while it is still running, not on the invoice.
- **Reconciliation.** Journalled spend set against what the cloud actually billed, with the gap explained.
- **Chargeback.** Cost allocated to teams and clients by agent and by run, exportable for internal billing.

## 8. Quality and evals

- **Benchmarks per agent.** Every agent carries its latest eval score, the model it was measured on, and whether the current deployment still matches that measurement.
- **Compare models.** Run a labelled set across candidate models and get quality, cost per case and latency side by side, with a recommendation and the cases where they disagreed.
- **Regression gates.** A deployment that scores below its predecessor on the benchmark is blocked until a person overrides it with a reason.
- **Production sampling.** A share of real runs flows into a review queue; disagreements become new labelled cases with one click.
- **Confusion and calibration.** Per-disposition confusion matrices and confidence calibration curves, per agent and per model.
- **Golden runs.** Mark a run as the reference for its input; future runs on the same input are diffed against it automatically.

## 9. Knowledge

- **Corpus health.** What is admitted, what is waiting, what is stale against its source, and what nothing retrieves, with a re-fetch and re-index that preserves provenance.
- **Retrieval observability.** For any answer or agent decision, the passages retrieved, their scores, what the reranker changed, and what the grounding check said.
- **Admission workflow.** Fetch, clean, review, admit, with the diff from the previous version and the policy the admission rests on.
- **Coverage map.** Which frameworks, standards and regulations the corpus covers, by clause, and the questions it could not answer last week.

## 10. Integrations and surfaces

- **Connector catalogue.** Every system an agent can reach, its interface (API, MCP, DB, files, events), the security layer between, its last call and its error rate.
- **MCP broker view.** Which tools are exposed to which agents and peers, with live call counts and refusals per tool.
- **Agent Factory as a client.** The control plane's own MCP and A2A surfaces listed with their consumers and keys.
- **Webhook and queue intake.** Trigger queues per agent with depth, age, workers and dead letters, and a replay for anything that failed.
- **ITSM and chat.** Approvals, kills and incidents mirrored to ServiceNow, Teams or Slack, with the decision taken there signed back into the journal.

## 11. Observability

- **Traces.** Every run as a waterfall of spans with model time, tool time and wait time separated, exportable to OpenTelemetry.
- **Logs with meaning.** The journal filtered by kind, control, tool, person or taint, with the prose view for reading and the JSON view for copying.
- **SLOs.** Per agent: success rate, p95 run time, cost per run, refusal rate, with error budgets and burn alerts.
- **Health checks.** Connectors, models, vector store, queue and peers probed continuously; a failing dependency shows which agents it will stop.
- **Correlation.** A kill, a refusal, a cost spike and a connector error that happened together are shown together.

## 12. Incident response

- **Incidents from signals.** A refusal storm, a budget breach, a drift alert or a failed health check opens an incident with the affected agents and runs attached.
- **Runbooks.** Each incident type carries the steps to take, the controls involved and the people to call, executable from the panel where the step is an action it can take.
- **Containment actions.** Pause an agent, revoke a key, block a sink, drain a queue, each recorded against the incident.
- **Post-incident record.** A timeline assembled from the journal, the decisions taken and by whom, exportable as the report.

## 13. Compliance and audit

- **Evidence on demand.** For any control and any period, the firings, the approvals, the policy versions and the identities involved, packaged for an assessor.
- **Immutable journal.** Every run's record hashed and chained; tampering is detectable and the panel shows the verification state.
- **Retention and redaction.** Secrets and personal data redacted in the record by rule, with the redaction itself logged; retention periods enforced per record class.
- **Regulatory views.** The estate seen through DPDP, GDPR, SEBI, RBI or NIST AI RMF, listing the obligations each agent touches and the evidence for each.
- **Attestations.** Owners periodically attest that their agents still do what they were approved to do, with the diff since the last attestation.

## 14. Collaboration

- **Comments on anything.** A run, a step, a gate, a control or a cost figure can carry a thread, with mentions that notify.
- **Hand-offs.** Assign a review, an incident or a finding to a person or role with a due time; the attention queue tracks it.
- **Shared views.** Save a filtered, windowed view of any page and share it by link; the link reproduces the exact state.
- **Reports.** Weekly and monthly summaries generated from the records, narrated by the assistant, reviewed before sending.

## 15. Assistance and automation

- **Ask the control plane.** The assistant answers from live records, draws charts, opens the relevant page, and drafts actions it cannot take without a person confirming.
- **Explain this.** Any refusal, decision, cost figure or drift alert can be explained in plain words with the records cited.
- **Suggested actions.** The panel proposes tightenings, routings, retirements and reviews from what it observes, each with the evidence and a single confirming click.
- **Scheduled operations.** Nightly evals, weekly access reviews, monthly cost reports and corpus refreshes, run by the platform and reported in the attention queue.
- **Self-healing within policy.** Retry transient tool failures, fall back to a declared backup model, and reroute around a failing connector, all within limits a person set and all recorded.

## 16. Experience

- **Command palette.** Every page, agent, run, control and action reachable by typing.
- **Keyboard first.** Approve, refuse, kill, next, previous, open, without a mouse.
- **Density and theme.** Compact and comfortable densities, light and dark, subject colours on or off, remembered per person.
- **Mobile approvals.** Gates and kills usable from a phone with the same evidence and the same signature.
- **Accessibility.** Screen-reader labels on every figure, focus order that follows reading order, no information carried by colour alone.
- **Offline-tolerant.** The panel degrades to the last known state with a clear stale marker when the backend is unreachable, and never shows a blank.

## 17. Multi-tenant and executive

- **Many estates.** Clients or business units as separate estates with their own policies, budgets and identities, switchable from one place by those who hold the permission.
- **Executive summary.** A one-page view for leadership: agents in production, decisions made, people-hours returned, incidents, spend against budget, controls exercised, all with the period comparison.
- **Benchmarks across estates.** Cost per decision, refusal rate and gate turnaround compared across estates, anonymised where required.
