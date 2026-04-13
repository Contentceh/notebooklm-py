# notebooklm-py TODO

## Stage 0 — repo preparation

- [x] Confirm or create the fork repo URL
- [x] Clone the fork into `/home/vgoro/n8n-install/notebooklm-py`
- [x] Add/verify upstream remote pointing to `teng-lin/notebooklm-py`
- [x] Create repo-local docs dir `docs/local-stack/`
- [x] Move these temporary planning docs into the fork

## Stage 1 — host bootstrap without Docker

- [x] Confirm exact host Python version to use (`3.11` or `3.12`) — using `python3.11`
- [x] Record pre-install host package baseline
- [x] Create `.venv` at `/home/vgoro/n8n-install/notebooklm-py/.venv`
- [x] Set `NOTEBOOKLM_HOME=/home/vgoro/n8n-install/notebooklm-py/.local/notebooklm-home`
- [x] Set `PLAYWRIGHT_BROWSERS_PATH=/home/vgoro/n8n-install/notebooklm-py/.local/ms-playwright`
- [x] Ensure `.venv` and `.local/` are gitignored in the fork
- [x] Install `notebooklm-py[browser]`
- [x] Install Playwright Chromium
- [ ] Run `notebooklm login`
- [x] Run baseline `notebooklm auth check` (shows missing `storage_state.json`)
- [ ] Run `notebooklm auth check --test`
- [ ] Run smoke test: list notebooks / create test notebook / simple ask flow

Current blocker:

- server-side auth is still missing (`storage_state.json` does not exist yet)
- no reusable browser cookie DB was found under `/home/vgoro`
- to continue, we need either a successful `notebooklm login` with usable GUI/browser interaction or a copied-in auth state (`storage_state.json` / `NOTEBOOKLM_AUTH_JSON`)
- [x] Record all host-side deltas in `ENVIRONMENT-LEDGER.md`

## Stage 2 — decide on Docker

- [ ] Decide whether runtime should stay on host or move into Docker
- [ ] If Docker is chosen, define auth/state handoff from `.local/notebooklm-home`
- [ ] Define compose mount/env layout
- [ ] Validate Docker-side smoke test

## Stage 3 — cleanup after Docker migration

- [ ] Remove `.venv` if no longer needed on the host
- [ ] Remove Playwright/browser payloads if they were host-only
- [ ] Review host OS packages installed only for Stage 1
- [ ] Remove obsolete bootstrap files and temporary notes
