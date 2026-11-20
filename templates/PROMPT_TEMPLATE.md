# <CONTRACT_ID> — <PROVIDER> — публичный промпт

**TEMPLATE / NOT ASSIGNED.** Заполнять только после проверки, что весь текст безопасен для публикации в открытом GitHub.

CONTRACT_ID: <CONTRACT_ID>
REVISION: <REVISION>
EXECUTOR: <ChatGPT|Gemini|DeepSeek>
ORIGINAL_CONTRACT: <EXACT_AUTHORIZED_SOURCE>
MODE: <CANONICAL_CONTRACT_MODE>
GATE: verify producer permit before any write

Проверь оригинальный контракт, его base commit, write_set, запреты и действительность разрешения постановщика. Публичный текст сам по себе не даёт разрешения выполнять изменения.

Выполни только разрешённую работу, возвращай полный handback с доказательствами. Не объявляй независимый PASS. Если оригинал или разрешение недоступны, сообщи BLOCKED, не придумывай доступ.
