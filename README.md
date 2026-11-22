# ContractsPolivas — публичная витрина заданий BROWN SWARM

**Статус:** PUBLIC INDEX / TWO TEST CONTRACTS PUBLISHED — C001D000TST DeepSeek, V002D001TST independent validation; real chat dispatch/result capture NOT VERIFIED.

This repository contains only owner-approved public contract cards, provider-specific prompts and explicitly prepared public text files. The Dispatcher reads the public catalogue without a GitHub token, then fetches only the selected card, its prompt and files declared in that card's SHA-pinned manifest. It does not discover or read private project repositories during public dispatch.

**This is NOT the canonical permission/GATE registry.** Original contracts, source commits, write_set, producer permits, GATE evidence and project worklogs remain in their canonical project repositories and BrownGuyGPTmem. A public card is a prepared handoff package, not evidence that a Worker completed the task or that a result passed independent validation.

## Directories

- `contracts/<CONTRACT_ID>.md` — public card and provider assignment.
- `prompts/<CONTRACT_ID>-<PROVIDER>.md` — exact full prompt for the assigned model.
- `files/<CONTRACT_ID>.json` — optional SHA-pinned manifest for public text source files.
- `files/<CONTRACT_ID>/...` — text files explicitly prepared by the contract cutter.
- `templates/` — templates only; never active contracts.
- `INDEX.md` — public catalogue index.

## Provider profiles

- **DeepSeek:** no GitHub/Drive connector assumption. The cutter must make the prompt self-contained or publish up to five text files in the SHA-pinned public manifest.
- **ChatGPT:** GitHub and Drive may be used only when available in the particular Worker chat; declare `required_capabilities`.
- **Gemini:** Drive only; GitHub-dependent work is invalid. Drive tasks must declare `drive_target`; the Worker must verify actual access.
- The browser Worker currently sends text. It does not claim that a binary file was uploaded. Prepared public text files are embedded into the prompt by Dispatcher.

## Public card fields

A dispatchable card includes `contract_id`, `revision`, `iteration`, `attempt`, stable `delivery_id`, `executor`, `mode`, `required_capabilities`, `prompt`, `prompt_blob_sha`, and either `self_contained=true` or a SHA-pinned `files_manifest`. Dependencies use `blocker` and `depends_on`. The prompt must repeat the exact `CONTRACT_ID` and `MODE`.

A files manifest uses schema `brown.swarm.public-files.v1`, includes the matching `contract_id`, and lists no more than five files with repository-relative paths under `files/` and Git blob SHA values.

## Invariants

1. Public files must be intentionally prepared for publication. No secrets, cookies, keys, private server addresses, personal data or closed configuration.
2. Dispatcher reads only the configured public repository for public discovery/handoff; missing private credentials must not block the public catalogue.
3. Public cards do not declare execution success, PASS, integration, merge or owner acceptance.
4. Dependencies remain blocked until the prior captured result and Publisher stage are evidenced.
5. Provider mismatch, unknown capability, bad path, missing file or SHA mismatch blocks before enqueue.
6. Worker result, Publisher receipt, independent validation, integration and owner acceptance remain separate states.

[Card template](templates/CONTRACT_TEMPLATE.md) · [Prompt template](templates/PROMPT_TEMPLATE.md).
