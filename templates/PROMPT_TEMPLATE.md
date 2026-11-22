# <CONTRACT_ID> — <PROVIDER> — публичный промпт

**TEMPLATE / NOT ASSIGNED.** Публиковать только после проверки безопасности текста и всех приложенных файлов.

ROLE: <ROLE>
CONTRACT_ID: <CONTRACT_ID>
REVISION: <REVISION>
ITERATION: <ITERATION>
ATTEMPT: <ATTEMPT>
MODE: <READ_ONLY|CODE_CHANGE>
EXECUTOR: <DeepSeek|ChatGPT|Gemini>
CAPABILITY_PROFILE: <TEXT_WORKER_V1|CONNECTOR_WORKER_V1>
REQUIRED_CAPABILITIES: <none|github|drive|github,drive>
SELF_CONTAINED: <true|false>

## Задание

<Полный точный текст задания. Не оставляйте обязательные части за ссылками, если executor не имеет нужного коннектора.>

## Источники и файлы

- DeepSeek: вставьте исходники прямо в этот промпт или подготовьте текстовый SHA-pinned files_manifest. Не рассчитывайте на GitHub/Drive.
- ChatGPT: можно указать точные GitHub/Drive источники, если они доступны в конкретном worker-чате. Если это не подтверждено, приложите исходники inline.
- Gemini: только точные Google Drive источники; GitHub не использовать. Укажите drive_target в карточке. Если Drive не открылся, исполнитель обязан вернуть BLOCKED.

## Обязательные правила ответа

Верни полный ответ и все требуемые доказательства. Не утверждай, что отправка/публикация/коммит/тест выполнены, если это не подтверждено. Если источники или инструменты недоступны, укажи BLOCKED и точную причину. Не присваивай себе независимый PASS.
