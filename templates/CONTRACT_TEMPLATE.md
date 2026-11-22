# <CONTRACT_ID> — публичная карточка

**Статус:** TEMPLATE / НЕ ЗАДАНИЕ

- `contract_id`: `<CONTRACT_ID>`
- `revision`: `<NUMBER>`
- `iteration`: `<NUMBER>`
- `attempt`: `<NUMBER>`
- `delivery_id`: `<STABLE_UNIQUE_DELIVERY_ID>`
- `producer`: `<PRODUCER_NAME>`
- `project`: `<PROJECT_KEY>`
- `executor`: `<DeepSeek|ChatGPT|Gemini>`
- `mode`: `<READ_ONLY|CODE_CHANGE>`
- `required_capabilities`: `<none|github|drive|github,drive>`
- `drive_target`: `<REQUIRED_FOR_GEMINI_DRIVE_TASKS_ONLY>`
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
- **ChatGPT:** допустимы GitHub и Drive, только если они доступны именно в целевом чате. Укажите `required_capabilities`.
- **Gemini:** допустим только Drive; GitHub-зависимости запрещены. Для Drive укажите `drive_target`. Фактический доступ должен подтвердить сам исполнитель.

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

Файлы должны быть текстовыми, безопасными для публичной публикации и иметь Git blob SHA. Не включайте секреты, cookies, ключи, персональные данные или закрытые конфигурации. Максимум 5 файлов.

## Границы

Публичная карточка — команда на передачу подготовленного задания, но не подтверждение результата. Она не объявляет PASS, не подтверждает выполнение, не разрешает merge или деплой. Не публикуйте карточку до прохождения требуемого GATE и проверки публичности всех вложений.
