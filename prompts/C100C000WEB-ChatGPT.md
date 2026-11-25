# C100C000WEB — CRM035 DevKit: дельта init/doctor и реальная валидация

**Роль:** Worker. **Исполнитель:** ChatGPT. **Исходный тип результата:** private GitHub code+QA. **Блокеры:** 000. **Статус:** PUBLISHED/NOT STARTED. **Продолжение CRM:** CRM-MODULE-DEVKIT-035.

## Цель
Не переписывать готовый CLI/generator/validator RC1. Закрыть проверенные пробелы host API и дать действующий module template.

## Самодостаточное техническое задание
CODE_REF implementation/crm035/cli.py blob 95f1065b7891de5f96ef439807470331a51f5961. Исторические 19 test PASS/Chromium 3 относятся к старому запуску. data_only interactive navigation пока unsupported; host исправления только handoff.

## write_set
- `implementation/crm035/**`
- `tests/test_crm035_*`
- `docs/CRM-MODULE-DEVKIT-035_*`
Любые новые tests/docs/handoff только в этих путях; остальные файлы read-only.

## Критерии и тесты
init/validate/doctor against real inspect_module, copy→enable для schema/legacy, data_only truthful; path traversal/overwrite/duplicate nav; old regression.

**GPT доступ:** закрытый SEKA_WEB доступен через GitHub, на старте подтвердить собственный доступ и exact refs. CODE_REF прочитать старый CRM контракт + код/тесты; DOCS_REF — BASE/README.md, CURRENT/README.md, docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md, AUDITS/SEKA_WEB_SWARM_081_093_REVISION_2026-11-25.md. Не делать фиктивных выводов по 404 в неправильном дереве. Результат private feature branch+commit, WORKLOG и self-audit внутри write_set, точный handoff CRM034.

**Ссылки на два источника (оба проверены постановщиком):** CODE_REF = player5/SEKA_WEB, feature/crm034-ui-integrity-20261120 @ 30507c3fd17ffdb65640b47d6c2d4be048909377; DOCS_REF = player5/SEKA_WEB @ 17c4ab6f754a76f6ccb5dde408313d1e4b0ef4ae. В CODE_REF нет BASE/README.md, CURRENT/README.md и docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md; эти обязательные документы читать только на DOCS_REF. Проект WIP, не релиз. API v1: manifest.json, register(app), register_view. SQL DDL — только SEKA SQL Manager. Не менять sekamap, рабочий сервер/ПК, legacy Договоры, login min4, темы, чужие контракты, shared core/view_runtime/view_widgets/module_loader/manifest_validator/platform_api/static/index.html. Shared host меняет только CRM034 после независимого QA; без деплоя и merge. Перед кодом проверить старые реализации/тесты, поискать пригодное готовое GitHub решение, Issues, лицензии и безопасность, если доступ есть.

**Сдача:** точные source refs, собственные изменённые файлы/коммит или полный текст, исполняемые инструкции, новые и регрессионные тесты с фактическим stdout и PASS/FAIL/NOT RUN, независимые negative cases, незавершённое, риски/блокеры и NEXT. STATUS_EXECUTION COMPLETE/PARTIAL/BLOCKED по доказательствам. Worker не выдаёт себе независимый PASS.
