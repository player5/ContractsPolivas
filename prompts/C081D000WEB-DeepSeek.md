# C081D000WEB — Workspace Alpha: независимая система рабочих панелей

**Роль:** Worker (C). **Исполнитель:** DeepSeek. **Тип исходного результата:** TEXT в чате, все файлы целиком. **Статус:** PUBLISHED / NOT STARTED.
**Проект:** SEKA WEB UI/API First (альфа). **Продолжение действующего проекта:** CRM-UI-020.
**База для чтения и будущей интеграции:** `player5/SEKA_WEB@feature/crm034-ui-integrity-20261120:30507c3fd17ffdb65640b47d6c2d4be048909377`.
**Зависимости по транспорту:** 000 (самостоятельный исполнимый результат, интеграция CRM034 отдельно).

## Цель и законченный результат
Построить автономный переносимый Workspace с панелями и вкладками, перестановкой, изменением размеров, сохранением и восстановлением компоновки через переданный host-adapter. Это работающая библиотека для последующего CRM034, не переписывание SEKA WEB host.

## Самодостаточное техническое задание и вход
Поставить ванильный JS ES module, CSS и node:test. Вход createWorkspace(root,{moduleId,userContext,layout,onChange,onAction,storage}), результат setLayout/getLayout/dispose; layout={version:1,panels:[{id,title,x,y,w,h,visible,tabGroup?}],activeId?}. Идентификаторы ^[a-z][a-z0-9_-]{0,39}$, максимум 48 панелей, числовые координаты конечны. Storage состоит из load(key)/save(key,layout), ключ только из доверенных moduleId/userContext. Все DOM узлы через createElement/textContent, никакого innerHTML/eval и сетевых зависимостей. Действия и layout валидируются до применения. Не подключать чужой Desktop/Electron код.

## Строгий write_set
- `implementation/crm020/workspace_alpha/**`
Это **только** пути итоговых файлов в закрытом SEKA_WEB после доставки, никакого совместного host. Не менять старые примеры/код за пределами write_set. Вспомогательные tests/README/handoff размещать **внутри** названных owned directories.

## Критерии приёмки
1. Реально открывать/закрывать, перемещать, масштабировать и группировать панели во вкладки, переключать активную, сбрасывать и восстанавливать layout.
2. Изоляция module/user, отключённое storage = явный volatile mode, сохранение только через host callbacks, доступность управления с клавиатуры.
3. Тесты: roundtrip сериализации, invalid/duplicate ID, NaN/overflow, ошибка callback, действие после dispose, XSS title, два независимых workspace, отказ сохранения; браузер только при реальном запуске.
4. Полный исходный код workspace.js/css/test.js + README + интеграционный контракт/ошибки. Все файлы текстом в чате, без вымышленных ссылок.

## Доступ и передача DeepSeek
- Самостоятельное задание с **полным публичным техническим входом выше**. У DeepSeek нет подтверждённого GitHub/Drive или доступа к закрытому SEKA_WEB. **Полный исходный текст каждого файла выдавать непосредственно в чате**, без придуманного URL. Исходный тип результата — TEXT, сохраняется при совместимом переливе. GPT courier после отдельной проверки перенесёт код в закрытый репозиторий.
- Node.js stdlib test runner если доступен; если не доступен, отмечай NOT RUN. Не выдавать «работает в SEKA WEB» без реального host. Никаких сторонних импортов, секретов, приватного исходника или доступа к продуктовой БД.

## Проверки и передача результата
- Реально прогнать тесты новых функций и регрессий: invalid ID/payload/bounds; role 401/403; stale revision 409; unsafe HTML/script; race/retry/rollback; failing backend и перезапуск где применимо. В отчёте отдельные PASS/FAIL/NOT RUN с командами, средой и доказательствами. Не считать наличие тестового файла выполненным тестом. Если браузер/PG18 недоступен, писать NOT RUN.
- Результат: `CONTRACT | BASE_SHA | ITERATION/ATTEMPT | WRITE_SET | CHANGED_FILES | COMMITS/SOURCE_TEXT/DRIVE_FILE | TESTS_RUN | TESTS_NOT_RUN | FAILURES | BLOCKERS | NEXT | STATUS_EXECUTION`. STATUS_EXECUTION: COMPLETE/PARTIAL/BLOCKED. Worker self-audit ≠ independent Validator acceptance; интегратор CRM034, release/PG18 отдельно. Не добавлять транспортный BROWN_FINISH: Dispatcher добавляет сам.
