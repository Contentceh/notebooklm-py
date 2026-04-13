# notebooklm-py development process

Use this process only if `notebooklm-py` needs local patching, hardening, or custom integration work.

## Scope

This document is about our stack-local work around a fork/clone of `teng-lin/notebooklm-py` at:

- `/home/vgoro/n8n-install/notebooklm-py`

## Working rules

1. Start from a working host bootstrap first.
2. Keep repo-local notes under `docs/local-stack/` inside the fork.
3. Keep runtime/auth under `.local/` inside the repo folder but outside git tracking.
4. Separate clearly:
   - upstream library behavior;
   - our fork/local changes;
   - our auth/runtime environment;
   - our Docker/integration glue.
5. Track every non-default host addition in `ENVIRONMENT-LEDGER.md`.
6. If a workaround is only for Stage 1 bootstrap, mark it as removable after Docker migration.


## Current MVP integration path

- Integration point: `/home/vgoro/n8n-install/python-runner/main.py`
- Runtime shape: Dockerized `python-runner` service mounts `./notebooklm-py:/opt/notebooklm-py`
- Auth/state path inside container: `NOTEBOOKLM_HOME=/opt/notebooklm-py/.local/notebooklm-home`
- Dependency injection: `python-runner/requirements.txt` installs local path `-e /opt/notebooklm-py`
- Bridge implementation is intentionally thin and shells out to the official CLI via `python -m notebooklm`

Current MVP endpoints:

- `GET /notebooklm/healthz`
- `POST /notebooklm/list`
- `POST /notebooklm/ask`

Proven smoke from inside the `n8n` container network:

- `GET http://python-runner:8000/notebooklm/healthz?test_auth=true`
- `POST http://python-runner:8000/notebooklm/list`
- `POST http://python-runner:8000/notebooklm/ask`
