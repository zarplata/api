# Отрасли компаний

> ‼️ Внимание! Значения в справочниках могут поменяться в любой момент. Не нужно завязываться на них.

`GET /industries` возвращает двухуровневый справочник всех отраслей. 

```json
[
  {
    "id": "49",
    "name": "Услуги для населения",
    "industries": [
        {
            "id": "49.408",
            "name": "Ритуальные услуги"
        }
    ]
  }
]
```

Все верхнеуровневые объекты считаются отраслями, а объекты из массивов `industries` - специальностями.

В справочнике возможны другие значения.

----

Пример: [https://api.zarplata.ru/industries](https://api.zarplata.ru/industries)
