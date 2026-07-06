# Open WebUI + LM Studio Connection Settings

## LM Studio Local Server
Start LM Studio local server from the Developer/Server section.

Typical local base URL:

```text
http://localhost:1234/v1
```

## Open WebUI Provider Setting
If Open WebUI is running inside Docker and LM Studio is running on your host system, use:

```text
http://host.docker.internal:1234/v1
```

If both are running directly on the same host system, use:

```text
http://localhost:1234/v1
```

## API Key
For local LM Studio testing, use a placeholder if required:

```text
lm-studio
```

## Assistant Name
```text
ReEarth Local Compliance Assistant
```

## Recommended Model Settings
```text
Temperature: 0.2–0.4
Top P: 0.8–0.95
Max Tokens: 700–1200
```

## Safety Setting
Use the full prompt from:

```text
system-prompt.md
```

## Knowledge Context
Use:

```text
knowledge-base/reearth-local-context.md
```

## Important Note
Do not upload real client data, certificate IDs, private GST/CIN data, or actual audit documents into a local demo unless your system is secured and the data is permitted for testing.
