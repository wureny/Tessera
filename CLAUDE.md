# Warmpath (working name) — Meta Global AI Developer Hackathon entry

Network OS for organizations whose product is their network (accelerator hubs, university
venture centers, VC platform teams). It keeps relationship data fresh by capturing it from
work exhaust, remembers what people said, and plans a visiting founder's week of intros
under two-sided attention constraints.

**Read `docs/SPEC.html` before doing anything.** It is the source of truth for scope,
data model, demo storyline, schedule and acceptance criteria. If the spec and this file
disagree, the spec wins; if the spec is ambiguous, ask Alix.
`docs/DESIGN.md` records implementation decisions that refine the spec (synthetic world,
planner pipeline, endpoints, eval). Read it next; its §0 lists decisions still open.

## Hard deadline
Submission closes **Wed Nov 4, 2026, 9:00 PM EST**. Target: submitted by Wed afternoon.
Today's work is defined in the spec's schedule section. Build vertical slices that run
end to end; never leave the app in a non-running state at the end of a session.

## Stack
- Backend: Python 3.11+, FastAPI, SQLModel + SQLite (`backend/`)
- Frontend: Vite + React + TypeScript, react-force-graph-2d (`frontend/`)
- LLM: Meta Model API (OpenAI-compatible). All calls go through `backend/llm.py`.
  Model IDs come from env vars, never hard-coded elsewhere.
- Verify model IDs, request formats and audio/PDF input handling against the official
  Meta Model API docs before writing integration code. Do not guess API shapes.

## Env
```
META_API_KEY=
META_BASE_URL=https://api.meta.ai/v1
MODEL_FAST=muse-spark-1.3          # extraction, multimodal capture, drafting
MODEL_REASON=muse-wonder-1.0       # long-context recall, planning, briefs
MODEL_TRANSCRIBE=muse-voice-transcribe-1.0
MODEL_IMAGE=muse-image-1.0         # synthetic demo inputs (business cards etc.)
```
Contributor-tier models are fine for synthetic data only.

## Guardrails (non-negotiable)
- All people and organizations in the data are synthetic and labeled as such. No scraping
  LinkedIn or any real person's data. No real organization's name or branding in the product.
- Outbound messages are drafts that a human confirms. Nothing auto-sends.
- Every stored fact keeps provenance (which interaction it came from, when).
- README claims only what the code actually does. Alix must be able to defend every
  sentence in an interview. If Muse Code was not used, do not say it was.

## Working style
- Small commits with clear messages; commit at the end of every working block.
- Keep `docs/STATUS.md` updated: what runs, what's stubbed, known issues, next step.
- Prefer boring, legible code over clever abstractions. This is a 3-day build.
- When a choice affects the demo or the README story, ask Alix instead of deciding.
