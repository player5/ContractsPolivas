# BROWN SWARM — активная очередь

Dispatcher читает публичную таблицу. Только успешное чтение корректного INDEX определяет активные ID и сквозные номера. Отсутствие всех номеров блокеров разрешает выдачу зависимого задания. Ошибка чтения не считается пустой очередью. Получение ответа или BROWN_FINISH не снимает зависимость.

| Contract ID | Тип | Исполнитель | Карточка | Промпт | Состояние |
|---|---|---|---|---|---|
| **C081D000WEB** | C | DeepSeek | [C081D000WEB](contracts/C081D000WEB.md) | [Задание](prompts/C081D000WEB-DeepSeek.md) | PUBLISHED |
| **C082D000WEB** | C | DeepSeek | [C082D000WEB](contracts/C082D000WEB.md) | [Задание](prompts/C082D000WEB-DeepSeek.md) | PUBLISHED |
| **C083G000WEB** | C | Gemini | [C083G000WEB](contracts/C083G000WEB.md) | [Задание](prompts/C083G000WEB-Gemini.md) | PUBLISHED |
| **C084G000WEB** | C | Gemini | [C084G000WEB](contracts/C084G000WEB.md) | [Задание](prompts/C084G000WEB-Gemini.md) | PUBLISHED |
| **C085C000WEB** | C | ChatGPT | [C085C000WEB](contracts/C085C000WEB.md) | [Задание](prompts/C085C000WEB-ChatGPT.md) | PUBLISHED |
| **C086C000WEB** | C | ChatGPT | [C086C000WEB](contracts/C086C000WEB.md) | [Задание](prompts/C086C000WEB-ChatGPT.md) | PUBLISHED |
| **C087C000WEB** | C | ChatGPT | [C087C000WEB](contracts/C087C000WEB.md) | [Задание](prompts/C087C000WEB-ChatGPT.md) | PUBLISHED |
| **C088C000WEB** | C | ChatGPT | [C088C000WEB](contracts/C088C000WEB.md) | [Задание](prompts/C088C000WEB-ChatGPT.md) | PUBLISHED |
| **C089C000WEB** | C | ChatGPT | [C089C000WEB](contracts/C089C000WEB.md) | [Задание](prompts/C089C000WEB-ChatGPT.md) | PUBLISHED |
| **C090C000WEB** | C | ChatGPT | [C090C000WEB](contracts/C090C000WEB.md) | [Задание](prompts/C090C000WEB-ChatGPT.md) | PUBLISHED |
| **C091C000WEB** | C | ChatGPT | [C091C000WEB](contracts/C091C000WEB.md) | [Задание](prompts/C091C000WEB-ChatGPT.md) | PUBLISHED |
| **V092C081+082+083+084+085+086WEB** | V | ChatGPT | [V092C081+082+083+084+085+086WEB](contracts/V092C081+082+083+084+085+086WEB.md) | [Задание](prompts/V092C081+082+083+084+085+086WEB-ChatGPT.md) | PUBLISHED |
| **V093C087+088+089+090+091WEB** | V | ChatGPT | [V093C087+088+089+090+091WEB](contracts/V093C087+088+089+090+091WEB.md) | [Задание](prompts/V093C087+088+089+090+091WEB-ChatGPT.md) | PUBLISHED |

Порядок публикации: [CUTTER.md](CUTTER.md). Формат и резервирование номеров: [NUMBERING.md](NUMBERING.md). GPT убирает только строку подтверждённого сохранения/нахождения результата. Качество проверяет независимый Validator; Dispatcher не оценивает содержимое и не пишет в GitHub.
