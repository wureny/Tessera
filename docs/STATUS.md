# Status

_Last updated: Sun Nov 1, 2026_

## What runs
Nothing yet. Repo contains docs only.

## Docs
- `docs/SPEC.html` — scope, data model, demo, schedule (source of truth)
- `docs/DESIGN.md` — implementation decisions refining the spec; open decisions D1–D5 in §0

## Blockers
- This cloud session cannot reach `api.meta.ai` (proxy returns 403). M0 needs either the
  domain allowed in the environment's network settings, or to run locally.
- Model IDs not yet verified against official Meta docs. Third-party sources (Nov 1) say:
  base URL `https://api.meta.ai/v1`, OpenAI-compatible `/chat/completions` and `/responses`,
  Spark 1.3 is current. `muse-wonder-1.0`, `muse-voice-transcribe-1.0`, `muse-image-1.0`
  are unverified.

## Next step
Scaffold backend + frontend, `llm.py` with record/replay, seed generator (DESIGN §2), M0.
