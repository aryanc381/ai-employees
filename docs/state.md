# Persistent State

OpenClaw runtime state must live outside the Docker image.

## Local Path

```text
./state/openclaw
```

The compose file mounts it into the container:

```text
./state/openclaw -> /home/sunday/.openclaw
```

## VPS Path

Use a stable host path:

```text
/var/lib/sunday-openclaw/openclaw
```

In production, mount it the same way:

```text
/var/lib/sunday-openclaw/openclaw -> /home/sunday/.openclaw
```

## What Lives Here

```text
OpenClaw config
WhatsApp login/session
Google Calendar auth
agent sessions
media/cache/log state
```

## What Never Goes In Git

```text
state/
.env
client_secret*.json
tokens
auth/session files
```

## Why This Matters

The container can be rebuilt or recreated without losing Sunday auth/state.

```text
rebuild container
state mount remains
Sunday keeps config and auth
```
