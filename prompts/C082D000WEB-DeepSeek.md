# C082D000WEB — Tree Alpha: универсальное ленивое дерево с подтверждением изменений

**Роль:** Worker (C). **Исполнитель:** DeepSeek. **Тип исходного результата:** TEXT в чате, все файлы целиком. **Статус:** PUBLISHED / NOT STARTED.
**Проект:** SEKA WEB UI/API First (альфа). **Продолжение действующего проекта:** CRM-UI-WIDGETS-027.
**База для чтения и будущей интеграции:** `player5/SEKA_WEB@feature/crm034-ui-integrity-20261120:30507c3fd17ffdb65640b47d6c2d4be048909377`.
**Зависимости по транспорту:** 000 (самостоятельный исполнимый результат, интеграция CRM034 отдельно).

## Цель и законченный результат
Создать самостоятельный UI Tree adapter с безопасным lazy-fetch, выбором, контекстными операциями и перемещением узлов. Host интеграция через публичные callbacks; существующее дерево CRM027 не менять.

## Самодостаточное техническое задание и вход
Ванильный JS ES module tree.js, CSS и node:test. API createTree(root,{nodes,revision,fetchChildren,dispatch,onError}) -> setState/getState/dispose. Node={id,label,hasChildren?,children?}, ID /^[a-z][a-z0-9_-]{0,39}$/, глубина ≤32, лимит на порцию 500 узлов. События dispatch({event,revision,data}) типов expand/select/context/move; move data={nodeId,parentId?,targetParentId?,direction:'up'|'down'|'reparent'}; сервер может вернуть {ok:true,revision,viewOrNodes} или reject {ok:false,status,error}. Не считать произвольный клиентский reorder подтверждённым. Строить DOM через textContent. Backend callback авторитетен; пересечения с host только handoff.

## Строгий write_set
- `implementation/crm027/tree_alpha/**`
Это **только** пути итоговых файлов в закрытом SEKA_WEB после доставки, никакого совместного host. Не менять старые примеры/код за пределами write_set. Вспомогательные tests/README/handoff размещать **внутри** названных owned directories.

## Критерии приёмки
1. Lazy child load/expand/collapse, выбранный/раскрытый узел, контекстная команда, reorder и reparent с проверкой циклов и допустимости destination.
2. Optimistic UI при move откатывается при 403/409/422/503, повторное событие bounded, выбранное состояние не теряется при обновлении.
3. Тесты на 500+ узлов, цикл, отсутствующего родителя, двойные IDs, XSS label, устаревшую revision, 2 независимых экземпляра, ошибку fetch и повторную подгрузку.
4. Полный текст tree.js/css/test.js/README/handoff в чате, без заявлений о тесте на недоступном host.

## Доступ и передача DeepSeek
- Самостоятельное задание с **полным публичным техническим входом выше**. У DeepSeek нет подтверждённого GitHub/Drive или доступа к закрытому SEKA_WEB. **Полный исходный текст каждого файла выдавать непосредственно в чате**, без придуманного URL. Исходный тип результата — TEXT, сохраняется при совместимом переливе. GPT courier после отдельной проверки перенесёт код в закрытый репозиторий.
- Node.js stdlib test runner если доступен; если не доступен, отмечай NOT RUN. Не выдавать «работает в SEKA WEB» без реального host. Никаких сторонних импортов, секретов, приватного исходника или доступа к продуктовой БД.

## Проверки и передача результата
- Реально прогнать тесты новых функций и регрессий: invalid ID/payload/bounds; role 401/403; stale revision 409; unsafe HTML/script; race/retry/rollback; failing backend и перезапуск где применимо. В отчёте отдельные PASS/FAIL/NOT RUN с командами, средой и доказательствами. Не считать наличие тестового файла выполненным тестом. Если браузер/PG18 недоступен, писать NOT RUN.
- Результат: `CONTRACT | BASE_SHA | ITERATION/ATTEMPT | WRITE_SET | CHANGED_FILES | COMMITS/SOURCE_TEXT/DRIVE_FILE | TESTS_RUN | TESTS_NOT_RUN | FAILURES | BLOCKERS | NEXT | STATUS_EXECUTION`. STATUS_EXECUTION: COMPLETE/PARTIAL/BLOCKED. Worker self-audit ≠ independent Validator acceptance; интегратор CRM034, release/PG18 отдельно. Не добавлять транспортный BROWN_FINISH: Dispatcher добавляет сам.
