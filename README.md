# memelli-claude-team-shell — RAIL INSTANCE

Mirror of operator Mel's local locked dashboard (127.0.0.1:7777), running rail-side on Railway.

Two instances of the same operator surface — one on Mel's laptop, one on the rail. Same GUC token (1604). Same operator identity. Different physical location.

## Endpoints

| Method | Path | Auth | Purpose |
|---|---|---|---|
| GET | / | open | Dashboard HTML |
| GET | /api/health | open | Liveness probe |
| GET | /api/status | open | Groq + Anthropic live probe + env-presence |
| GET | /api/whoami | open | Auth state |
| POST | /api/auth | open | Exchange GUC for op_session cookie |
| GET | /api/ledger | open | Ping ledger tail (in-memory) |
| GET | /api/events | open | SSE stream |
| POST | /api/ping | **operator** | Master-loop ping — fans Groq slaves |
| POST | /api/groq | **operator** | Groq proxy |
| POST | /api/claude | **operator** | Anthropic Claude proxy |

## Env vars (set at Railway project level)

- `GROQ_API_KEY` — required for Groq slaves
- `ANTHROPIC_API_KEY` — required for `/api/claude`
- `GUC_TOKEN` — defaults to `1604` (operator's lock token)
- `OPERATOR_EMAIL` — defaults to `osmemelli@gmail.com`
- `PORT` — Railway-injected

## Built by

The local instance (Claude Code on Mel's laptop) pushed this via GitHub PAT, GUC token 1604, 2026-05-13.
