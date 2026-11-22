# <CONTRACT_ID> — публичная карточка

**Статус:** TEMPLATE / НЕ ЗАДАНИЕ

- `contract_id`: `<CONTRACT_ID>`
- `schema`: `brown.swarm.public-card.v1`
- `revision`: `<NUMBER>`
- `iteration`: `<NUMBER>`
- `attempt`: `<NUMBER>`
- `delivery_id`: `<STABLE_UNIQUE_DELIVERY_ID>`
- `producer`: `<PRODUCER_NAME>`
- `project`: `<PROJECT_KEY>`
- `executor`: `<DeepSeek|ChatGPT|Gemini>`
- `mode`: `READ_ONLY` *(CODE_CHANGE запрещён публичным маршрутом до машинной проверки разрешения постановщика, write_set, base commit и GATE)*
- `required_capabilities`: `none` *(пока нет проверки коннекторов конкретной вкладки; github/drive будут BLOCKED_SESSION_CONNECTOR_NOT_VERIFIED)*
- `drive_target`: `<D1|D2|D3>/<PATH>` *(только для будущих Gemini Drive-заданий после проверки привязки сессии)*
- `self_contained`: `<true|false>`
- `prompt`: [полный промпт](../prompts/<CONTRACT_ID>-<PROVIDER>.md)
- `prompt_blob_sha`: `<40_HEX_GIT_BLOB_SHA>`
- `files_manifest`: [подготовленные файлы](../files/<CONTRACT_ID>.json)
- `files_manifest_blob_sha`: `<40_HEX_GIT_BLOB_SHA>`
- `blocker`: `<D000|D001|...>`
- `depends_on`: `<CONTRACT_ID+CONTRACT_ID_OR_EMPTY>`
- `canonical_contract`: `<AUDIT_REFERENCE_ONLY; NEVER A DISPATCHER FETCH SOURCE>`

## Краткое задание

Опишите задачу в пределах исходного контракта. Dispatcher передаёт подготовленный промпт и только перечисленные в манифесте публичные файлы. Он не ищет исходники в приватных репозиториях.

## Подготовка по исполнителю

- **DeepSeek:** никаких GitHub/Drive-коннекторов. Все нужные исходники должны быть встроены в промпт или в текстовые файлы манифеста; максимум 5 файлов.
- **ChatGPT:** может использовать GitHub/Drive лишь после доказанной доступности в данной вкладке; пока такого доказательства нет, публичный диспетчер блокирует `required_capabilities=github/drive`. Рабочий вариант — самодостаточный текст с `required_capabilities=none`.
- **Gemini:** GitHub недоступен, Drive возможен только после доказанной привязки D1/D2/D3 к конкретной вкладке. Пока привязка и readback не реализованы, Drive-зависимые публичные задания блокируются. Можно использовать самодостаточный текстовый промпт.

## Файловый манифест

Если используются отдельные исходники, опубликуйте `files/<CONTRACT_ID>.json` по схеме:

```json
{
  "schema": "brown.swarm.public-files.v1",
  "contract_id": "<CONTRACT_ID>",
  "files": [
    {
      "path": "files/<CONTRACT_ID>/source.txt",
      "blob_sha": "<40_HEX_GIT_BLOB_SHA>"
    }
  ]
}
```

Файлы должны быть текстовыми, безопасными для публичной публикации и иметь Git blob SHA. Если исходники не встроены в сам промпт, файловый манифест должен содержать хотя бы один файл. Даже `required_capabilities=none` не отменяет необходимости `self_contained=true` либо проверенного манифеста. Не включайте секреты, cookies, ключи, персональные данные или закрытые конфигурации. Максимум 5 файлов.

## Границы

Публичная карточка — команда на передачу подготовленного задания, но не подтверждение результата. Она не объявляет PASS, не подтверждает выполнение, не разрешает merge или деплой. Не публикуйте карточку до прохождения требуемого GATE и проверки публичности всех вложений.
