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
