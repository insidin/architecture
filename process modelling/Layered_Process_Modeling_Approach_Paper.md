*A practical paper on separating context, responsibility, and
realization in process design*

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Executive summary<br />
</strong>This paper explains a three-level approach to process modeling.
Level 1 describes what the process does. Level 2 defines who is
responsible for what. Level 3 explains how the process is realized
through procedures, workflows, systems, and automation. The central idea
is simple: levels are separated by intent, not by notation.</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

# Quick reference

| **Level** | **Question answered** | **Primary focus**                                 | **Typical exclusions**                        |
|-----------|-----------------------|---------------------------------------------------|-----------------------------------------------|
| **L1**    | What is done?         | Business context and major flow                   | Roles, systems, implementation detail         |
| **L2**    | Who does what?        | Responsibilities, handoffs, business decisions    | API logic, timer mechanics, technical routing |
| **L3**    | How is it realized?   | Workflow, procedures, automation, execution logic | Purely abstract business-only framing         |

# 1. Purpose and scope

This paper presents a layered approach to process modeling for IT,
digital operating models, and process-enabled architecture work. It is
intended for analysts, architects, product and platform teams,
governance practitioners, and delivery leaders who need a disciplined
way to move from business understanding to operational design without
collapsing everything into one overloaded diagram.

The approach uses three levels:

- Level 1, context and what

- Level 2, responsibility and who does what

- Level 3, realization and how

The value of the method lies in preserving clarity between business
framing, accountability, and implementation.

# 2. Why this approach is needed

In many organizations, process discussions move too quickly from a
problem statement to tickets, workflows, products, and automation. When
that happens, three concerns become mixed in a single model: business
context, responsibility design, and realization design.

That mixing creates recurring problems. High-level diagrams become
unreadable. Accountabilities remain vague. Technical design decisions
are made before the real business handoffs have been clarified.
Auditability suffers because there is no clean relationship between the
business decision and the mechanism that enforces it. Delivery teams
then inherit process models that are neither suitable for stakeholder
discussion nor detailed enough for implementation.

The layered approach solves this by separating concerns in a deliberate
sequence. First define the business context. Then define roles and
responsibilities. Only then define the realization mechanism.

# 3. Core principle, distinguish levels by intent, not notation

The levels should not be distinguished primarily by notation. The same
notation may appear across levels, including BPMN-style tasks, gateways,
and swimlanes.

What matters is the intent of the model:

- A model is Level 1 when it exists to explain the business context and
  major flow.

- A model is Level 2 when it exists to explain responsibilities,
  handoffs, approvals, and business decisions.

- A model is Level 3 when it exists to explain realization, execution
  logic, workflow behavior, procedures, systems, and automation.

This principle is essential because it prevents teams from assuming that
a diagram becomes technical simply because it uses BPMN-like shapes. A
BPMN-looking diagram can still be a responsibility model. The question
is not what symbols are used, but what design question the model is
answering.

# 4. Level 1, context and what

Level 1 provides the highest-level view of the process. It explains what
is done to solve the problem.

The purpose of Level 1 is to establish a stable business-context view.
It should be understandable without implementation knowledge and without
assumptions about organizational ownership. It identifies the process
boundary, the start and end, the major activities, and the intended
outcome.

A sound Level 1 model typically includes the process name, the problem
being addressed, the major end-to-end steps, and the expected result. It
should not include actors, swimlanes, systems, APIs, automation details,
or fine-grained decisions.

A simple access management example at Level 1 might read as follows:
receive access need, validate request, assess whether access can be
granted, grant or deny access, record outcome. This is enough to explain
the process at business level without committing to roles or technology.

# 5. Level 2, responsibility and who does what

Level 2 refines the process into a role-based operating view. It
explains who is responsible for what, where the meaningful handoffs
occur, and which business decisions matter.

The purpose of Level 2 is to define accountability and operating
behavior. Roles may be shown through swimlanes or another role-based
structure. Tasks may be described in more detail than at Level 1, and
gateways may be used where they represent business decisions rather than
execution mechanics.

Typical Level 2 content includes roles and actors, business activities
per role, approvals, handoffs, major exception paths, and the
information needed to support business decisions. Level 2 should remain
technology-agnostic. It should avoid API calls, system routing logic,
workflow engine behavior, timer semantics, field mappings, and
product-specific implementation detail.

A strong test for Level 2 is this: if the tooling changed tomorrow,
would the model still remain valid? If yes, the model is probably still
at the right level. In an access process, Level 2 might show a
requester, a product owner, a second-line reviewer, and an operations
role, with steps such as submit request, review request, perform
second-line review, execute approved change, and communicate outcome.

# 6. Level 3, realization and how

Level 3 defines how the Level 2 process is realized in practice. This is
where procedures, workflows, systems, integrations, and automation are
designed.

The purpose of Level 3 is to make the process operational. At this
level, the model becomes suitable for implementation, workflow
configuration, service design, and feature delivery. Level 3 may
therefore include user tasks, service tasks, forms, APIs, rule
execution, notifications, timers, escalations, retries, integration
logic, audit logging, and mappings to components or services.

A Level 3 access example may define a request form that captures purpose
and justification, a policy decision step that evaluates conditions, a
low-risk auto-approval path, a high-risk human approval path, a
provisioning API call, an audit log write, a requester notification, and
a remediation path if provisioning fails.

This is the realization level because the model now describes the
mechanism by which the process runs.

# 7. The critical boundary between Level 2 and Level 3

This boundary is where most confusion arises. Because Level 2 already
includes actors, handoffs, approvals, and gateways, it can look very
similar to Level 3. The distinction remains the same: intent.

Level 2 is about accountable behavior. It explains who is responsible,
what business decisions matter, and how work passes between roles. Level
3 is about executable behavior. It explains how those responsibilities
are realized through procedures, systems, automation, and workflow
logic.

A useful test is to ask whether a statement is primarily about
responsibility or primarily about realization mechanism. 'Product owner
reviews request' belongs in Level 2. 'Call policy decision service'
belongs in Level 3. 'Sensitive access requires second-line approval'
belongs in Level 2. 'If the risk score exceeds the threshold, create a
review task and wait 48 hours before escalation' belongs in Level 3.

# 8. Gateway interpretation

The same gateway shape can appear in both Level 2 and Level 3. The
distinction lies in the type of decision being modeled.

At Level 2, a gateway represents a business decision or accountability
split. Example: does this request require second-line approval?

At Level 3, a gateway represents an execution or realization decision.
Example: did the policy service return a high-risk classification, or
did provisioning succeed within the timeout?

This distinction is important because it allows a role-based model to
remain clear without forcing technical execution logic into it.

# 9. Practical modeling rules

A practical way to preserve the boundary is to apply naming discipline.

At Level 2, activity names should be expressible without naming a tool.
Good examples include review request, assess sensitivity, approve
access, investigate incident, escalate case, and confirm outcome.

At Level 3, activities should map clearly to a realization mechanism.
Examples include call policy service, run rule table, create workflow
task, invoke provisioning API, send notification, write audit record,
and start escalation timer.

A second practical rule is to avoid collapsing all levels into a single
model. A process should first be framed at Level 1, then refined into a
Level 2 responsibility view, and only then detailed at Level 3 where
implementation or operationalization is required.

# 10. Application in IT and digital operating contexts

This layered approach is particularly useful in IT because many
processes sit at the boundary between business policy and technical
enforcement. Access management, data quality management, incident
handling, exception management, change approval, onboarding, and
operational governance all benefit from the separation.

The approach also supports collaboration across roles. Business
stakeholders can engage at Level 1 and Level 2 without being forced into
implementation detail. Delivery and platform teams can work at Level 3
with a clearer understanding of what must be realized and why.
Governance and assurance functions benefit because the relation between
policy, accountability, and technical enforcement becomes more
traceable.

# 11. Concluding view

The strength of the layered process modeling approach lies in its
simplicity. Level 1 explains what the process does. Level 2 explains who
is responsible for what. Level 3 explains how the process is realized.

The method does not depend on a single notation and should not be
reduced to a notation debate. The real discipline is conceptual:
separate business context, accountability, and realization so that each
can be designed with clarity and then connected in a controlled way.

When applied consistently, the approach yields cleaner process analysis,
better operating design, stronger traceability into implementation, and
more durable process documentation.

# Appendix A, quick comparison of Level 2 and Level 3

| **Aspect**                  | **Level 2**                            | **Level 3**                               |
|-----------------------------|----------------------------------------|-------------------------------------------|
| Primary question            | Who is responsible for what?           | How is it realized?                       |
| Focus                       | Accountability and business decisions  | Execution and implementation logic        |
| Typical content             | Roles, handoffs, approvals, exceptions | Tasks, rules, APIs, timers, notifications |
| Should survive tool change? | Yes                                    | Not necessarily                           |
| Good activity example       | Review request                         | Invoke approval workflow service          |
