# Индекс публичных контрактов BROWN SWARM

**Активные карточки: 1.** Неактивные шаблоны: 1.

| Contract ID | Тип | Исполнитель | Карточка | Промпт | Состояние |
|---|---|---|---|---|---|
| **C001D000TST** | C / тест | DeepSeek | [C001D000TST](contracts/C001D000TST.md) | [полный промпт](prompts/C001D000TST-DeepSeek.md) | PUBLISHED / attempt 3 / READY |
| **V002D001TST** | V / шаблон | ChatGPT | [V002D001TST](contracts/V002D001TST.md) | [полный промпт](prompts/V002D001TST-ChatGPT.md) | TEMPLATE / AUTO-DISPATCH DISABLED |

## Рабочая цепочка

`public card → model in Firefox → full answer capture → (DeepSeek only) Publisher prompt → public results file → DONE`

Если ответ не захвачен за 10 минут, Dispatcher автоматически повторяет отправку с новым внутренним Command ID. Повторяется каждые 10 минут до получения ответа. Номер опубликованной карточки не требуется менять для транспортного повтора.

Publisher — промпт, не отдельная программа. После подтверждённой записи и readback Publisher возвращает `BROWN_STATUS|<CONTRACT_ID>|DONE`. Отдельный Validator в стандартном цикле не запускается.

Исторические исправления ID: [history/pilot-id-correction-2026-11-21](history/pilot-id-correction-2026-11-21/).
