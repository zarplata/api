# Справочник регионов

> ‼️ Внимание! Значения в справочниках могут поменяться в любой момент. Не нужно завязываться на них.

* [Дерево всех регионов](#areas)
* [Справочник регионов, начиная с указанного](#item)
* [Справочник стран](#countries)
* [Дополнительные параметры запроса](#additional_parameters)

### Смотрите также

* [Подсказки по полному дереву регионов и листам дерева регионов](suggests.md#areas)


<a name="areas"></a>
## Дерево всех регионов

`GET /areas` возвращает древовидный список всех регионов с указанием названия
региона, его идентификатором и ссылкой на родительский регион `parent_id`.

```json
[
    {
        "name": "Украина",
        "id": "5",
        "parent_id": null,
        "areas": [
            {
                "name": "Киев",
                "id": "115",
                "parent_id": "5",
                "areas": []
            }
        ]
    }
]
```

Пример: [https://api.zarplata.ru/areas](https://api.zarplata.ru/areas)


<a name="item"></a>
## Справочник регионов, начиная с указанного

`GET /areas/{area_id}` вернёт древовидный список регионов, начиная с указанного.

Пример: [https://api.zarplata.ru/areas/1146](https://api.zarplata.ru/areas/1146)


<a name="countries"></a>
## Справочник стран

`GET /areas/countries` вернёт подмножество регионов, являющихся странами.

Пример ответа:

```json
[
  {
    "url": "https://api.zarplata.ru/areas/113",
    "id": "113",
    "name": "Россия"
  },
  {
    "url": "https://api.zarplata.ru/areas/5",
    "id": "5",
    "name": "Украина"
  }
]
```

<a name="additional_parameters"></a>
## Дополнительные параметры запроса

Только для русской локализации можно получить дополнительное поле - название area в предложном падеже. Для этого нужно передать query параметр:

`GET /areas/{area_id}?additional_case=prepositional`

Пример: [https://api.zarplata.ru/areas/1?additional_case=prepositional](https://api.zarplata.ru/areas/1?additional_case=prepositional)

```json
{
  "id": "1",
  "parent_id": "113",
  "name": "Москва",
  "areas": [],
  "name_prepositional": "в Москве"
}
```

### Ошибки при запросе

При передаче не поддерживаемого падежа возвращается ошибка

`GET /areas/{area_id}?additional_case=wrong_case`

Пример: [https://api.zarplata.ru/areas/1?additional_case=wrong_case](https://api.zarplata.ru/areas/1?additional_case=wrong_case)

```json
{
  "errors": [
    {
      "type": "bad_argument",
      "value": "wrong_case"
    }
  ]
}
```
