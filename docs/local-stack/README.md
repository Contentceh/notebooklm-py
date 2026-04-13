# notebooklm-py bootstrap plan

## Decision

- Preferred clone path: `/home/vgoro/n8n-install/notebooklm-py/`
- We will work from that folder directly.
- Repo-specific notes should also live **inside that fork**, not in a separate top-level docs area.
- Org policy: stack-owned repos should use the `Contentceh` organization as `origin` when applicable.
- Stage 1 is still done **without Docker**.
- Docker is Stage 2, after host-side auth/smoke test succeed.

## Preferred final layout

### Fork working tree

- Fork clone path: `/home/vgoro/n8n-install/notebooklm-py`
- Expected upstream base: `teng-lin/notebooklm-py`
- Actual fork remote: `https://github.com/Contentceh/notebooklm-py.git`

### Local runtime paths inside the repo folder

- Bootstrap venv: `/home/vgoro/n8n-install/notebooklm-py/.venv`
- NotebookLM home/auth: `/home/vgoro/n8n-install/notebooklm-py/.local/notebooklm-home`
- Playwright browser cache: `/home/vgoro/n8n-install/notebooklm-py/.local/ms-playwright`
- Optional work area: `/home/vgoro/n8n-install/notebooklm-py/.local/work`

### Repo-local documentation

Once the fork is cloned, stack/integration notes should live in:

- `/home/vgoro/n8n-install/notebooklm-py/docs/local-stack/README.md`
- `/home/vgoro/n8n-install/notebooklm-py/docs/local-stack/TODO.md`
- `/home/vgoro/n8n-install/notebooklm-py/docs/local-stack/DEVELOPMENT.md`
- `/home/vgoro/n8n-install/notebooklm-py/docs/local-stack/ENVIRONMENT-LEDGER.md`

## Why this layout

- convenient to work from one folder: code + local docs + bootstrap env;
- simpler navigation during patching/debugging;
- later Docker integration can mount the repo subtree directly if needed;
- `.venv` and `.local/` can stay gitignored.

## Current state

- The fork is cloned at `/home/vgoro/n8n-install/notebooklm-py`.
- Repo-local planning docs were moved into `docs/local-stack/`.
- Host bootstrap is now green through auth and minimal smoke testing.
- Current auth source is a copied-in `storage_state.json` under `.local/notebooklm-home/profiles/default/`.
- Docker-side MVP bridge now runs through the `python-runner` service in `infra-n8n-setup`.
- Current bridge endpoints are available to `n8n` at `http://python-runner:8000/notebooklm/...`.

## Stage 1 sequence

1. Clone the fork into `/home/vgoro/n8n-install/notebooklm-py`.
2. Create `.venv` inside that repo.
3. Set `NOTEBOOKLM_HOME=/home/vgoro/n8n-install/notebooklm-py/.local/notebooklm-home`.
4. Set `PLAYWRIGHT_BROWSERS_PATH=/home/vgoro/n8n-install/notebooklm-py/.local/ms-playwright`.
5. Install `notebooklm-py[browser]`.
6. Install Playwright Chromium.
6. Provide auth either via `notebooklm login` on a GUI-capable machine or by copying in a valid `storage_state.json`.
7. Run `notebooklm auth check --test`.
8. Run minimal smoke test (list notebooks -> create smoke notebook -> add source -> ask).
9. Only after that decide whether Docker migration is worth doing.
