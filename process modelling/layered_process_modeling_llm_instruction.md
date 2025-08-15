# Instruction for Applying the Layered Process Modeling Approach

## Purpose

Use this instruction when analyzing, reviewing, or generating process models based on a three-level approach:

- **Level 1 = What**
- **Level 2 = Who does what**
- **Level 3 = How it is realized**

The purpose of the method is to separate business context, accountability, and realization so that process models stay clear, traceable, and useful for both design and implementation.

## Core principle

Do not distinguish the levels by notation alone.

The same notation, including BPMN-style tasks, gateways, and swimlanes, may appear in multiple levels. The correct distinction is based on **modeling intent**.

- **Level 1** explains the business context and major flow.
- **Level 2** explains responsibilities, handoffs, approvals, and business decisions.
- **Level 3** explains realization, workflow behavior, procedures, systems, and automation.

A reliable shorthand is:

- **Level 2 = accountable behavior**
- **Level 3 = executable behavior**

## How to apply each level

### Level 1, Context and What

Use Level 1 to describe what the process does to solve the problem.

Include:
- process boundary
- start and end
- major end-to-end steps
- intended outcome

Exclude:
- roles
- swimlanes
- systems
- APIs
- automation logic
- implementation details

### Level 2, Responsibility and Who does what

Use Level 2 to describe who is responsible for what and where meaningful business decisions and handoffs occur.

Include:
- roles or actors
- swimlanes if useful
- business activities per role
- handoffs
- approvals
- major business decisions
- major exception paths
- required information or evidence for decisions

Exclude:
- API calls
- workflow engine mechanics
- system routing logic
- timer semantics
- field mappings
- technical retries
- product-specific implementation detail

### Level 3, Realization and How

Use Level 3 to describe how the Level 2 process is realized in practice.

Include:
- procedures
- user tasks
- service tasks
- forms
- APIs
- rule execution
- notifications
- timers and escalations
- retries and exception handling
- integration logic
- audit logging
- mapping to services, features, or components

## Boundary rule between Level 2 and Level 3

This is the most important distinction.

### It is Level 2 if:
- the statement is about responsibility
- the step is phrased in business terms
- the model remains valid if the tooling changes

Examples:
- Review request
- Assess sensitivity
- Approve access
- Investigate issue
- Escalate case

### It is Level 3 if:
- the statement is about realization mechanism
- the step defines execution logic
- the model is implementation-ready

Examples:
- Call policy decision service
- Run rule table
- Create workflow task
- Invoke provisioning API
- Wait 48 hours, then escalate
- Write audit record

## Gateway interpretation rule

A gateway may appear in both Level 2 and Level 3.

- At **Level 2**, the gateway is a business decision.
  - Example: Does this request require second-line approval?
- At **Level 3**, the gateway is an execution decision.
  - Example: Did the policy service return a high-risk result?

## Working method

When asked to analyze or generate a process model:

1. Start with **Level 1** unless another level is explicitly requested.
2. Create **Level 2** to define roles, accountabilities, handoffs, and business decisions.
3. Create **Level 3** only when realization, workflow, automation, or implementation detail is needed.
4. Do not collapse all levels into one diagram unless explicitly requested.
5. If mixed content appears, separate it into the appropriate levels.

## Review checklist

For every activity or gateway, ask:

1. Is this about **business context**?
2. Is this about **responsibility and accountability**?
3. Is this about **realization mechanism and execution logic**?

Then classify accordingly:
- business context = Level 1
- responsibility = Level 2
- realization = Level 3

## Output expectation

When producing output:
- make the level explicit
- keep language appropriate to that level
- avoid implementation detail in Level 1 and Level 2
- avoid vague business-only wording in Level 3 when realization must be specified
- preserve traceability from Level 1 to Level 2 to Level 3
