# C094D000WEB — Workspace: layout state engine

**Роль:** Worker. **Исполнитель:** DeepSeek. **Исходный тип результата:** TEXT source in chat. **Блокеры:** 000. **Статус:** PUBLISHED/NOT STARTED. **Продолжение CRM:** CRM-UI-020.

## Цель
Самостоятельный маленький JS layout model вместо переписывания 081: открытие/закрытие/resize/move/group/ungroup, безопасная сериализация. Не писать весь Workspace UI.

## Самодостаточное техническое задание
createLayoutState(initial)→get/open/close/move/resize/group/ungroup/serialize/dispose. JSON version1 panels≤48 {id,title,x,y,w,h,visible,group?}; id /^[a-z][a-z0-9_-]{0,39}$/, finite coordinates, no DOM/storage/network. Три полных файла layout.js, layout.test.js, README.md, текстом пофайлово.

## write_set
- `implementation/crm020/workspace_layout_alpha/**`
Любые новые tests/docs/handoff только в этих путях; остальные файлы read-only.

## Критерии и тесты
Node tests open/close/group/roundtrip, invalid IDs, bounds, disposed object; без тестовой среды NOT RUN; отсутствие unsafe HTML/eval; rollback на плохом layout.

**DeepSeek вход:** весь необходимый публичный контракт утилиты дан здесь, private GitHub/Drive не нужен. Не утверждай чтение кода. Исходный результат TEXT: три полноценных небольших файла по отдельности в чате, без монолитной генерации или вымышленных ссылок. Проверки через Node только если он реально доступен; иначе NOT RUN.

**Ссылки на два источника (оба проверены постановщиком):** CODE_REF = player5/SEKA_WEB, feature/crm034-ui-integrity-20261120 @ 30507c3fd17ffdb65640b47d6c2d4be048909377; DOCS_REF = player5/SEKA_WEB @ 17c4ab6f754a76f6ccb5dde408313d1e4b0ef4ae. В CODE_REF нет BASE/README.md, CURRENT/README.md и docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md; эти обязательные документы читать только на DOCS_REF. Проект WIP, не релиз. API v1: manifest.json, register(app), register_view. SQL DDL — только SEKA SQL Manager. Не менять sekamap, рабочий сервер/ПК, legacy Договоры, login min4, темы, чужие контракты, shared core/view_runtime/view_widgets/module_loader/manifest_validator/platform_api/static/index.html. Shared host меняет только CRM034 после независимого QA; без деплоя и merge. Перед кодом проверить старые реализации/тесты, поискать пригодное готовое GitHub решение, Issues, лицензии и безопасность, если доступ есть.

**Сдача:** точные source refs, собственные изменённые файлы/коммит или полный текст, исполняемые инструкции, новые и регрессионные тесты с фактическим stdout и PASS/FAIL/NOT RUN, независимые negative cases, незавершённое, риски/блокеры и NEXT. STATUS_EXECUTION COMPLETE/PARTIAL/BLOCKED по доказательствам. Worker не выдаёт себе независимый PASS.
