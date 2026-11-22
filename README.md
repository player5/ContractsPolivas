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
- **ChatGPT:** external GitHub/Drive capabilities require verified access in that exact Worker session. Until session proof exists, public dispatch is limited to prepared inline text (`required_capabilities=none`); other cards return `BLOCKED_SESSION_CONNECTOR_NOT_VERIFIED`.
- **Gemini:** no GitHub. Drive tasks need a verified target account (D1/D2/D3), browser-session mapping and package readback; `drive_target` on a card alone is not proof. Until those checks exist, use inline text or return `BLOCKED_SESSION_CONNECTOR_NOT_VERIFIED`.
- The browser Worker currently sends text. It does not claim that a binary file was uploaded. Prepared public text files are embedded into the prompt by Dispatcher.

## Public card fields

A dispatchable new card includes `schema=brown.swarm.public-card.v1`, `contract_id`, `revision`, `iteration`, `attempt`, stable `delivery_id`, `executor`, `mode`, `required_capabilities`, `prompt`, `prompt_blob_sha`, and either `self_contained=true` or a SHA-pinned `files_manifest`. Dependencies use `blocker` and `depends_on`. The prompt must repeat the exact `CONTRACT_ID` and `MODE`.

A files manifest uses schema `brown.swarm.public-files.v1`, includes the matching `contract_id`, and lists one to five files with repository-relative paths under `files/` and Git blob SHA values.

## Invariants

1. Public files must be intentionally prepared for publication. No secrets, cookies, keys, private server addresses, personal data or closed configuration.
2. Dispatcher reads only the configured public repository for public discovery/handoff; missing private credentials must not block the public catalogue.
3. Public cards do not declare execution success, PASS, integration, merge or owner acceptance. `CODE_CHANGE` on the public route is blocked until authenticated producer/GATE/write-set checks are implemented; it cannot inherit permission merely from a public file.
4. Dependencies remain blocked until the prior captured result and Publisher stage are evidenced.
5. Provider mismatch, unknown capability, bad path, missing file, SHA mismatch, unverified external connector, and missing full source package block before enqueue. `required_capabilities=none` does not exempt the card from `self_contained=true` or the manifest.
6. Worker result, Publisher receipt, independent validation, integration and owner acceptance remain separate states.

[Card template](templates/CONTRACT_TEMPLATE.md) · [Prompt template](templates/PROMPT_TEMPLATE.md).

## v0.7.7 candidate compatibility note (2026-11-22)

- Existing C001/V002 smoke cards remain legacy read-only compatibility exceptions; their original delivery IDs and uncertain receipts are unchanged.
- New cards require the exact Markdown `schema=brown.swarm.public-card.v1` field. The attached files manifest remains a separate strict `brown.swarm.public-files.v1` JSON document. The older proposal of a single nested `brown.swarm.public-handoff.v1` manifest is not the active wire format.
- This branch remains an OPEN PR, not merged or production accepted. Live browser send/result and connector mapping are NOT VERIFIED.
