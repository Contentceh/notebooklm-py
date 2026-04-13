# notebooklm-py TODO

## Stage 0 — repo preparation

- [ ] Confirm or create the fork repo URL
- [ ] Clone the fork into `/home/vgoro/n8n-install/notebooklm-py`
- [ ] Add/verify upstream remote pointing to `teng-lin/notebooklm-py`
- [ ] Create repo-local docs dir `docs/local-stack/`
- [ ] Move these temporary planning docs into the fork

## Stage 1 — host bootstrap without Docker

- [ ] Confirm exact host Python version to use (`3.11` or `3.12`)
- [ ] Record pre-install host package baseline
- [ ] Create `.venv` at `/home/vgoro/n8n-install/notebooklm-py/.venv`
- [ ] Set `NOTEBOOKLM_HOME=/home/vgoro/n8n-install/notebooklm-py/.local/notebooklm-home`
- [ ] Ensure `.venv` and `.local/` are gitignored in the fork
- [ ] Install `notebooklm-py[browser]`
- [ ] Install Playwright Chromium
- [ ] Run `notebooklm login`
- [ ] Run `notebooklm auth check --test`
- [ ] Run smoke test: list notebooks / create test notebook / simple ask flow
- [ ] Record all host-side deltas in `ENVIRONMENT-LEDGER.md`

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
