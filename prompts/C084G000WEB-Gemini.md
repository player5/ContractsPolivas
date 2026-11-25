# C084G000WEB — Form/Dialog Alpha: сложные формы и подтверждаемые операции

**Роль:** Worker (C). **Исполнитель:** Gemini. **Тип исходного результата:** ZIP на Google Drive с исходниками, тестами и handoff. **Статус:** PUBLISHED / NOT STARTED.
**Проект:** SEKA WEB UI/API First (альфа). **Продолжение действующего проекта:** CRM-UI-020 / CRM-UI-WIDGETS-027.
**База для чтения и будущей интеграции:** `player5/SEKA_WEB@feature/crm034-ui-integrity-20261120:30507c3fd17ffdb65640b47d6c2d4be048909377`.
**Зависимости по транспорту:** 000 (самостоятельный исполнимый результат, интеграция CRM034 отдельно).

## Цель и законченный результат
Сделать независимый адаптер форм и диалогов с валидацией, зависимыми полями и серверным ACK, сохраняя совместимость с data-only schema v1. Код готовится вне закрытого SEKA WEB, host интеграция отдельная.

## Самодостаточное техническое задание и вход
Пакет JS ES module + CSS + tests + README + handoff. API mountForm(root,{id,revision,fields,actions,dispatch,onError}); поля {id,type:'field'|'select'|'radio'|'slider'|'spinbox',label,value,required?,maxLength?,visibleWhen?:{field,equals}}, actions={id,label,event,confirm?}. Допускать visibleWhen только у field внутри form/dialog, зависимость от безусловного контроллера того же form, без eval. Кнопка save вызывает dispatch({event,revision,data:{componentId,values}}), ACK={ok:true,revision,view?}; отказ статус 403|409|422|503. Не передавать скрытые поля, не использовать HTML-исполнение, не менять host и его валидаторы.

## Строгий write_set
- `implementation/crm027/form_alpha/**`
Это **только** пути итоговых файлов в закрытом SEKA_WEB после доставки, никакого совместного host. Не менять старые примеры/код за пределами write_set. Вспомогательные tests/README/handoff размещать **внутри** названных owned directories.

## Критерии приёмки
1. Условная видимость, обязательные/типизированные поля, field errors, при отмене откат dirty state, повторное открытие не сбрасывает подтверждённые значения.
2. Проверка до submit и на стороне backend callback (демо), 403/409/422 не показывают успех; подтверждение опасных действий, клавиатура и восстановление фокуса.
3. Тесты: malformed values, hidden field omission, XSS, limit, stale revision, duplicate clicks, close/reopen; доступные браузерные проверки отдельно.
4. ZIP с исходниками, тестами и README на Google Drive, verified readback и SHA256; при отсутствии доступного создания/загрузки BLOCKED.

## Доступ и передача Gemini
- Самостоятельное задание с **полным публичным техническим входом выше**. У Gemini **нет гарантированного доступа к закрытому `player5/SEKA_WEB`**. Не пытаться читать приватный GitHub и не заявлять, что интеграция с host проверена. Поставить автономную исходную библиотеку с тем же API-соглашением; интеграцию делает GPT/CRM034.
- Исходный тип результата: **обычный ZIP-файл на Google Drive**, включающий все JS/CSS/tests/README/handoff, никаких нативных Google Docs вместо ZIP. В ZIP не должно быть секретов или закрытого кода. Пути внутри архива — точно разрешённый write_set; private repo меняет только GPT courier после проверки.
- **Строгий алгоритм Drive**: (1) сформировать реальные файлы и ZIP через инструмент файлов/кода; (2) проверить содержимое архива, тесты и SHA256; (3) загрузить готовый ZIP на Drive поддерживаемым способом, не создавать его как нативный документ; (4) если способ не удался, проверить отдельно создание и альтернативный upload/export; (5) проверить наличие ZIP повторным чтением/скачиванием, вернуть реальную ссылку и SHA. Не заменять чужие файлы и не менять доступ. Если разрешённые способы исчерпаны — BLOCKED, не выдумывать DONE.
- Без прямых host/core/DB mutations, без зависимости от стороннего CDN.

## Проверки и передача результата
- Реально прогнать тесты новых функций и регрессий: invalid ID/payload/bounds; role 401/403; stale revision 409; unsafe HTML/script; race/retry/rollback; failing backend и перезапуск где применимо. В отчёте отдельные PASS/FAIL/NOT RUN с командами, средой и доказательствами. Не считать наличие тестового файла выполненным тестом. Если браузер/PG18 недоступен, писать NOT RUN.
- Результат: `CONTRACT | BASE_SHA | ITERATION/ATTEMPT | WRITE_SET | CHANGED_FILES | COMMITS/SOURCE_TEXT/DRIVE_FILE | TESTS_RUN | TESTS_NOT_RUN | FAILURES | BLOCKERS | NEXT | STATUS_EXECUTION`. STATUS_EXECUTION: COMPLETE/PARTIAL/BLOCKED. Worker self-audit ≠ independent Validator acceptance; интегратор CRM034, release/PG18 отдельно. Не добавлять транспортный BROWN_FINISH: Dispatcher добавляет сам.
