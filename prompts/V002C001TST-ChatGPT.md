# ПОЛНЫЙ ПРОМПТ — V002C001TST / независимая проверка текста на 100 слов

ROLE: независимый Validator BROWN SWARM / ChatGPT. Это отдельный обычный исполняемый контракт, не Publisher и не автор исходного текста.
CONTRACT_ID: V002C001TST
MODE: READ_ONLY
ITERATION: 1
ATTEMPT: 1
REVISION: 2
RESPONSE_LANGUAGE: ru-RU
TARGET_CONTRACT: C001D000TST
DEPENDS_ON: C001D000TST
SOURCE_DELIVERY_ID: PUB-C001D000TST-I2-A1
EXPECTED_RESULT_PATH: results/PUB-C001D000TST-I2-A1.txt
EXPECTED_TOPIC: Как устроена автоматизация современного макаронного завода

**Сначала выполни короткую служебную вставку, если она приложена Dispatcher:** запиши доставленный результат C001 и убери его строку из активного INDEX. Затем переходи к независимой проверке текста по критериям ниже. Не требуй отдельного PROCESSED или SHA-гейта. Действуй по реально доступному результату, ничего не придумывай.

1. Прочитай карточку [C001D000TST](https://github.com/player5/ContractsPolivas/blob/main/contracts/C001D000TST.md) и её [полный промпт](https://github.com/player5/ContractsPolivas/blob/main/prompts/C001D000TST-DeepSeek.md).
2. Прочитай фактический текст результата: https://raw.githubusercontent.com/player5/ContractsPolivas/main/results/PUB-C001D000TST-I2-A1.txt. Если файл недоступен, честно верни `RESULT_PENDING` и не заявляй PASS.
3. Найди ровно один блок `TEXT_BEGIN`/`TEXT_END`, внутри которого должен находиться один русский связный абзац про автоматизацию макаронного завода.
4. Независимо сосчитай слова **только между этими маркерами**. Слово — непрерывная группа непробельных символов; разделители — любые пробелы, табуляция, перевод строки. Должно быть **ровно 100**.
5. Проверь содержание по теме, техническую связность, отсутствие списков/заголовков внутри текста, корректность финального `BROWN_STATUS|v1|C001D000TST|PUB-C001D000TST-I2-A1|DONE`.
6. Выдай **подробный предметный отчёт**: `SOURCE_CONTRACT`, `SOURCE_DELIVERY_ID`, `SOURCE_URL`, `RESULT_AVAILABLE`, `WORD_COUNT_ACTUAL`, `WORD_COUNT_EXPECTED=100`, `WORD_COUNT_VERDICT`, `TOPIC_VERDICT`, `STRUCTURE_VERDICT`, `SOURCE_STATUS_VERDICT`, `CONTENT_VERDICT`, доказательства по каждому критерию и `NEXT_EXACT_STEP`. Никаких SHA и криптографических проверок для учёта завершения.
7. Если содержание не соответствует ТЗ, сформулируй точное замечание для срочного исправления с конечной `F`: `C001D000TSTF`. Не утверждай независимый PASS по одному только `DONE`; статус работы Validator и результат проверки содержимого указывай отдельно.

**Права:** не исправляй исходный текст, не меняй сторонние контракты, проекты или доступы. Короткая служебная уборка уже завершённых контрактов в начале обычного GPT-задания выполняется отдельно от этой предметной проверки; там не надо оценивать качество, считать слова или SHA.

Финальная строка своего отчёта:
BROWN_STATUS|v1|V002C001TST|{{BROWN_DELIVERY_ID}}|<STATUS>

Заменяй `<STATUS>` на `DONE`, `BLOCKED` или `NEED_INPUT` по фактическому завершению работы.
