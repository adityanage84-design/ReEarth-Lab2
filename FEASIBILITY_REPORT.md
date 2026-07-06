# Feasibility Report — ReEarth Local LLM Assistant

## Lab

Lab 2 — Local LLM Feasibility

## Toolkit

LM Studio + Open WebUI

## Strategic Focus

Zero-cost prototyping for AI-powered compliance support.

## Product Context

ReEarth is a subscription-based EPR compliance and verified recycling platform for plastic-producing SMEs, D2C brands, FMCG startups, e-commerce private labels, and compliance consultants.

The platform helps users manage:

1. Verified recycler access.
2. CPCB-aligned certificate workflows.
3. Audit-ready documents.
4. Compliance dashboards.
5. Subscription-based compliance operations.

## Feasibility Question

Can ReEarth use a local LLM to answer low-risk support questions and triage risky compliance issues without relying on paid hosted APIs?

## Implementation Summary

A local assistant was designed using LM Studio as the model runner and Open WebUI as the chat interface.

The assistant was configured with:

1. A ReEarth-specific system prompt.
2. Product context from the ReEarth PRD and business overview.
3. Strict grounding rules.
4. Escalation rules for legal, audit, fraud, certificate, and penalty-related questions.
5. Test cases covering product support, EPR basics, ERP/accounting roadmap questions, recycler onboarding, and risk escalation.

## Intended Assistant Capabilities

The assistant can answer:

1. What ReEarth does.
2. Who ReEarth serves.
3. How verified recycling reduces trust gaps.
4. What the dashboard shows.
5. What onboarding information may be needed.
6. How ERP/accounting integrations may work in the future.
7. Which issues need human compliance manager review.

## Out-of-Scope Decisions

The assistant must not make final decisions on:

1. Certificate fraud.
2. Legal compliance interpretation.
3. CPCB notices.
4. Penalty exposure.
5. Official certificate revocation.
6. Recycler misconduct investigation.
7. Contract/payment disputes.

## Risk Controls

| Risk | Control |
|---|---|
| Hallucinated compliance advice | Low temperature and strict system prompt |
| Fake legal certainty | Mandatory escalation rules |
| Invented pricing | Prompt instructs not to invent prices |
| Certificate fraud mishandling | Escalation to human compliance manager |
| Hardware limitations | Small/medium quantized model recommended |
| Inconsistent answers | Test cases and evaluation rubric included |

## Recommended Use

The local LLM is suitable for:

1. Internal prototype testing.
2. Product education.
3. Basic EPR support.
4. FAQ handling.
5. Internal triage before human review.

It is not suitable as:

1. Final legal advisor.
2. Final compliance decision-maker.
3. Official audit response system.
4. Certificate fraud authority.

## Feasibility Conclusion

Local LLM deployment is feasible for ReEarth as a zero-cost prototype for product education, basic EPR support, ERP/accounting integration FAQs, and internal triage.

However, it should not be used as the final authority for audit-critical compliance decisions. The recommended production approach is a hybrid system:

1. Local LLM for low-risk support.
2. RAG knowledge grounding for product-specific responses.
3. Human escalation for legal, certificate, fraud, and regulatory-risk cases.

## Final Recommendation

Proceed with local LLM testing for Lab 2 and use the findings to inform Lab 4, where ReEarth will move from a basic local assistant toward a more grounded RAG chatbot using Dify + Ollama.
