# Setup Guide — LM Studio + Open WebUI for ReEarth

## Goal
Set up a local AI assistant for ReEarth using:

- **LM Studio** as the local model runner and OpenAI-compatible local server.
- **Open WebUI** as the chat interface for testing the assistant.

## 1. Install LM Studio
1. Download and install LM Studio for your operating system.
2. Open LM Studio.
3. Go to the model search/download area.
4. Download a small or medium instruct model that your laptop can run.

### Suggested model size by laptop
| Hardware | Suggested model range | Notes |
|---|---:|---|
| 8 GB RAM | 3B–4B quantized instruct model | Good for basic testing only |
| 16 GB RAM | 7B–8B quantized instruct model | Recommended starting point |
| 32 GB RAM or GPU | 14B+ quantized instruct model | Better quality, slower setup |

You do not need the largest model for this lab. The purpose is feasibility testing, not final production performance.

## 2. Load the model in LM Studio
1. Open the selected model in LM Studio.
2. Keep temperature low for compliance use.
3. Recommended starting parameters:

```text
Temperature: 0.2 to 0.4
Top P: 0.8 to 0.95
Max Tokens: 700 to 1200
Context Length: as high as your machine allows
```

## 3. Start LM Studio Local Server
1. Go to LM Studio's developer/server section.
2. Start the local server.
3. Default local base URL is usually:

```text
http://localhost:1234/v1
```

4. Keep LM Studio running while using Open WebUI.

## 4. Install Open WebUI
Preferred method for most students: Docker.

### Option A — Docker Desktop
1. Install Docker Desktop.
2. Run Open WebUI using the official quick-start command from Open WebUI docs.
3. Open the local Open WebUI URL in your browser.

### Option B — Python install
Use this only if Docker is not working on your system. Follow Open WebUI's official Python installation instructions.

## 5. Connect Open WebUI to LM Studio
Inside Open WebUI:

1. Go to **Admin Settings**.
2. Open **Connections** or provider settings.
3. Add an OpenAI-compatible provider.
4. Use this base URL:

```text
http://host.docker.internal:1234/v1
```

Use the above if Open WebUI is running inside Docker and LM Studio is running on your Windows/Mac host.

If Open WebUI and LM Studio are both running directly on your host system, use:

```text
http://localhost:1234/v1
```

5. API key can be any placeholder value if LM Studio does not require authentication locally, for example:

```text
lm-studio
```

6. Save settings and check whether Open WebUI detects your loaded LM Studio model.

## 6. Create ReEarth Assistant in Open WebUI
1. Create a new model/chat assistant in Open WebUI.
2. Paste the content from `system-prompt.md` as the system prompt.
3. Add the content from `knowledge-base/reearth-local-context.md` as the assistant knowledge/context.
4. Save the assistant as:

```text
ReEarth Local Compliance Assistant
```

## 7. Test the assistant
Use the questions from:

```text
test-cases/reearth-local-llm-test-cases.csv
```

Track results in:

```text
model-testing-notes.md
```

## 8. Screenshot evidence to collect
Place screenshots in the `screenshots/` folder:

1. LM Studio model loaded.
2. LM Studio local server running.
3. Open WebUI connection settings.
4. ReEarth assistant prompt setup.
5. Successful answer to a ReEarth product question.
6. Successful escalation for legal/fraud/audit-critical question.

## Troubleshooting

### Open WebUI cannot connect to LM Studio
Try:

```text
http://host.docker.internal:1234/v1
```

instead of:

```text
http://localhost:1234/v1
```

This matters when Open WebUI is inside Docker.

### Model is too slow
Use a smaller quantized model or reduce context length.

### Answers are too creative
Lower temperature to around 0.2 and strengthen the system prompt.

### Model invents rules or prices
Add stronger grounding instructions:

```text
Do not invent legal requirements, prices, certificate IDs, recycler names, or audit outcomes. If information is unavailable, say so and escalate.
```
