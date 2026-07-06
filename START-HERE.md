# START HERE — Lab 2 Local LLM Feasibility

Use this file when you are ready to make Lab 2 work on your laptop.

## Step 1 — Add this folder to GitHub

Put this complete folder inside your main repository:

```text
reearth-strategic-ai-deployment-matrix/
└── lab-2-local-llm-feasibility/
```

Commit and push:

```bash
git add lab-2-local-llm-feasibility
git commit -m "Add Lab 2 local LLM feasibility"
git push
```

## Step 2 — Install LM Studio

1. Download LM Studio from its official website.
2. Open LM Studio.
3. Download a small instruct model.

Recommended models for student laptops:

| Laptop RAM | Suggested model type |
|---:|---|
| 8 GB | 3B–4B quantized instruct model |
| 16 GB | 7B–8B quantized instruct model |
| 32 GB+ | 14B quantized instruct model |

## Step 3 — Start LM Studio Server

1. Load the model.
2. Go to the local server / developer section.
3. Start the server.
4. Keep the server running.

Expected local server URL:

```text
http://localhost:1234/v1
```

## Step 4 — Start Open WebUI

### Option A — Docker Compose

From this folder, run:

```bash
docker compose up -d
```

Then open:

```text
http://localhost:3000
```

### Option B — Windows script

Double-click:

```text
scripts/openwebui-run-windows.bat
```

### Option C — Mac/Linux script

Run:

```bash
chmod +x scripts/openwebui-run-mac-linux.sh
./scripts/openwebui-run-mac-linux.sh
```

## Step 5 — Connect Open WebUI to LM Studio

In Open WebUI:

1. Go to **Admin Settings**.
2. Open **Connections**.
3. Add OpenAI-compatible connection.
4. Use this URL if Open WebUI is running in Docker:

```text
http://host.docker.internal:1234/v1
```

5. Use any placeholder key:

```text
lm-studio
```

6. Save.

## Step 6 — Create the ReEarth Assistant

1. Create a new assistant/model in Open WebUI.
2. Name it:

```text
ReEarth Local Compliance Assistant
```

3. Paste the full contents of:

```text
system-prompt.md
```

4. Add context from:

```text
knowledge-base/reearth-local-context.md
```

## Step 7 — Test and Take Screenshots

Use questions from:

```text
test-cases/reearth-local-llm-test-cases.csv
```

Take screenshots of:

1. LM Studio model loaded.
2. LM Studio server running.
3. Open WebUI running.
4. Open WebUI connection to LM Studio.
5. ReEarth assistant answering a normal product question.
6. ReEarth assistant escalating a risky certificate/legal question.

Save screenshots in:

```text
screenshots/
```

## Step 8 — Submit Lab 2

Your Lab 2 submission is complete when the GitHub folder includes:

- Working setup files.
- System prompt.
- Knowledge base.
- Test cases.
- Evaluation rubric.
- Feasibility report.
- Screenshots.
