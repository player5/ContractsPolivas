# BROWN SWARM — активная очередь

Dispatcher читает публичную таблицу. Только успешное чтение корректного INDEX определяет активные ID и сквозные номера. Отсутствие всех номеров блокеров разрешает выдачу зависимого задания. Ошибка чтения не считается пустой очередью. Получение ответа или BROWN_FINISH не снимает зависимость.

| Contract ID | Тип | Исполнитель | Карточка | Промпт | Состояние |
|---|---|---|---|---|---|

Порядок публикации: [CUTTER.md](CUTTER.md). Формат и резервирование номеров: [NUMBERING.md](NUMBERING.md). GPT убирает только строку подтверждённого сохранения/нахождения результата. Качество проверяет независимый Validator; Dispatcher не оценивает содержимое и не пишет в GitHub.
| **C068C000WEB** | Worker | ChatGPT | [карточка](contracts/C068C000WEB.md) | [промпт](prompts/C068C000WEB-C.md) | PUBLISHED |
| **C069C000WEB** | Worker | ChatGPT | [карточка](contracts/C069C000WEB.md) | [промпт](prompts/C069C000WEB-C.md) | PUBLISHED |
| **C070C000WEB** | Worker | ChatGPT | [карточка](contracts/C070C000WEB.md) | [промпт](prompts/C070C000WEB-C.md) | PUBLISHED |
| **C071C000WEB** | Worker | ChatGPT | [карточка](contracts/C071C000WEB.md) | [промпт](prompts/C071C000WEB-C.md) | PUBLISHED |
| **C072D000WEB** | Worker | DeepSeek | [карточка](contracts/C072D000WEB.md) | [промпт](prompts/C072D000WEB-D.md) | PUBLISHED |
| **C073C000WEB** | Worker | ChatGPT | [карточка](contracts/C073C000WEB.md) | [промпт](prompts/C073C000WEB-C.md) | PUBLISHED |
| **C074C000WEB** | Worker | ChatGPT | [карточка](contracts/C074C000WEB.md) | [промпт](prompts/C074C000WEB-C.md) | PUBLISHED |
| **C075C000WEB** | Worker | ChatGPT | [карточка](contracts/C075C000WEB.md) | [промпт](prompts/C075C000WEB-C.md) | PUBLISHED |
| **C076C000WEB** | Worker | ChatGPT | [карточка](contracts/C076C000WEB.md) | [промпт](prompts/C076C000WEB-C.md) | PUBLISHED |
| **C077C000WEB** | Worker | ChatGPT | [карточка](contracts/C077C000WEB.md) | [промпт](prompts/C077C000WEB-C.md) | PUBLISHED |
| **C078C000WEB** | Worker | ChatGPT | [карточка](contracts/C078C000WEB.md) | [промпт](prompts/C078C000WEB-C.md) | PUBLISHED |
| **V079C068+069+070+071+072+073WEB** | Validator | ChatGPT | [карточка](contracts/V079C068+069+070+071+072+073WEB.md) | [промпт](prompts/V079C068+069+070+071+072+073WEB-C.md) | PUBLISHED |
| **V080C074+075+076+077+078WEB** | Validator | ChatGPT | [карточка](contracts/V080C074+075+076+077+078WEB.md) | [промпт](prompts/V080C074+075+076+077+078WEB-C.md) | PUBLISHED |
