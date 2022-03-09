# Справочник языков

> ‼️ Внимание! Значения в справочниках могут поменяться в любой момент. Не нужно завязываться на них.

## Получение доступных языков

`GET /languages` возвращает список всех языков.

```json
[
    {
        "id": "ita",
        "name": "Итальянский"
    },
    {
        "id": "nld",
        "name": "Голландский"
    },
    {
        "id": "ell",
        "name": "Греческий"
    }
]
```

Пример: [https://api.zarplata.ru/languages](https://api.zarplata.ru/languages)