# C099C000WEB — UI Lab v0: четыре реальные страницы без патча host

**Роль:** Worker. **Исполнитель:** ChatGPT. **Исходный тип результата:** private GitHub code+QA. **Блокеры:** 000. **Статус:** PUBLISHED/NOT STARTED. **Продолжение CRM:** CRM-UI-020 / CRM-UI-WIDGETS-027.

## Цель
Создать новый постоянный test module одной папкой из уже существующего seka.ui027_demo, старый demo не менять.

## Самодостаточное техническое задание
CODE_REF implementation/crm027/examples/seka.ui027_demo/backend.py и manifest.json (blobs c4802126872a7b1818e2b7fe6f28466feda08890 и 687370162f768bc44ce63961f68fd53e3f628f5c). Table/Tree/Dialog/Widget реальные events, API v1; явно RAM ONLY.

## write_set
- `implementation/crm027/examples/seka.ui_lab/**`
- `tests/test_seka_ui_lab_*.py`
- `docs/SEKA_UI_LAB_*`
Любые новые tests/docs/handoff только в этих путях; остальные файлы read-only.

## Критерии и тесты
Isolated host discover/install, 4 views, two users, 403/409, malformed/XSS, rollback/restart; old CRM027 regression, browser real or NOT RUN.

**GPT доступ:** закрытый SEKA_WEB доступен через GitHub, на старте подтвердить собственный доступ и exact refs. CODE_REF прочитать старый CRM контракт + код/тесты; DOCS_REF — BASE/README.md, CURRENT/README.md, docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md, AUDITS/SEKA_WEB_SWARM_081_093_REVISION_2026-11-25.md. Не делать фиктивных выводов по 404 в неправильном дереве. Результат private feature branch+commit, WORKLOG и self-audit внутри write_set, точный handoff CRM034.

**Ссылки на два источника (оба проверены постановщиком):** CODE_REF = player5/SEKA_WEB, feature/crm034-ui-integrity-20261120 @ 30507c3fd17ffdb65640b47d6c2d4be048909377; DOCS_REF = player5/SEKA_WEB @ 17c4ab6f754a76f6ccb5dde408313d1e4b0ef4ae. В CODE_REF нет BASE/README.md, CURRENT/README.md и docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md; эти обязательные документы читать только на DOCS_REF. Проект WIP, не релиз. API v1: manifest.json, register(app), register_view. SQL DDL — только SEKA SQL Manager. Не менять sekamap, рабочий сервер/ПК, legacy Договоры, login min4, темы, чужие контракты, shared core/view_runtime/view_widgets/module_loader/manifest_validator/platform_api/static/index.html. Shared host меняет только CRM034 после независимого QA; без деплоя и merge. Перед кодом проверить старые реализации/тесты, поискать пригодное готовое GitHub решение, Issues, лицензии и безопасность, если доступ есть.

**Сдача:** точные source refs, собственные изменённые файлы/коммит или полный текст, исполняемые инструкции, новые и регрессионные тесты с фактическим stdout и PASS/FAIL/NOT RUN, независимые negative cases, незавершённое, риски/блокеры и NEXT. STATUS_EXECUTION COMPLETE/PARTIAL/BLOCKED по доказательствам. Worker не выдаёт себе независимый PASS.
