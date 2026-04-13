# notebooklm-py environment ledger

Purpose: track everything added on the host for Stage 1, so it can be cleaned up later if Docker becomes the permanent runtime.

## Planned paths

- Fork working tree: `/home/vgoro/n8n-install/notebooklm-py`
- Host bootstrap venv: `/home/vgoro/n8n-install/notebooklm-py/.venv`
- NotebookLM home: `/home/vgoro/n8n-install/notebooklm-py/.local/notebooklm-home`
- Playwright browser cache: `/home/vgoro/n8n-install/notebooklm-py/.local/ms-playwright`
- Optional working area: `/home/vgoro/n8n-install/notebooklm-py/.local/work`

## Repo metadata

- Fork remote URL: `https://github.com/Contentceh/notebooklm-py.git`
- Upstream remote URL: `https://github.com/teng-lin/notebooklm-py`
- Branch used: `main`

## Record actual deltas here

### Python runtime

- Chosen version: `python3.11` / Python 3.11.2
- Already present before work started: yes
- Installed during bootstrap: no new host Python package installed; reused existing system `python3.11`

### Host OS packages added

- none so far
- pre-existing helpers observed on host: `google-chrome`, `xdg-open`, `xvfb-run`
- pre-install manual package baseline saved to `.local/work/host-manual-packages.before.txt`

### Python packages installed in `.venv`

- upgraded bootstrap tooling: `pip`, `setuptools`, `wheel`
- installed editable package: `-e .[browser]`
- key installed runtime deps: `playwright`, `click`, `httpx`, `rich`
- full freeze saved to `.local/work/bootstrap-venv-freeze.txt`

### Browser / Playwright artifacts added

- Chromium installed via Playwright: yes
- Playwright cache path: `/home/vgoro/n8n-install/notebooklm-py/.local/ms-playwright`
- Browser profile path: `/home/vgoro/n8n-install/notebooklm-py/.local/notebooklm-home/profiles/default/browser_profile`

### NotebookLM auth artifacts

- `NOTEBOOKLM_HOME` used: `/home/vgoro/n8n-install/notebooklm-py/.local/notebooklm-home`
- `storage_state.json` path: `/home/vgoro/n8n-install/notebooklm-py/.local/notebooklm-home/profiles/default/storage_state.json` (present)
- extra profiles used: none

### Cleanup candidates after Docker migration

- `/home/vgoro/n8n-install/notebooklm-py/.venv`
- host-only Playwright/browser payloads
- host OS packages added only for Stage 1

## Current bootstrap status

- repo bootstrap is green through package install, Playwright browser download, auth validation, and minimal smoke testing
- `notebooklm --version` works (`0.3.4`)
- `notebooklm doctor --fix` succeeded for profile-dir creation
- `notebooklm auth check --test --json` returned `status: ok`
- auth is currently provided by repo-local `storage_state.json`
- minimal smoke path passed: create notebook -> add pasted-text source -> wait ready -> ask with cited answer

## Smoke artifacts

- auth check result: `.local/work/auth-check-test.json`
- list output before smoke: `.local/work/list-before.txt`
- smoke notebook create result: `.local/work/create-smoke.json`
- smoke source add result: `.local/work/smoke-source-add.json`
- smoke source wait result: `.local/work/smoke-source-wait.json`
- smoke ask result: `.local/work/smoke-ask-with-source.json`
- temporary smoke notebook ID: `3a3b265d-975d-4290-a385-0c2cb5fe4f4d`
