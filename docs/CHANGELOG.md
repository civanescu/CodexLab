# Change log

## 2026-11-24 — Persist task completion

- Updated `app/service.py` to replace the completed task in the loaded collection and save it, so the completion timestamp and status survive subsequent reads.
- Verification: reproduced the old behavior with isolated JSON storage, then verified persistence with isolated service checks and live `POST /tasks/1/complete` followed by `GET /tasks/1` on port 8001. Both API responses showed `status=done` and the same non-null `completed_at`. Restored `data/tasks.json` after the API check.

## 2026-11-24 — Fix task status filtering

- Updated `app/service.py` to compare each task status with the requested `status` value, so `status=open` and `status=done` return matching tasks.
- Verification: service-level checks pass against the sample data (3 open tasks and 1 done task). HTTP verification could not run because port 8000 was unavailable and the environment denied binding the Uvicorn server.

## 2026-11-24 — Implementation workflow guidance

- Expanded `AGENTS.md` and the `change-docs` skill with the requested workflow: inspect before editing, report findings before the first patch, run setup when needed, and rerun relevant verification after each code change.
- Verification: reviewed the instruction and changelog diffs; no application code changed, so app checks were not needed.

## 2026-11-24 — Baseline app review and change documentation workflow

- Added repository guidance and the `change-docs` skill so implementation tasks record their changes in this file.
- Installed the declared FastAPI, Uvicorn, and Pydantic requirements into the existing `.venv` using `uv`.
- Started the development server with `uvicorn app.main:app --reload` at `http://127.0.0.1:8000`.
- Checked the live health, list, status-filter, search, task-detail, and not-found routes. Health, list, detail, and 404 behavior work. The status filter currently returns an empty list for `status=open`, and `q=launch` currently returns every task.
- Exercised create and complete against an isolated temporary JSON file. Creating persists correctly. Completing returns `done` in its immediate response but does not persist: a subsequent lookup still reports `open`.
- Verification note: route read checks used the running server. The installed Starlette test client could not run because its optional `httpx2` dependency is absent; create/complete behavior was checked through the service functions with isolated storage instead.
