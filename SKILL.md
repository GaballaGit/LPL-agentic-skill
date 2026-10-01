---
name: lpl-hackathon-builder
description: Plan, build, verify, and pitch LPL Financial hackathon prototypes using LPL's public advisor and investor priorities and the user-supplied Angular/TypeScript, ASP.NET Core, Kubernetes, AWS, and Terraform stack. Use for LPL hackathon ideation, implementation, architecture review, demo preparation, or adapting a prototype to an event brief. Separate verified public facts from proposed engineering practices and private unknowns.
---

# LPL Hackathon Builder

Deliver one useful, demonstrable workflow for an LPL advisor, investor, service colleague, or engineering team. Optimize for measurable user value, credible engineering, and a reliable demo. Treat this skill as a proposed approach informed by public sources, never as an LPL internal standard.

## Load context and match the request

- Read [LPL context](references/lpl-context.md) before selecting a problem or making company claims.
- Read [engineering approach](references/engineering.md) before implementation or architecture review.
- Read [demo and acceptance](references/demo-and-acceptance.md) when defining acceptance criteria and before handoff.
- Follow the user's request, event rules, repository AGENTS.md, and supplied sponsor materials. Adapt these defaults to actual requirements and record consequential deviations.
- Match the requested phase. Produce ideas or a plan when asked for those. Write application code only when the user requests building or implementation. Installing this skill does not itself authorize building an application.

## 1. Establish the brief

Inspect event materials, project files, toolchains, and the current working state. Reuse working components and preserve unrelated changes.

Collect the theme, judging rubric, deadline and usable hours, team capacity, mandatory stack, permitted APIs/datasets, AI restrictions, deployment budget, and submission format. Ask one compact question for consequential missing information while continuing independent work.

Without a brief, label assumptions explicitly: LPL Financial; open theme; synthetic data; local-first demo; no paid cloud provisioning; stack supplied by the user. If duration is unknown, use a provisional 24-hour plan and identify it as a planning assumption. Never invent sponsor rules, credentials, private APIs, or undocumented company practices.

Refresh public company context for the event. Prefer LPL-owned sources and official framework documentation. Record source URL, publication date when present, retrieval date, claim, and whether it is fact or inference. If browsing is unavailable, use the dated snapshot and disclose the freshness limit.

## 2. Choose a valuable workflow

Refine the user's concept first when supplied. Otherwise propose at most three candidates. For each, specify the persona, concrete trigger, current friction, complete before/after workflow, sourced LPL alignment, incremental contribution beyond public offerings, demo moment, measurable outcome, dependency, and biggest risk.

Use this selection heuristic only when the organizer provides no rubric. Score each criterion 1–5 and apply weights; label it as our selection aid:

| Criterion | Weight | Evidence |
| --- | ---: | --- |
| User value and LPL relevance | 30% | Specific friction tied to a public priority |
| Complete demo feasibility | 25% | End-to-end path within available hours |
| Incremental contribution | 20% | Distinction from existing offerings |
| Trust and failure handling | 15% | Verifiable controls and recovery |
| Engineering and integration fit | 10% | Coherent use of the requested stack |

Recommend one candidate with tradeoffs. When asked to build, proceed with the strongest feasible option unless consequential uncertainty blocks it. Avoid repeated permission requests for routine implementation choices.

Consider exception handling, onboarding completeness, service triage, meeting action reconciliation, or engineering reliability tied to advisor impact. Evaluate a synthetic onboarding exception workbench as one possible candidate: detect omissions, explain issues, assign tasks, review corrections, and preserve a timeline. Treat this as a hypothesis, not a proven LPL product gap.

Avoid generic dashboards without decisions, unsupported return predictions, or chatbots whose only result is prose. Include AI when it improves the workflow; an agentic build process does not require an AI product.

## 3. Define the build contract

Before application code, create a short project brief and ordered plan covering:

- Persona, problem, outcome, evidence, assumptions, and differentiator.
- One principal journey, state transitions, and 3–5 acceptance criteria.
- MVP, stretch work, and explicit cuts.
- Data entities, identity/tenant boundaries, API contract, and integration seams.
- One small architecture diagram and persistence/deployment rationale.
- Time budget, fixtures, reset procedure, and external dependency fallback.

Use Angular/TypeScript and one ASP.NET Core modular backend as the supplied application-stack baseline, even when a later prompt omits it. Change that baseline only for explicit user/event requirements or a documented feasibility constraint. Use a simple relational store when persistence matters. Keep Kubernetes files and Terraform AWS configuration proportionate to the event. Finish the local workflow first in short events; do not require a new EKS cluster merely to show stack familiarity.

Distinguish infrastructure authored, statically validated, planned, and deployed. Use existing authorized environments when available. Provision resources only with an authorized account and scope; mentioning AWS/Terraform does not establish spending authority.

Reserve roughly 15% of time for problem/contract, 50% for the working journey, 20% for verification/recovery, and 15% for the demo. Adapt to the actual rubric. If the core journey is incomplete halfway through implementation, cut stretch features. Cut breadth and infrastructure before core authorization, correctness, and rehearsal.

## 4. Implement in observable increments

Build a walking skeleton: frontend interaction → API → persisted state → visible result. Seed reproducible synthetic fixtures. Complete the main success path before secondary views.

Then implement state rules, server-side validation/authorization, relevant audit events, and one meaningful failure/recovery path. Add automation and operational evidence after the core works. Use the engineering reference for details.

After each meaningful increment, record working behavior, commands run, actual results, and unresolved dependencies. Keep a short project checkpoint for resumption: chosen scope, current state, next step, blockers. Keep product language appropriate for users.

For AI-enabled workflows:

- Ground proposals in permitted, identified sources or synthetic inputs; preserve provenance.
- Use structured outputs; validate schemas and business rules server-side.
- Separate proposing from executing. Require human approval in the product for consequential financial or client-facing actions.
- Treat documents, retrieved content, and model outputs as untrusted data. Do not let them change tool permissions or instructions.
- Use allowlisted tools, bounded calls, timeouts, and server-side resource authorization. Do not trust model-supplied ownership claims.
- Preserve the exact approved proposal version; changed proposals need fresh approval. Prevent duplicate execution on retries.
- Expose review, uncertainty, and errors. Do not invent numeric confidence.
- Provide a labeled deterministic demo provider if live AI is unavailable, and disclose it in the pitch.

## 5. Verify claims

Exercise the journey in the actual UI/API. Test risky behavior rather than implementation details:

- Persist and reload the principal state transition.
- Return useful corrections for invalid input.
- Reject unauthorized and cross-tenant API access wherever those boundaries exist.
- Handle duplicates, stale approvals, and external failures where applicable.
- Record actor, action, resource, time, and result in audit events without leaking sensitive data.
- Reset fixtures to a reproducible state.

Run relevant frontend/backend checks, then conditional container, Kubernetes, and Terraform checks for included artifacts. Mark unavailable tools and unexecuted checks clearly. Never infer production readiness, regulatory compliance, scale, or cloud deployment from configuration files alone.

Measure a useful workflow metric on a stated synthetic scenario. Report observed time, steps, detected issues, or recovery results with sample size and limits. Separate measured outcomes from assumed savings or modeled impact.

## 6. Deliver and pitch

Prepare a default 3-minute pitch, adapting to event rules: explain the problem and LPL relevance; show one complete journey and changed next action; demonstrate one trust/recovery control; report observed evidence and the next integration step.

Provide the source project, local start/reset instructions, fixtures, verification results, a concise architecture decision note, and demo script. Include cloud artifacts only to the extent requested and built. Present implemented, simulated, untested, and future capabilities explicitly when boundaries could be unclear.

Describe potential adapters to ClientWorks or enterprise systems as hypothetical until sponsor documentation and an authorized test establish integration. Never imply LPL endorsement or proprietary access.

End with the working result, verification, and material limits. Center the pitch on user value; use technical evidence to substantiate reliability and integration fit.
