# Индекс публичных контрактов

Публичные карточки: **2**. Реальное выполнение: **0 подтверждено**.

| Contract ID | Revision | Producer | Public card | Public prompt | Status |
|---|---:|---|---|---|---|
| **C0001** | 1 | BROWN_SWARM_MASTER | [C0001](contracts/C0001.md) | [DeepSeek](prompts/C0001-DeepSeek.md) | PUBLISHED / READY_TO_FORWARD; NOT DISPATCHED |
| **V0002** | 1 | BROWN_SWARM_MASTER | [V0002](contracts/V0002.md) | [ChatGPT Validator](prompts/V0002-ChatGPT.md) | PUBLISHED / WAITING_FOR_C0001 |

**Порядок:** C0001 → полное получение ответа из DeepSeek → Publisher направляет оригинал в GPT для записи файла → через ~120 секунд после `PUBLISH_SEND_CLICKED` V0002 проверяет фактический файл и транспортные receipts. При отсутствии файла V0002 возвращает `RESULT_PENDING`, не PASS.

**Безопасность:** это публичные тексты тестовых заданий READ_ONLY. Карточка/индекс не являются доказательством фактической отправки, авторизации на запись, запуска модели, успешного сохранения результата или независимого PASS. Источник прав — исходный контракт в [BrownGuyGPTmem](https://github.com/player5/BrownGuyGPTmem/tree/main/BROWN_COMMAND/TEST_CONTRACTS), разрешение Producer и GATE. Никаких секретов, модельных API, merge/deploy.

**Известное предупреждение:** `GET_STATUS RECEIPT_UNCERTAIN` вместе с `TARGET_TAB_MISMATCH` на Gemini — диагностический сбой адресации. Не считать это ACK и не отправлять пилот в Gemini; сначала подтвердить реальную DeepSeek-вкладку.
