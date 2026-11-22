# Индекс публичных контрактов BROWN SWARM

Публичные карточки: **2**. Автоматическая отправка готовых карточек включена в Dispatcher v0.7.8; фактические отправки и ответы пока NOT RUN.

| Contract ID | Тип | Исполнитель | Карточка | Промпт | Состояние |
|---|---|---|---|---|---|
| **C001D000TST** | C / тест | DeepSeek | [C001D000TST](contracts/C001D000TST.md) | [полный промпт](prompts/C001D000TST-DeepSeek.md) | PUBLISHED / attempt 3 / READY |
| **V002D001TST** | V / независимая проверка | ChatGPT | [V002D001TST](contracts/V002D001TST.md) | [полный промпт](prompts/V002D001TST-ChatGPT.md) | WAITING_FOR_C001D000TST |

## Цепочка

C001 отправляется в DeepSeek. После полного захвата Dispatcher автоматически отправляет Publisher-промпт в ChatGPT. Publisher сохраняет оригинал в публичный файл `results/<DELIVERY_ID>.txt`. Через 120 секунд зависимая карточка V002 автоматически отправляется в ChatGPT с динамическими ID и SHA исходного результата.

**Важно:** PUBLISHED ≠ DISPATCHED; SEND_CLICKED ≠ RESULT_CAPTURED; 120-секундный таймер ≠ FILE_READBACK; PASS выставляется только по реальным доказательствам.

Исторические ошибочные ID C0001/V0002 сохранены в [history/pilot-id-correction-2026-11-21](history/pilot-id-correction-2026-11-21/).
