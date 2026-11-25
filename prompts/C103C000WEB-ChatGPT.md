# C103C000WEB — CRM036 Interop: доверенный gateway с существующим ACL

**Роль:** Worker. **Исполнитель:** ChatGPT. **Исходный тип результата:** private GitHub code+QA. **Блокеры:** 000. **Статус:** PUBLISHED/NOT STARTED. **Продолжение CRM:** CRM-MODULE-INTEROP-036.

## Цель
Продолжить 087 BLOCKED по сохранённому WORKLOG, не дублировать очередь 019, права 028 или IPC 030.

## Самодостаточное техническое задание
CODE_REF contracts/CRM-MODULE-INTEROP-036.md; C087 WORKLOG commit 5bd5a779827573fc031a6ece8e53f7c58389a8b7. Provider/service/version/schema/capability/deadline/generation, trusted gateway with explicit allowlist, default deny without 028, no caller impersonation. Общий host только CRM034.

## write_set
- `implementation/crm036/**`
- `tests/test_crm036_*`
- `docs/CRM-MODULE-INTEROP-036_*`
Любые новые tests/docs/handoff только в этих путях; остальные файлы read-only.

## Критерии и тесты
Fixtures consumer/provider/denied; 403/404/409/413/422/503/504, timeout/rate-limit, no privilege bypass; isolated tests+handoff.

**GPT доступ:** закрытый SEKA_WEB доступен через GitHub, на старте подтвердить собственный доступ и exact refs. CODE_REF прочитать старый CRM контракт + код/тесты; DOCS_REF — BASE/README.md, CURRENT/README.md, docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md, AUDITS/SEKA_WEB_SWARM_081_093_REVISION_2026-11-25.md. Не делать фиктивных выводов по 404 в неправильном дереве. Результат private feature branch+commit, WORKLOG и self-audit внутри write_set, точный handoff CRM034.

**Ссылки на два источника (оба проверены постановщиком):** CODE_REF = player5/SEKA_WEB, feature/crm034-ui-integrity-20261120 @ 30507c3fd17ffdb65640b47d6c2d4be048909377; DOCS_REF = player5/SEKA_WEB @ 17c4ab6f754a76f6ccb5dde408313d1e4b0ef4ae. В CODE_REF нет BASE/README.md, CURRENT/README.md и docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md; эти обязательные документы читать только на DOCS_REF. Проект WIP, не релиз. API v1: manifest.json, register(app), register_view. SQL DDL — только SEKA SQL Manager. Не менять sekamap, рабочий сервер/ПК, legacy Договоры, login min4, темы, чужие контракты, shared core/view_runtime/view_widgets/module_loader/manifest_validator/platform_api/static/index.html. Shared host меняет только CRM034 после независимого QA; без деплоя и merge. Перед кодом проверить старые реализации/тесты, поискать пригодное готовое GitHub решение, Issues, лицензии и безопасность, если доступ есть.

**Сдача:** точные source refs, собственные изменённые файлы/коммит или полный текст, исполняемые инструкции, новые и регрессионные тесты с фактическим stdout и PASS/FAIL/NOT RUN, независимые negative cases, незавершённое, риски/блокеры и NEXT. STATUS_EXECUTION COMPLETE/PARTIAL/BLOCKED по доказательствам. Worker не выдаёт себе независимый PASS.
