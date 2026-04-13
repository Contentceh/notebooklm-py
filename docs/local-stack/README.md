# notebooklm-py bootstrap plan

## Decision

- Preferred clone path: `/home/vgoro/n8n-install/notebooklm-py/`
- We will work from that folder directly.
- Repo-specific notes should also live **inside that fork**, not in a separate top-level docs area.
- Org policy: stack-owned repos should use the `Contentceh` organization as `origin` when applicable.
- Stage 1 is still done **without Docker**.
- Docker is Stage 2, after host-side login/auth/smoke test succeed.

## Preferred final layout

### Fork working tree

- Fork clone path: `/home/vgoro/n8n-install/notebooklm-py`
- Expected upstream base: `teng-lin/notebooklm-py`
- Actual fork remote: `https://github.com/Contentceh/notebooklm-py.git`

### Local runtime paths inside the repo folder

- Bootstrap venv: `/home/vgoro/n8n-install/notebooklm-py/.venv`
- NotebookLM home/auth: `/home/vgoro/n8n-install/notebooklm-py/.local/notebooklm-home`
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

## Transitional note

Right now the fork is **not cloned yet**, so the current files under `n8n-install/docs/notebooklm-py/` are temporary planning notes only.
After clone, they should be moved into the fork under `notebooklm-py/docs/local-stack/`.

## Stage 1 sequence

1. Clone the fork into `/home/vgoro/n8n-install/notebooklm-py`.
2. Create `.venv` inside that repo.
3. Set `NOTEBOOKLM_HOME=/home/vgoro/n8n-install/notebooklm-py/.local/notebooklm-home`.
4. Install `notebooklm-py[browser]`.
5. Install Playwright Chromium.
6. Run `notebooklm login`.
7. Run `notebooklm auth check --test`.
8. Run minimal smoke test.
9. Only after that decide whether Docker migration is worth doing.
