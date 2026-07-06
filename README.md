# Lab 2 — Local LLM Feasibility

## Project
**ReEarth — Local Compliance Assistant**

## Assignment Component
- **Lab:** Lab 2: Local LLM Feasibility
- **Primary Toolkit:** LM Studio + Open WebUI
- **Strategic Focus:** Zero-cost prototyping
- **Known Risks:** Hardware limits and inconsistent output quality

## Objective
This lab tests whether ReEarth can run a local AI assistant for early-stage support and internal compliance triage without depending on paid hosted APIs for every response.

The assistant is designed for:

1. Answering ReEarth product questions.
2. Explaining basic EPR compliance concepts in simple language.
3. Answering basic ERP/accounting integration questions related to ReEarth's future roadmap.
4. Helping ReEarth staff qualify whether a query is safe to answer or needs human escalation.

## Why this lab matters for ReEarth
ReEarth handles audit-sensitive compliance workflows. A local LLM can help prototype an assistant cheaply, privately, and quickly, but it cannot be treated as a final legal or regulatory authority. The feasibility question is not “can the model answer everything?” The real question is:

> Can a local model answer low-risk repetitive questions well enough while escalating audit-critical or legal questions to a human compliance manager?

## Final Lab Output
This folder contains:

```text
lab-2-local-llm-feasibility/
├── README.md
├── setup-guide.md
├── system-prompt.md
├── prompt-examples.md
├── model-testing-notes.md
├── evaluation-rubric.md
├── submission-checklist.md
├── config/
│   ├── openwebui-lmstudio-settings.md
│   └── local-assistant-config.example.json
├── knowledge-base/
│   └── reearth-local-context.md
├── test-cases/
│   └── reearth-local-llm-test-cases.csv
└── screenshots/
    └── .gitkeep
```

## Recommended Demo Flow
Use this flow during submission or viva:

1. Open LM Studio.
2. Load a local instruct model.
3. Start the local server.
4. Open Open WebUI.
5. Connect Open WebUI to the LM Studio local server.
6. Add the ReEarth system prompt.
7. Ask 5 test questions:
   - What does ReEarth do?
   - How does ReEarth reduce fake certificate risk?
   - What documents are needed during onboarding?
   - Can ReEarth connect to ERP/accounting software?
   - A subscriber says their certificate may be fake. What should happen?
8. Show that the assistant escalates risky issues instead of pretending to give final legal advice.

## Success Criteria
The local assistant is considered feasible if it:

- Explains ReEarth clearly.
- Answers low-risk EPR and product questions in simple language.
- Refuses or escalates legal, audit-critical, fraud, or penalty-related decisions.
- Does not invent pricing, legal rules, or guaranteed outcomes.
- Works acceptably on available laptop hardware.

## Feasibility Conclusion Template
Use this conclusion in your final report after testing:

> Local LLM deployment is feasible for ReEarth as a zero-cost prototype for product education, basic EPR support, and internal triage. However, it should not be used as the final authority for audit-critical compliance decisions. The recommended production approach is a hybrid model: local LLM for low-risk support, RAG knowledge grounding for product-specific answers, and human escalation for legal, certificate, fraud, or regulatory-risk cases.
