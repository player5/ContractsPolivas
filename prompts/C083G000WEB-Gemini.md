# C083G000WEB — DataTable Alpha: безопасные интерактивные таблицы

**Роль:** Worker (C). **Исполнитель:** Gemini. **Тип исходного результата:** ZIP на Google Drive с исходниками, тестами и handoff. **Статус:** PUBLISHED / NOT STARTED.
**Проект:** SEKA WEB UI/API First (альфа). **Продолжение действующего проекта:** CRM-UI-WIDGETS-027.
**База для чтения и будущей интеграции:** `player5/SEKA_WEB@feature/crm034-ui-integrity-20261120:30507c3fd17ffdb65640b47d6c2d4be048909377`.
**Зависимости по транспорту:** 000 (самостоятельный исполнимый результат, интеграция CRM034 отдельно).

## Цель и законченный результат
Сделать независимый переиспользуемый DataTable front-end adapter для schema API v1: серверная сортировка/фильтрация/пагинация, редактирование с ACK и откатом, selection/copy/paste/виртуализация. Общий host без изменений.

## Самодостаточное техническое задание и вход
Пакет на JavaScript ES module + CSS + tests + README + handoff. Самодостаточный публичный API mountDataTable(root,{id,columns,rows,page,pageSize,total,revision,dispatch,onError}); columns=[{key,label,editable?}], row={id,...}; events dispatch({event:'edit'|'select'|'sort'|'filter'|'page',revision,data:{componentId,rowId?,column?,value?,direction?,page?,filter?}}). ACK={ok:true,revision,view?}; rejects={ok:false,status:403|409|422|503,error}. Не хранить токен, не генерировать HTML строкой, не писать SQL. Таблица до 40 столбцов, в ответе до 500 строк, виртуализация/окно для больших массивов. Реальный host только через handoff, без доступа к закрытым исходникам.

## Строгий write_set
- `implementation/crm027/table_alpha/**`
Это **только** пути итоговых файлов в закрытом SEKA_WEB после доставки, никакого совместного host. Не менять старые примеры/код за пределами write_set. Вспомогательные tests/README/handoff размещать **внутри** названных owned directories.

## Критерии приёмки
1. Редактирование pending/ACK/reject, rollback, сохранение фокуса, запрет двойного submit.
2. Backend управляет sort/filter/page; выделение, копирование, вставка ограниченных значений и виртуальное отображение больших списков.
3. Node/browser доступные тесты 1k+ строк, 403/409, XSS, overflow, refresh state, сетевой reject; точные фактически запущенные тесты.
4. ZIP с исходниками и тестами на Google Drive; SHA256 и readback. Если загрузка/создание файла недоступны — BLOCKED, не фантазировать ссылку.

## Доступ и передача Gemini
- Самостоятельное задание с **полным публичным техническим входом выше**. У Gemini **нет гарантированного доступа к закрытому `player5/SEKA_WEB`**. Не пытаться читать приватный GitHub и не заявлять, что интеграция с host проверена. Поставить автономную исходную библиотеку с тем же API-соглашением; интеграцию делает GPT/CRM034.
- Исходный тип результата: **обычный ZIP-файл на Google Drive**, включающий все JS/CSS/tests/README/handoff, никаких нативных Google Docs вместо ZIP. В ZIP не должно быть секретов или закрытого кода. Пути внутри архива — точно разрешённый write_set; private repo меняет только GPT courier после проверки.
- **Строгий алгоритм Drive**: (1) сформировать реальные файлы и ZIP через инструмент файлов/кода; (2) проверить содержимое архива, тесты и SHA256; (3) загрузить готовый ZIP на Drive поддерживаемым способом, не создавать его как нативный документ; (4) если способ не удался, проверить отдельно создание и альтернативный upload/export; (5) проверить наличие ZIP повторным чтением/скачиванием, вернуть реальную ссылку и SHA. Не заменять чужие файлы и не менять доступ. Если разрешённые способы исчерпаны — BLOCKED, не выдумывать DONE.
- Без прямых host/core/DB mutations, без зависимости от стороннего CDN.

## Проверки и передача результата
- Реально прогнать тесты новых функций и регрессий: invalid ID/payload/bounds; role 401/403; stale revision 409; unsafe HTML/script; race/retry/rollback; failing backend и перезапуск где применимо. В отчёте отдельные PASS/FAIL/NOT RUN с командами, средой и доказательствами. Не считать наличие тестового файла выполненным тестом. Если браузер/PG18 недоступен, писать NOT RUN.
- Результат: `CONTRACT | BASE_SHA | ITERATION/ATTEMPT | WRITE_SET | CHANGED_FILES | COMMITS/SOURCE_TEXT/DRIVE_FILE | TESTS_RUN | TESTS_NOT_RUN | FAILURES | BLOCKERS | NEXT | STATUS_EXECUTION`. STATUS_EXECUTION: COMPLETE/PARTIAL/BLOCKED. Worker self-audit ≠ independent Validator acceptance; интегратор CRM034, release/PG18 отдельно. Не добавлять транспортный BROWN_FINISH: Dispatcher добавляет сам.
