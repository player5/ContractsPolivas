# BROWN SWARM — активная очередь

Dispatcher читает публичную таблицу. Только успешное чтение корректного INDEX определяет активные ID и сквозные номера. Отсутствие всех номеров блокеров разрешает выдачу зависимого задания. Ошибка чтения не считается пустой очередью. Получение ответа или BROWN_FINISH не снимает зависимость.

| Contract ID | Тип | Исполнитель | Карточка | Промпт | Состояние |
|---|---|---|---|---|---|
| **C094D000WEB** | C | DeepSeek | [C094D000WEB](contracts/C094D000WEB.md) | [Задание](prompts/C094D000WEB-DeepSeek.md) | PUBLISHED |
| **C095D000WEB** | C | DeepSeek | [C095D000WEB](contracts/C095D000WEB.md) | [Задание](prompts/C095D000WEB-DeepSeek.md) | PUBLISHED |
| **C096G000WEB** | C | Gemini | [C096G000WEB](contracts/C096G000WEB.md) | [Задание](prompts/C096G000WEB-Gemini.md) | PUBLISHED |
| **C097C000WEB** | C | ChatGPT | [C097C000WEB](contracts/C097C000WEB.md) | [Задание](prompts/C097C000WEB-ChatGPT.md) | PUBLISHED |
| **C098C000WEB** | C | ChatGPT | [C098C000WEB](contracts/C098C000WEB.md) | [Задание](prompts/C098C000WEB-ChatGPT.md) | PUBLISHED |
| **C099C000WEB** | C | ChatGPT | [C099C000WEB](contracts/C099C000WEB.md) | [Задание](prompts/C099C000WEB-ChatGPT.md) | PUBLISHED |
| **C100C000WEB** | C | ChatGPT | [C100C000WEB](contracts/C100C000WEB.md) | [Задание](prompts/C100C000WEB-ChatGPT.md) | PUBLISHED |
| **C101C000WEB** | C | ChatGPT | [C101C000WEB](contracts/C101C000WEB.md) | [Задание](prompts/C101C000WEB-ChatGPT.md) | PUBLISHED |
| **C104C000WEB** | C | ChatGPT | [C104C000WEB](contracts/C104C000WEB.md) | [Задание](prompts/C104C000WEB-ChatGPT.md) | PUBLISHED |
| **C105C000WEB** | C | ChatGPT | [C105C000WEB](contracts/C105C000WEB.md) | [Задание](prompts/C105C000WEB-ChatGPT.md) | PUBLISHED |
| **V106C094+095+096+097+098+099+100WEB** | V | ChatGPT | [V106C094+095+096+097+098+099+100WEB](contracts/V106C094+095+096+097+098+099+100WEB.md) | [Задание](prompts/V106C094+095+096+097+098+099+100WEB-ChatGPT.md) | PUBLISHED |
| **V107C101+102+103+104+105WEB** | V | ChatGPT | [V107C101+102+103+104+105WEB](contracts/V107C101+102+103+104+105WEB.md) | [Задание](prompts/V107C101+102+103+104+105WEB-ChatGPT.md) | PUBLISHED |

Порядок публикации: [CUTTER.md](CUTTER.md). Формат и резервирование номеров: [NUMBERING.md](NUMBERING.md). GPT убирает только строку подтверждённого сохранения/нахождения результата. Качество проверяет независимый Validator; Dispatcher не оценивает содержимое и не пишет в GitHub.
