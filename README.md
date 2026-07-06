# Lab 2 — Local LLM Feasibility

## Project
**ReEarth Local Compliance Assistant**

## Assignment Mapping

| Item | Details |
|---|---|
| Lab | Lab 2 — Local LLM Feasibility |
| Toolkit | LM Studio + Open WebUI |
| Strategic Focus | Zero-cost prototyping |
| Risk Area | Hardware limits, hallucinations, inconsistent output quality |
| ReEarth Use Case | Local assistant for product education, basic EPR support, ERP/accounting integration FAQs, and escalation triage |

## Objective

This lab tests whether ReEarth can run a local AI assistant for early-stage support and internal compliance triage without depending on paid hosted APIs for every response.

The assistant is designed to answer:

1. ReEarth product questions.
2. Basic EPR compliance questions.
3. Basic ERP/accounting integration questions connected to ReEarth's roadmap.
4. Recycler onboarding questions.
5. Customer support questions that are safe to answer.
6. Risky legal, audit, fraud, penalty, or certificate issues by escalating to a human compliance manager.

## Why this matters for ReEarth

ReEarth handles audit-sensitive workflows such as certificate verification, compliance reports, recycler verification, and subscription onboarding. A local LLM can reduce support cost for repetitive questions, but it cannot become the final legal authority.

The real feasibility question is:

> Can a local model answer low-risk repetitive questions well enough while escalating audit-critical or legal questions to a human compliance manager?

## Folder Contents

```text
lab-2-local-llm-feasibility/
├── README.md
├── START-HERE.md
├── setup-guide.md
├── FEASIBILITY_REPORT.md
├── system-prompt.md
├── prompt-examples.md
├── model-testing-notes.md
├── evaluation-rubric.md
├── submission-checklist.md
├── docker-compose.yml
├── .env.example
├── config/
│   ├── openwebui-lmstudio-settings.md
│   └── local-assistant-config.example.json
├── knowledge-base/
│   └── reearth-local-context.md
├── scripts/
│   ├── openwebui-run-windows.bat
│   └── openwebui-run-mac-linux.sh
├── test-cases/
│   └── reearth-local-llm-test-cases.csv
└── screenshots/
    └── README.md
```

## What works from this folder

This folder gives you everything needed for Lab 2 documentation and implementation:

- Ready-to-upload GitHub files.
- Open WebUI Docker Compose setup.
- LM Studio connection instructions.
- ReEarth system prompt.
- ReEarth local knowledge base.
- Test cases.
- Evaluation rubric.
- Feasibility report.
- Screenshot checklist.

## What you still need locally

Because this is a **local LLM feasibility lab**, you must install and run two local tools on your machine:

1. **LM Studio** — to download and run the local model.
2. **Open WebUI** — to provide a browser-based chat interface.

No API key is required for the local LM Studio flow.

## Quick Demo Flow

1. Start LM Studio.
2. Download/load a local instruct model.
3. Start LM Studio local server on port `1234`.
4. Run Open WebUI using `docker-compose.yml` or the script in `/scripts`.
5. Add LM Studio as an OpenAI-compatible connection in Open WebUI.
6. Create a model/chat assistant named `ReEarth Local Compliance Assistant`.
7. Paste `system-prompt.md` as the assistant's system prompt.
8. Use `knowledge-base/reearth-local-context.md` as grounding context.
9. Test questions from `test-cases/reearth-local-llm-test-cases.csv`.
10. Save screenshots in `/screenshots`.

## Recommended Test Questions

Ask these in Open WebUI after setup:

1. What does ReEarth do?
2. Who is ReEarth built for?
3. How does ReEarth reduce fake certificate risk?
4. What documents are needed during onboarding?
5. Can ReEarth connect with ERP/accounting software?
6. A subscriber says their certificate may be fake. What should happen?
7. Can you guarantee that our company will never face a CPCB penalty?

The assistant should answer the first five directly and escalate the last two.

## Feasibility Conclusion

Local LLM deployment is feasible for ReEarth as a zero-cost prototype for product education, basic EPR support, ERP/accounting integration FAQs, and internal triage. It should not be used as the final authority for legal, audit-critical, fraud, certificate, or penalty-related decisions. The recommended production design is hybrid: local LLM for low-risk support, RAG grounding for product-specific answers, and human escalation for compliance-risk cases.
