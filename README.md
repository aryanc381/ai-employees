# Sunday OpenClaw

Dockerized OpenClaw runtime for Sunday.

## Phase 1: Local Docker Baseline

Create local env:

```bash
cp .env.example .env
```

Build and start:

```bash
docker compose up -d --build
```

Check OpenClaw inside the container:

```bash
docker compose exec sunday openclaw --help
docker compose exec sunday openclaw --version
```

View logs:

```bash
docker compose logs -f sunday
```

Stop:

```bash
docker compose down
```

OpenClaw state is mounted at:

```text
./state/openclaw -> /home/sunday/.openclaw
```

Do not commit `state/` or `.env`.

## Phase 2: Persistent State

OpenClaw state is intentionally stored outside the image and outside Git.

Local development:

```text
./state/openclaw
```

VPS deployment:

```text
/var/lib/sunday-openclaw/openclaw
```

See [docs/state.md](docs/state.md).
