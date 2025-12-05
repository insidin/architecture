# AI Vision & Operating Model Memo  
*From buy-vs-build to an AI-shaped IT operating model*  

**Author:** Jan Uyttenhove — Insidin BV  
**Date:** 5 December 2025  

---

This memo is written to help organizations navigate a fast-moving shift: AI is changing not only what we deliver, but also how we design, govern, and operate digital capabilities. The practical consequence is that technology decisions—especially buy-versus-build—can no longer be treated as stable, multi-year conclusions. They must be revisited as the market matures, as interaction patterns change, and as delivery methods evolve.

The intent of this memo is to provide a compact framing that can be used repeatedly: it clarifies which distinctions matter, why governance and platform enablement become more important (not less) as engineering accelerates, and which lightweight operating mechanisms help keep decisions aligned with reality.

## The distinction that matters: autonomy and determinism, not “AI apps”
The most useful classification is not “AI applications versus normal applications.” The distinction that consistently drives architecture, governance, and platform needs is between **deterministic solutions**, **non-deterministic solutions**, and **agentic solutions**.

Deterministic solutions may be produced using AI-aided engineering, but their runtime behavior remains predictable and testable. This is where a key shift is underway: **the durable artifact moves from code to specification.** As engineering becomes more automated, code becomes easier to generate, refactor, and replace. Specifications, constraints, tests, and evaluation criteria become the enduring assets. This does not remove the need for discipline; it relocates it toward what defines correctness, safety, and maintainability.

Non-deterministic solutions include AI in runtime behavior and therefore include variability, context dependence, and probabilistic output. This does not inherently make them “worse,” but it does change what “good engineering” means. Observability, evaluation, traceability, and explicit safety measures become first-class requirements rather than optional afterthoughts.

Agentic solutions are non-deterministic systems with **delegated autonomy**: they do not merely respond, they can plan and act—often through tool calls and workflow execution. The important implication is that **autonomy becomes a primary risk driver.** As autonomy increases, the organization must rely on recognized risk-mitigation patterns (such as policy gating, constrained tool access, human approval steps, auditability, and rollback/override mechanisms). This memo does not expand those patterns in detail, but it explicitly links autonomy levels to risk posture and mitigation requirements, because the linkage is fundamental to operating agentic systems responsibly.¹

## AI as an IT operating model evolution, not a separate track
It can be useful to run “AI adoption” activities as an accelerator for a time, but it is risky to institutionalize AI as a parallel world. AI is not a niche. It reshapes mainstream IT practices: architecture and review criteria, governance controls, platform capabilities, delivery methods, and digital experience expectations.

The most sustainable direction is to treat AI as a catalyst for a broader evolution of the IT operating model. The question is not “where do AI initiatives live,” but how IT as a whole becomes capable of absorbing rapid change while staying governed, secure, and aligned to business expectations.

## A practical operating mechanism: monthly vision and portfolio alignment
Because the AI landscape evolves quickly, static strategies age fast. A pragmatic way to avoid both underreaction and overreaction is a lightweight **monthly AI vision and operating alignment review**. The intent is not to create a heavy governance structure, but to ensure that core assumptions are refreshed frequently enough to guide real decisions.

A monthly cadence works because it forces a repeatable discipline: what materially changed since last month, what that means for strategy and priorities, and what needs adjustment in platform enablement and the solution portfolio. This creates a controlled way to reassess buy/build/hybrid decisions as market maturity changes, and it prevents over-investment in choices that were rational at the time but are no longer optimal.

## Platform stance: enable adoption without over-platformizing
Organizations commonly fail in one of two ways: they build too little platform, causing uncontrolled adoption and fragmented risk; or they over-platformize early, committing to designs and standards that do not survive the next wave of tooling.

A pragmatic stance is to focus first on **minimum viable enablement and guardrails**—capabilities that reduce risk while accelerating delivery. Typical examples include access mediation and policy enforcement points, auditability, monitoring of cost and reliability, and operational controls that make experimentation safe. The goal is not to standardize everything early, but to ensure that adoption happens inside a governed boundary and remains adaptable.

## The interaction shift: your “user” may soon be an assistant
A frequently underestimated driver is the change in interaction patterns. Digital ecosystems are shifting. Increasingly, enterprise services will be consumed by a human through a personal assistant, or by an assistant acting under delegated authorization. Even if an organization does not build such assistants itself, customers, partners, and employees will bring them.

This shifts expectations for how systems expose capabilities: interfaces become more structured, delegation and policy enforcement become more central, and “assistant-mediated” interaction becomes a design consideration. The implication is not immediate redesign. It is to treat current architectures as short-term fit, and to include an explicit evolution track and bounded pilots to validate what next interaction patterns require.

## Buy vs build in the era of AI-aided engineering
AI-aided engineering changes the buy-versus-build equation because it changes the cost and speed profile of building and evolving software. As code becomes easier to generate and replace, vendor value must be assessed differently. The durable value increasingly shifts to specifications, constraints, evaluation harnesses, security controls, compliance evidence, operational resilience, and the platform guardrails that make rapid change safe.

This reframes buy-versus-build around a new baseline question: **can we implement, evolve, and operate this capability quickly and safely within our governed platform boundaries?** If the answer is yes, vendor differentiation must be clear to justify cost and lock-in. If the answer is no, the constraint is rarely engineering capacity; it is platform maturity and governance readiness.

This also has implications for procurement: major procurements should anticipate specification-driven change, transferability of ownership, and compatibility with platform guardrails. Otherwise, organizations risk buying solutions optimized for yesterday’s delivery and operating assumptions.

## Practical next steps
The fastest path to maturity is not a grand redesign. It is a small set of operating disciplines that keep decisions current and keep adoption safe:

Establish a monthly AI vision and operating alignment review that explicitly refreshes assumptions and translates them into portfolio and platform adjustments. Standardize a shared vocabulary based on determinism and autonomy so that architecture and governance decisions become consistent. Evolve platform enablement as “minimum viable guardrails plus acceleration,” expanding based on real adoption pressure rather than theoretical completeness. Update buy-versus-build and procurement criteria to reflect that specifications and controls become the durable assets as code becomes increasingly easy to replace.

---

# References & internal addendum

**R1 — Linking autonomy to risk posture (pointer to a separate topic)**  
In agentic systems, increased autonomy increases operational and compliance risk, which must be mitigated through established patterns (policy gating, constrained tools, approvals, auditability, override/rollback). This memo references that linkage but does not elaborate the mitigation patterns in detail. That is a separate document topic: “Agentic Risk & Mitigation Patterns by Autonomy Level.”¹

**R2 — Where to apply this internally (examples to fill in locally)**  
Use the monthly review to periodically reassess:
- major program procurements and RFPs (for AI-aided engineering readiness and future transferability),
- customer-facing agentic blueprints (for evolution tracks and assistant-mediated interaction readiness),
- platform capabilities (for guardrail gaps discovered via adoption),
- architecture and decision forums (for updated criteria aligned to determinism/autonomy).

---

¹ **Suggested companion note:** *Agentic Systems: Autonomy Levels, Risk Classes, and Mitigation Patterns* (separate working document).

---

© 2025 Insidin BV. All rights reserved.
