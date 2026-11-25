# C096G000WEB — DataTable: state controller для backend ACK

**Роль:** Worker. **Исполнитель:** Gemini. **Исходный тип результата:** TEXT source in chat. **Блокеры:** 000. **Статус:** PUBLISHED/NOT STARTED. **Продолжение CRM:** CRM-UI-WIDGETS-027.

## Цель
Не повторять прежний полный Table 083 и существующий UI renderer. Сделать только reusable state controller сортировки, фильтра, страниц и inline edit.

## Самодостаточное техническое задание
ES module createTableState(initial,{dispatch})→getState/requestSort/requestFilter/requestPage/editCell/dispose. Initial {revision,columns,rows,page,pageSize,total}, event {event,revision,data}, server {ok,revision,rows?,page?,total?}. Pending edit отдельно от confirmed; ACK advance required, 403/409/422/503 rollback; no DOM/SQL. Полные короткие table_state.js/table_state.test.js/README.md текстом в чате, без ZIP.

## write_set
- `implementation/crm027/table_state_alpha/**`
Любые новые tests/docs/handoff только в этих путях; остальные файлы read-only.

## Критерии и тесты
Node tests filter/sort/page, concurrent/stale edit, rollback, Unicode, invalid columns, payload limit32KiB; no fake browser PASS.

**Gemini вход:** весь необходимый публичный контракт дан здесь; private GitHub не нужен. Результат TEXT в чате, три коротких полных исходных файла; обычный файл/ZIP на Drive данным заданием не требуется, потому что у предыдущего Gemini ZIP upload был BLOCKED. Если всё-таки создаёшь обычный файл для Drive, действуй в строгом порядке: создать реальный файл инструментом кода/файлов, проверить данные/SHA, загрузить именно файл на Drive (не нативный Google Doc вместо ZIP/TXT), при ошибке испытать раздельные create и upload/export, проверить readback и действительную ссылку, иначе сообщить BLOCKED. Чужие файлы/права не менять.

**Ссылки на два источника (оба проверены постановщиком):** CODE_REF = player5/SEKA_WEB, feature/crm034-ui-integrity-20261120 @ 30507c3fd17ffdb65640b47d6c2d4be048909377; DOCS_REF = player5/SEKA_WEB @ 17c4ab6f754a76f6ccb5dde408313d1e4b0ef4ae. В CODE_REF нет BASE/README.md, CURRENT/README.md и docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md; эти обязательные документы читать только на DOCS_REF. Проект WIP, не релиз. API v1: manifest.json, register(app), register_view. SQL DDL — только SEKA SQL Manager. Не менять sekamap, рабочий сервер/ПК, legacy Договоры, login min4, темы, чужие контракты, shared core/view_runtime/view_widgets/module_loader/manifest_validator/platform_api/static/index.html. Shared host меняет только CRM034 после независимого QA; без деплоя и merge. Перед кодом проверить старые реализации/тесты, поискать пригодное готовое GitHub решение, Issues, лицензии и безопасность, если доступ есть.

**Сдача:** точные source refs, собственные изменённые файлы/коммит или полный текст, исполняемые инструкции, новые и регрессионные тесты с фактическим stdout и PASS/FAIL/NOT RUN, независимые negative cases, незавершённое, риски/блокеры и NEXT. STATUS_EXECUTION COMPLETE/PARTIAL/BLOCKED по доказательствам. Worker не выдаёт себе независимый PASS.
