# Setup Guide — LM Studio + Open WebUI for ReEarth

## Goal

Set up a local ReEarth assistant using:

- **LM Studio** as the local model runner and OpenAI-compatible local server.
- **Open WebUI** as the chat interface.

## 1. Install LM Studio

1. Download and install LM Studio.
2. Open LM Studio.
3. Search for an instruct model.
4. Download a model that your laptop can run.

### Suggested model size

| Hardware | Suggested model range | Notes |
|---|---:|---|
| 8 GB RAM | 3B–4B quantized instruct model | Basic testing only |
| 16 GB RAM | 7B–8B quantized instruct model | Recommended starting point |
| 32 GB RAM or GPU | 14B+ quantized instruct model | Better output, heavier runtime |

You do not need the largest model. The lab is about feasibility testing.

## 2. Load model in LM Studio

Recommended starting settings:

```text
Temperature: 0.2 to 0.4
Top P: 0.8 to 0.95
Max Tokens: 700 to 1200
Context Length: as high as your machine allows
```

## 3. Start LM Studio Local Server

1. Go to LM Studio's developer/server section.
2. Start the local server.
3. Expected local base URL:

```text
http://localhost:1234/v1
```

4. Keep LM Studio running while using Open WebUI.

## 4. Install/Open Open WebUI

### Recommended: Docker Compose

From this folder, run:

```bash
docker compose up -d
```

Open:

```text
http://localhost:3000
```

### Windows quick command

Run:

```text
scripts/openwebui-run-windows.bat
```

### Mac/Linux quick command

Run:

```bash
chmod +x scripts/openwebui-run-mac-linux.sh
./scripts/openwebui-run-mac-linux.sh
```

## 5. Connect Open WebUI to LM Studio

Inside Open WebUI:

1. Go to **Admin Settings**.
2. Open **Connections**.
3. Add OpenAI-compatible provider.
4. If Open WebUI is running in Docker and LM Studio is running on your host system, use:

```text
http://host.docker.internal:1234/v1
```

5. If both are running directly on the host system, use:

```text
http://localhost:1234/v1
```

6. API key can be a placeholder:

```text
lm-studio
```

7. Save settings.
8. Check whether the loaded LM Studio model appears in Open WebUI.

## 6. Create ReEarth Assistant

1. Create a new assistant/model in Open WebUI.
2. Name it:

```text
ReEarth Local Compliance Assistant
```

3. Paste `system-prompt.md` as the system prompt.
4. Paste or upload `knowledge-base/reearth-local-context.md` as assistant knowledge/context.

## 7. Test the assistant

Use:

```text
test-cases/reearth-local-llm-test-cases.csv
```

Track results in:

```text
model-testing-notes.md
```

## 8. Screenshots to collect

Save screenshots in the `screenshots/` folder:

1. LM Studio model loaded.
2. LM Studio local server running.
3. Open WebUI home page running.
4. Open WebUI connection settings.
5. ReEarth assistant prompt setup.
6. Assistant answering a safe product question.
7. Assistant escalating a risky fraud/legal/certificate question.

## Troubleshooting

### Open WebUI cannot connect to LM Studio

Use:

```text
http://host.docker.internal:1234/v1
```

instead of:

```text
http://localhost:1234/v1
```

This matters when Open WebUI is inside Docker.

### Model is slow

Use a smaller quantized model or reduce context length.

### Answers are too creative

Lower temperature to around `0.2`.

### Model invents rules, prices, or legal guarantees

Strengthen the grounding instruction:

```text
Do not invent legal requirements, prices, certificate IDs, recycler names, audit outcomes, or guaranteed regulatory results. If information is unavailable, say so and escalate.
```
