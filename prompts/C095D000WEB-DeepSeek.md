# C095D000WEB — Tree: wire revision/ACK adapter

**Роль:** Worker. **Исполнитель:** DeepSeek. **Исходный тип результата:** TEXT source in chat. **Блокеры:** 000. **Статус:** PUBLISHED/NOT STARTED. **Продолжение CRM:** CRM-UI-WIDGETS-027.

## Цель
Не переписывать две сохранённые версии 082. Реализовать маленький автономный переходник под действительный SEKA API v1.

## Самодостаточное техническое задание
Host ACK={baseRevision,revision,patch}, demo revision строка. Tree 082 ожидал {ok,revision,viewOrNodes}. toHostEvent({event,revision,data}); fromHostAck(wire,expectedRevision) возвращает success лишь при верном baseRevision и новой revision, patch max120 ops/128KiB, event max32KiB; expand/select/context/move. Вывести wire.js/wire.test.js/README.md целиком.

## write_set
- `implementation/crm027/tree_wire_alpha/**`
Любые новые tests/docs/handoff только в этих путях; остальные файлы read-only.

## Критерии и тесты
Node tests 403/409/stale string revision, invalid/large payload, disallowed event, 2 concurrent events; не мутировать view при отказе. Будущий CRM034 handoff в README.

**DeepSeek вход:** весь необходимый публичный контракт утилиты дан здесь, private GitHub/Drive не нужен. Не утверждай чтение кода. Исходный результат TEXT: три полноценных небольших файла по отдельности в чате, без монолитной генерации или вымышленных ссылок. Проверки через Node только если он реально доступен; иначе NOT RUN.

**Ссылки на два источника (оба проверены постановщиком):** CODE_REF = player5/SEKA_WEB, feature/crm034-ui-integrity-20261120 @ 30507c3fd17ffdb65640b47d6c2d4be048909377; DOCS_REF = player5/SEKA_WEB @ 17c4ab6f754a76f6ccb5dde408313d1e4b0ef4ae. В CODE_REF нет BASE/README.md, CURRENT/README.md и docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md; эти обязательные документы читать только на DOCS_REF. Проект WIP, не релиз. API v1: manifest.json, register(app), register_view. SQL DDL — только SEKA SQL Manager. Не менять sekamap, рабочий сервер/ПК, legacy Договоры, login min4, темы, чужие контракты, shared core/view_runtime/view_widgets/module_loader/manifest_validator/platform_api/static/index.html. Shared host меняет только CRM034 после независимого QA; без деплоя и merge. Перед кодом проверить старые реализации/тесты, поискать пригодное готовое GitHub решение, Issues, лицензии и безопасность, если доступ есть.

**Сдача:** точные source refs, собственные изменённые файлы/коммит или полный текст, исполняемые инструкции, новые и регрессионные тесты с фактическим stdout и PASS/FAIL/NOT RUN, независимые negative cases, незавершённое, риски/блокеры и NEXT. STATUS_EXECUTION COMPLETE/PARTIAL/BLOCKED по доказательствам. Worker не выдаёт себе независимый PASS.
