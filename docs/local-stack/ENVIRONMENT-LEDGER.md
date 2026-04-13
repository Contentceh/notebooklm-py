# notebooklm-py environment ledger

Purpose: track everything added on the host for Stage 1, so it can be cleaned up later if Docker becomes the permanent runtime.

## Planned paths

- Fork working tree: `/home/vgoro/n8n-install/notebooklm-py`
- Host bootstrap venv: `/home/vgoro/n8n-install/notebooklm-py/.venv`
- NotebookLM home: `/home/vgoro/n8n-install/notebooklm-py/.local/notebooklm-home`
- Optional working area: `/home/vgoro/n8n-install/notebooklm-py/.local/work`

## Repo metadata

- Fork remote URL:
- Upstream remote URL: `https://github.com/teng-lin/notebooklm-py`
- Branch used:

## Record actual deltas here

### Python runtime

- Chosen version:
- Already present before work started: yes / no
- Installed during bootstrap:

### Host OS packages added

- 

### Python packages installed in `.venv`

- 

### Browser / Playwright artifacts added

- Chromium installed via Playwright: yes / no
- Playwright cache path:
- Browser profile path:

### NotebookLM auth artifacts

- `NOTEBOOKLM_HOME` used: `/home/vgoro/n8n-install/notebooklm-py/.local/notebooklm-home`
- `storage_state.json` path:
- extra profiles used:

### Cleanup candidates after Docker migration

- `/home/vgoro/n8n-install/notebooklm-py/.venv`
- host-only Playwright/browser payloads
- host OS packages added only for Stage 1
