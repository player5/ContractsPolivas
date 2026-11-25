# C090C000WEB — CRM029: версии, права и безопасное хранение файлов

**Роль:** Worker (C). **Исполнитель:** ChatGPT. **Тип исходного результата:** Код и отчёты в закрытом GitHub SEKA_WEB, отдельная feature branch/PR. **Статус:** PUBLISHED / NOT STARTED.
**Проект:** SEKA WEB UI/API First (альфа). **Продолжение действующего проекта:** CRM-FILES-029.
**База для чтения и будущей интеграции:** `player5/SEKA_WEB@feature/crm034-ui-integrity-20261120:30507c3fd17ffdb65640b47d6c2d4be048909377`.
**Зависимости по транспорту:** 000 (самостоятельный исполнимый результат, интеграция CRM034 отдельно).

## Цель и законченный результат
Развить существующий CRM029 в переиспользуемый модульный file service с версиями, квотами, ACL, безопасной загрузкой и восстановлением. Не менять существующие маршруты host или делать файловый сервис универсальным SQL-blob store.

## Самодостаточное техническое задание и вход
Version ID + SHA256 content-addressed blobs, module/user/owner permission gates, quota, streaming bounded upload, download, listing/version history, soft delete/restore, optimistic ETag on write. Только disposable local storage for tests, portable single-root. SQL proposal отдельным handoff, SQL Manager пишет DDL.

## Строгий write_set
- `implementation/crm029/**`
- `tests/test_crm029_*`
- `docs/CRM-FILES-029_*`
Это **только** пути итоговых файлов в закрытом SEKA_WEB после доставки, никакого совместного host. Не менять старые примеры/код за пределами write_set. Вспомогательные tests/README/handoff размещать **внутри** названных owned directories.

## Критерии приёмки
1. Загрузка/получение версии, CRC/SHA, dedup, quotas, restore/tombstone и idempotent conflict.
2. Negative path traversal/symlink/invalid MIME/Unicode/broken checksum/oversize/user/other module; no secret/path leaks.
3. Interrupted upload cleanup, parallel update 409, broken storage failure, old upload/download regression.
4. Точный API для filePicker и handoff 034, real host/PG Not Run если недоступно.

## Работа с исходником и безопасность
- Закрытый проект: `player5/SEKA_WEB`. Только у реально подключённого GPT допускается чтение private GitHub; при отсутствии доступа не притворяться, передать BLOCKED/handoff. Ветка `feature/crm034-ui-integrity-20261120`, подтверждённый источник `30507c3fd17ffdb65640b47d6c2d4be048909377` (PR #28, Draft). При старте заново проверить фактический HEAD и файлы, не использовать main вместо runtime. Исторические CRM-контракты продолжаются, новый BROWN ID — только транспортная порция работ, не новый проект.
- Прочесть `BASE/README.md`, `CURRENT/README.md`, `docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md`, действующий целевой CRM-контракт, код/регрессионные тесты. Проверить GitHub repos/issues/discussions на готовое качество и лицензии (MIT/BSD и commercial-use отдельно), записать выбор до разработки.
- Локальная ветка от точного commit, только разрешённые файлы. Shared `core.py`, `view_runtime.py`, `view_widgets.py`, `module_loader.py`, `manifest_validator.py`, `platform_api.py`, `static/index.html` — read-only; изменения только в `integration_handoff.md` в разрешённом корне для CRM034.
- Никаких изменений закрытой рабочей базы `sekamap`, production, сервера/ПК, SQL DDL, других модулей и legacy Contracts, пароля (минимум 4), брендовых тем/favicon. Не менять API v1 без versioned opt-in; PG18 schema принадлежит только SQL Manager.
- Поэтапные записи WORKLOG (contract/iteration/attempt/source SHA/diff/tests/blockers/NEXT) в своей области, readback после commit, полный self-audit и result report.

## Проверки и передача результата
- Реально прогнать тесты новых функций и регрессий: invalid ID/payload/bounds; role 401/403; stale revision 409; unsafe HTML/script; race/retry/rollback; failing backend и перезапуск где применимо. В отчёте отдельные PASS/FAIL/NOT RUN с командами, средой и доказательствами. Не считать наличие тестового файла выполненным тестом. Если браузер/PG18 недоступен, писать NOT RUN.
- Результат: `CONTRACT | BASE_SHA | ITERATION/ATTEMPT | WRITE_SET | CHANGED_FILES | COMMITS/SOURCE_TEXT/DRIVE_FILE | TESTS_RUN | TESTS_NOT_RUN | FAILURES | BLOCKERS | NEXT | STATUS_EXECUTION`. STATUS_EXECUTION: COMPLETE/PARTIAL/BLOCKED. Worker self-audit ≠ independent Validator acceptance; интегратор CRM034, release/PG18 отдельно. Не добавлять транспортный BROWN_FINISH: Dispatcher добавляет сам.
