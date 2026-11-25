# C089C000WEB — CRM028: объектные и полевые ACL, права модулей

**Роль:** Worker (C). **Исполнитель:** ChatGPT. **Тип исходного результата:** Код и отчёты в закрытом GitHub SEKA_WEB, отдельная feature branch/PR. **Статус:** PUBLISHED / NOT STARTED.
**Проект:** SEKA WEB UI/API First (альфа). **Продолжение действующего проекта:** CRM-PERMISSIONS-SETTINGS-028.
**База для чтения и будущей интеграции:** `player5/SEKA_WEB@feature/crm034-ui-integrity-20261120:30507c3fd17ffdb65640b47d6c2d4be048909377`.
**Зависимости по транспорту:** 000 (самостоятельный исполнимый результат, интеграция CRM034 отдельно).

## Цель и законченный результат
Довести PermissionService CRM028 до реального fail-closed контроля capability, роли, объекта и поля, не изменяя core/auth/базу пользователей.

## Самодостаточное техническое задание и вход
Сохранить existing API allowed/require при наличии, declared capability/roles, object grants+denies, field permissions, deny-overrides-allow, caller namespace identity. UI скрытие не считается проверкой. Для 036 межмодульный вызов разрешать только explicit host delegation, не фальсифицировать module_caller. SQL Manager отдельно владеет DDL.

## Строгий write_set
- `implementation/crm028/**`
- `tests/test_crm028_*`
- `docs/CRM-PERMISSIONS-SETTINGS-028_*`
Это **только** пути итоговых файлов в закрытом SEKA_WEB после доставки, никакого совместного host. Не менять старые примеры/код за пределами write_set. Вспомогательные tests/README/handoff размещать **внутри** названных owned directories.

## Критерии приёмки
1. Owner/role/object/field read/write/admin ограничения, reject неизвестной capability и отключённого модуля.
2. Негативные direct API + list/export/field, cross user/module, bogus caller, admin undeclared permission.
3. Стабильные 401/403/409, отказ при недоступном backend, audit only sanitized.
4. Regression existing auth/password minimum 4, independent handoff CRM034 and crosslink 036/records.

## Работа с исходником и безопасность
- Закрытый проект: `player5/SEKA_WEB`. Только у реально подключённого GPT допускается чтение private GitHub; при отсутствии доступа не притворяться, передать BLOCKED/handoff. Ветка `feature/crm034-ui-integrity-20261120`, подтверждённый источник `30507c3fd17ffdb65640b47d6c2d4be048909377` (PR #28, Draft). При старте заново проверить фактический HEAD и файлы, не использовать main вместо runtime. Исторические CRM-контракты продолжаются, новый BROWN ID — только транспортная порция работ, не новый проект.
- Прочесть `BASE/README.md`, `CURRENT/README.md`, `docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md`, действующий целевой CRM-контракт, код/регрессионные тесты. Проверить GitHub repos/issues/discussions на готовое качество и лицензии (MIT/BSD и commercial-use отдельно), записать выбор до разработки.
- Локальная ветка от точного commit, только разрешённые файлы. Shared `core.py`, `view_runtime.py`, `view_widgets.py`, `module_loader.py`, `manifest_validator.py`, `platform_api.py`, `static/index.html` — read-only; изменения только в `integration_handoff.md` в разрешённом корне для CRM034.
- Никаких изменений закрытой рабочей базы `sekamap`, production, сервера/ПК, SQL DDL, других модулей и legacy Contracts, пароля (минимум 4), брендовых тем/favicon. Не менять API v1 без versioned opt-in; PG18 schema принадлежит только SQL Manager.
- Поэтапные записи WORKLOG (contract/iteration/attempt/source SHA/diff/tests/blockers/NEXT) в своей области, readback после commit, полный self-audit и result report.

## Проверки и передача результата
- Реально прогнать тесты новых функций и регрессий: invalid ID/payload/bounds; role 401/403; stale revision 409; unsafe HTML/script; race/retry/rollback; failing backend и перезапуск где применимо. В отчёте отдельные PASS/FAIL/NOT RUN с командами, средой и доказательствами. Не считать наличие тестового файла выполненным тестом. Если браузер/PG18 недоступен, писать NOT RUN.
- Результат: `CONTRACT | BASE_SHA | ITERATION/ATTEMPT | WRITE_SET | CHANGED_FILES | COMMITS/SOURCE_TEXT/DRIVE_FILE | TESTS_RUN | TESTS_NOT_RUN | FAILURES | BLOCKERS | NEXT | STATUS_EXECUTION`. STATUS_EXECUTION: COMPLETE/PARTIAL/BLOCKED. Worker self-audit ≠ independent Validator acceptance; интегратор CRM034, release/PG18 отдельно. Не добавлять транспортный BROWN_FINISH: Dispatcher добавляет сам.
