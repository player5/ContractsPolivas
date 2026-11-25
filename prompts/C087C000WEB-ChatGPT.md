# C087C000WEB — Interop CRM036: реестр и безопасный шлюз сервисов

**Роль:** Worker (C). **Исполнитель:** ChatGPT. **Тип исходного результата:** Код и отчёты в закрытом GitHub SEKA_WEB, отдельная feature branch/PR. **Статус:** PUBLISHED / NOT STARTED.
**Проект:** SEKA WEB UI/API First (альфа). **Продолжение действующего проекта:** CRM-MODULE-INTEROP-036.
**База для чтения и будущей интеграции:** `player5/SEKA_WEB@feature/crm034-ui-integrity-20261120:30507c3fd17ffdb65640b47d6c2d4be048909377`.
**Зависимости по транспорту:** 000 (самостоятельный исполнимый результат, интеграция CRM034 отдельно).

## Цель и законченный результат
Создать изолированный версионированный gateway для вызовов сервисов между модулями по CRM036, без прямого импорта чужого backend, без подделки роли вызывающего и без новой шины задач.

## Самодостаточное техническое задание и вход
Trusted service descriptor provider/service/version/capability/request/response schema/deadline/idempotency; enabled state, generation on update, caller allowlist (caller,provider,service,version), CRM028 PermissionService adapter обязателен. Нет adapter => fail closed. Host hooks только через integration_handoff, no public endpoint by default.

## Строгий write_set
- `implementation/crm036/**`
- `tests/test_crm036_*`
- `docs/CRM-MODULE-INTEROP-036_*`
Это **только** пути итоговых файлов в закрытом SEKA_WEB после доставки, никакого совместного host. Не менять старые примеры/код за пределами write_set. Вспомогательные tests/README/handoff размещать **внутри** названных owned directories.

## Критерии приёмки
1. Рабочие provider/consumer fixtures и запрещённый consumer; schema validation both directions, bounded timeout/payload/concurrency.
2. Negative tests caller impersonation, foreign namespace, stale generation, invalid response, missing ACL adapter, recursion, leaking secrets.
3. Errors 403/404/409/413/422/429/502/503/504, безопасные audit fields.
4. Не переписывать CRM019 event bus/CRM030 IPC; host/real PG E2E NOT RUN до 034/028 интеграции.

## Работа с исходником и безопасность
- Закрытый проект: `player5/SEKA_WEB`. Только у реально подключённого GPT допускается чтение private GitHub; при отсутствии доступа не притворяться, передать BLOCKED/handoff. Ветка `feature/crm034-ui-integrity-20261120`, подтверждённый источник `30507c3fd17ffdb65640b47d6c2d4be048909377` (PR #28, Draft). При старте заново проверить фактический HEAD и файлы, не использовать main вместо runtime. Исторические CRM-контракты продолжаются, новый BROWN ID — только транспортная порция работ, не новый проект.
- Прочесть `BASE/README.md`, `CURRENT/README.md`, `docs/SEKA_UI_API_FIRST_DECISION_2026-11-23.md`, действующий целевой CRM-контракт, код/регрессионные тесты. Проверить GitHub repos/issues/discussions на готовое качество и лицензии (MIT/BSD и commercial-use отдельно), записать выбор до разработки.
- Локальная ветка от точного commit, только разрешённые файлы. Shared `core.py`, `view_runtime.py`, `view_widgets.py`, `module_loader.py`, `manifest_validator.py`, `platform_api.py`, `static/index.html` — read-only; изменения только в `integration_handoff.md` в разрешённом корне для CRM034.
- Никаких изменений закрытой рабочей базы `sekamap`, production, сервера/ПК, SQL DDL, других модулей и legacy Contracts, пароля (минимум 4), брендовых тем/favicon. Не менять API v1 без versioned opt-in; PG18 schema принадлежит только SQL Manager.
- Поэтапные записи WORKLOG (contract/iteration/attempt/source SHA/diff/tests/blockers/NEXT) в своей области, readback после commit, полный self-audit и result report.

## Проверки и передача результата
- Реально прогнать тесты новых функций и регрессий: invalid ID/payload/bounds; role 401/403; stale revision 409; unsafe HTML/script; race/retry/rollback; failing backend и перезапуск где применимо. В отчёте отдельные PASS/FAIL/NOT RUN с командами, средой и доказательствами. Не считать наличие тестового файла выполненным тестом. Если браузер/PG18 недоступен, писать NOT RUN.
- Результат: `CONTRACT | BASE_SHA | ITERATION/ATTEMPT | WRITE_SET | CHANGED_FILES | COMMITS/SOURCE_TEXT/DRIVE_FILE | TESTS_RUN | TESTS_NOT_RUN | FAILURES | BLOCKERS | NEXT | STATUS_EXECUTION`. STATUS_EXECUTION: COMPLETE/PARTIAL/BLOCKED. Worker self-audit ≠ independent Validator acceptance; интегратор CRM034, release/PG18 отдельно. Не добавлять транспортный BROWN_FINISH: Dispatcher добавляет сам.
