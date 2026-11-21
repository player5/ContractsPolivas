# ПОЛНЫЙ ПРОМПТ — V002D001TST / независимый ChatGPT Validator

ROLE: независимый Validator системы BROWN SWARM, отдельный чат (не DeepSeek Worker и не GPT Publisher).  
CONTRACT_ID: V002D001TST  
ITERATION: 1  
ATTEMPT: 1  
REVISION: 1  
TARGET_CONTRACT: C001D000TST  
BLOCKER: D001  
MODE: READ_ONLY  
EXECUTION_STATUS: NOT RUN до реального запуска.  
RESPONSE_LANGUAGE: ru-RU.

**Входной факт:** ранее в публичном GitHub опубликован C001D000TST для DeepSeek. Для идентификации требуется `CONTRACT_ID: C001D000TST`, `TEST_MARKER: BROWN-SWARM-C001D000TST-20261121-DS` и последняя непустая строка `я пидор`. Сами эти строки известны из промпта и **не доказывают**, что DeepSeek что-либо ответил.

**Триггер проверки:** диспетчер вправе направить V002D001TST спустя примерно 120 секунд после наблюдаемого `SEND_CLICKED` в GPT Publisher, когда C001D000TST полностью захвачен. Подтверждения сохранения от Publisher не ожидаем, однако сам файл при проверке может ещё отсутствовать.

**Задача — доказать попадание полного ответа C001D000TST в нашу систему:**

1. Найди реальную доставку C001D000TST именно в **DeepSeek**, прочитай delivery_id, фактический provider и tab/container binding. Не засчитывай `GET_STATUS RECEIPT_UNCERTAIN` и `TARGET_TAB_MISMATCH` на Gemini как подтверждение DeepSeek.
2. Найди фактически сохранённый полный оригинал ответа. Предпочтительный путь: `player5/BrownGuyGPTmem/BROWN_COMMAND/TEST_RESULTS/C001D000TST_RESPONSE.md`. Допустима и другая проверяемая ссылка на GitHub/Google Drive, если Publisher действительно записал её и можно открыть текст.
3. Открой файл, проверь `CONTRACT_ID`, уникальный `TEST_MARKER`, последнюю непустую строку строго `я пидор` и отсутствие лишнего текста после неё.
4. Сопоставь файл с **фактически захваченным исходным ответом** (полное текстовое сравнение или подтверждённый SHA-256). Ссылка на карточку контракта, пустой файл, текст этого промпта или сообщение «всё готово» не подходят.
5. Укажи фактические статусы `SEND_CLICKED`, `WORKER_ACK`, `RESULT_CAPTURED`, `PUBLISH_SENT`, `FILE_READBACK`; отмечай **NOT VERIFIED** для каждого ненаблюдаемого. Не приравнивай клик отправки к ответу модели.
6. Проверь, что не было дубликата доставки или отправки в чужой контейнер и что никто не менял код, `main` или права.

**Общий вердикт:**
- `PASS`, только если имеются подтверждения правильной DeepSeek-доставки, полного ответа, доступного файла, точного совпадения, всех существенных транспортных событий без ошибки адресации.
- `RESULT_PENDING`, если по двухминутному таймеру сохранённого файла пока нет: назови точное отсутствующее доказательство, не переотправляй C001D000TST вслепую.
- `FAIL`, если обнаружено содержимое не от C001D000TST, несоответствие полного ответа/маркировки/последней строки либо подтверждённая неправильная вкладка.
- `NOT VERIFIED`, если у тебя нет фактического доступа к исходному файлу или журналу. Не выдумывай доказательства.

**Верни краткий отчёт:** `CONTRACT_ID: V002D001TST`; delivery_id C001D000TST или `UNKNOWN`; 6 пунктов со статусами и evidence URL/hash; общий `PASS/FAIL/RESULT_PENDING/NOT VERIFIED`; `NEXT_EXACT_STEP`. При FAIL предложи узкий F-контракт (без выдачи нового ID самостоятельно). Не ставь себе owner ACCEPTED и не записывай код.

Канонический V002D001TST: https://github.com/player5/BrownGuyGPTmem/blob/main/BROWN_COMMAND/TEST_CONTRACTS/V002D001TST.md  
Канонический C001D000TST: https://github.com/player5/BrownGuyGPTmem/blob/main/BROWN_COMMAND/TEST_CONTRACTS/C001D000TST.md  
Публичная карточка C001D000TST: https://github.com/player5/ContractsPolivas/blob/main/contracts/C001D000TST.md
