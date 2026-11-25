# C088C000WEB — Record API Alpha: универсальный транзакционный CRUD

**Роль:** Worker (C). **Исполнитель:** ChatGPT. **Тип исходного результата:** Код и отчёты в закрытом GitHub SEKA_WEB, отдельная feature branch/PR. **Статус:** PUBLISHED / NOT STARTED.
**Проект:** SEKA WEB UI/API First (альфа). **Продолжение действующего проекта:** CRM-UI-020 / CRM-INTEGRATOR-034.
**База для чтения и будущей интеграции:** `player5/SEKA_WEB@feature/crm034-ui-integrity-20261120:30507c3fd17ffdb65640b47d6c2d4be048909377`.
**Зависимости по транспорту:** 000 (самостоятельный исполнимый результат, интеграция CRM034 отдельно).

## Цель и законченный результат
Отдельный универсальный record/model сервис List/Form для модулей, пригодный для Frappe-подобного CRUD без host special cases. До одобренной миграции работает с disposable SQLite adapter; PostgreSQL sekamap не трогать.

## Самодостаточное техническое задание и вход
Model metadata: types, fields, required/read-only, filters/sorts/page, namespace, schemaVersion. CRUD create/get/list/update/delete; optimistic revision/CAS; commit-before-ACK, transactional tests; inject guard (module,user,record,field,operation) и fail-closed без него. Только предложения DDL для SQL Manager.

## Строгий write_set
- `implementation/crm020/records_alpha/**`
- `tests/test_crm020_records_alpha_*`
- `docs/CRM020_RECORDS_ALPHA_*`
Это **только** пути итоговых файлов в закрытом SEKA_WEB после доставки, никакого совместного host. Не менять старые примеры/код за пределами write_set. Вспомогательные tests/README/handoff размещать **внутри** названных owned directories.

## Критерии приёмки
1. CRUD + pagination/filter/sort, persisted test records after restart SQLite, transaction rollback on disk/error.
2. 403/409/422/413 and row/field denies both reads/writes; no raw SQL from client and no leaks.
3. Concurrency and stale revision tests, schema validation and old module regressions, zero DDL on real PG.
4. Handoff с точным adapter API для CRM028/CRM034.

## Работа с исходником и безопасность
- Закрытый проект: `player5/SEKA_WEB`. Только у реально подключённого GPT допускается чтение private GitHub; при отсутствии доступа не притворяться, передать BLOCKED/handoff. Ветка `feature/crm034-ui-integrity-20261120`, подтверждённый источник `30507c3fd17ffdb65640b47d6c2d4be048909377` (PR #28, Draft). При старте заново проверить фактический HEAD и файлы, не использовать main вместо runtime. Исторические CRM-контракты продолжаются, новый BROWN ID — только транспортная порция работ, не новый проект.
- Прочесть `BASE/README.md`, `CURRENT/README.md`, `docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md`, действующий целевой CRM-контракт, код/регрессионные тесты. Проверить GitHub repos/issues/discussions на готовое качество и лицензии (MIT/BSD и commercial-use отдельно), записать выбор до разработки.
- Локальная ветка от точного commit, только разрешённые файлы. Shared `core.py`, `view_runtime.py`, `view_widgets.py`, `module_loader.py`, `manifest_validator.py`, `platform_api.py`, `static/index.html` — read-only; изменения только в `integration_handoff.md` в разрешённом корне для CRM034.
- Никаких изменений закрытой рабочей базы `sekamap`, production, сервера/ПК, SQL DDL, других модулей и legacy Contracts, пароля (минимум 4), брендовых тем/favicon. Не менять API v1 без versioned opt-in; PG18 schema принадлежит только SQL Manager.
- Поэтапные записи WORKLOG (contract/iteration/attempt/source SHA/diff/tests/blockers/NEXT) в своей области, readback после commit, полный self-audit и result report.

## Проверки и передача результата
- Реально прогнать тесты новых функций и регрессий: invalid ID/payload/bounds; role 401/403; stale revision 409; unsafe HTML/script; race/retry/rollback; failing backend и перезапуск где применимо. В отчёте отдельные PASS/FAIL/NOT RUN с командами, средой и доказательствами. Не считать наличие тестового файла выполненным тестом. Если браузер/PG18 недоступен, писать NOT RUN.
- Результат: `CONTRACT | BASE_SHA | ITERATION/ATTEMPT | WRITE_SET | CHANGED_FILES | COMMITS/SOURCE_TEXT/DRIVE_FILE | TESTS_RUN | TESTS_NOT_RUN | FAILURES | BLOCKERS | NEXT | STATUS_EXECUTION`. STATUS_EXECUTION: COMPLETE/PARTIAL/BLOCKED. Worker self-audit ≠ independent Validator acceptance; интегратор CRM034, release/PG18 отдельно. Не добавлять транспортный BROWN_FINISH: Dispatcher добавляет сам.
