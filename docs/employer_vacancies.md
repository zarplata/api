# Вакансии для работодателя

* [Варианты публикации вакансий](#available_types)
* [Публикация вакансий](#creation)
* [Условия заполнения полей при добавлении и редактировании вакансий](#conditions)
* [Редактирование вакансий](#edit)
* [Продление вакансий](#prolongate)
* [Информация о возможности продления вакансии](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/get-prolongation-vacancy-info)
* [Список опубликованных вакансий](#active)
* [Архивация вакансий](#archive)
* [Список архивных вакансий](#archived)
* [Удаление вакансий](#hide)
* [Список удаленных вакансий](#hidden)
* [Восстановление из удаленных](#restore)
* [Статистика по вакансии](#stats)
* [Просмотры вакансии](#visitors)

Смотрите также:

* [Дополнительные поля для автора вакансии при получении вакансии](vacancies.md#author)


<a name="available_types"></a>
## Варианты публикации вакансий у текущего менеджера

> !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Informaciya-o-menedzhere/operation/get-available-vacancy-types)

<a name="creation"></a>
## Публикация вакансий

> !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/publish-vacancy)

<a name="conditions"></a>
## Условия заполнения полей при добавлении и редактировании вакансий

> !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/get-vacancy-conditions)

<a name="edit"></a>
## Редактирование вакансий

> !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/edit-vacancy)

<a name="other-actions"></a>
### Прочие действия

* [архивация](#archive)
* [удаление](#hide)
* [восстановление из удаленных](#restore)



<a name="prolongate"></a>
## Продление вакансий

**Продление вакансии по стоимости приравнивается к новой публикации**

Существуют ограничения по продлению вакансии, они могут меняться, на данный
момент работают следующие правила:

* "Промо" вакансии можно продлевать, если с предыдущего продления прошло не менее 1 минуты.
* вакансии "Бизнес" возможно продлевать не ранее 7 дней до окончания публикации.


### Запрос

`POST /vacancies/{vacancy_id}/prolongate`

где `vacancy_id` - идентификатор вакансии.

### Ответ

При успешном продлениии вакансии вернется `204 No Content`.

### Ошибки

* `403 Forbidden` – текущий пользователь не является работодателем или
  продление невозможно.
* `404 Not Found` – текущему пользователю недоступно продление вакансии.
* `404 Not Found` – вакансия с переданным идентификатором не существует.

Дополнительно к HTTP коду сервер может вернуть
описание [причины ошибки](errors.md#vacancies-prolongate).


<a name="prolongate-info"></a>
## Информация о возможности продления вакансии


### Запрос

`GET /vacancies/{vacancy_id}/prolongate`

где `vacancy_id` - идентификатор вакансии.


### Ответ

Успешный ответ приходит с кодом `200 OK`.

Пример ответа, когда продление невозможно:

```json
{
    "id": "123456789",
    "expires_at": "2015-11-19T17:10:48+0300",
    "actions": [
        {
            "id": "prolongate",
            "enabled": false,
            "disable_reason": {
                "id": "standard_plus_publication_is_updated_automatically",
                "name": "Вакансия 'Бизнес' не может быть обновлена, это происходит автоматически раз в три дня."
            }
        }
    ]
}
```

Пример ответа, когда продление возможно только со списанием вакансии со счёта:

```json
{
    "id": "123456789",
    "expires_at": "2015-11-19T17:10:48+0300",
    "actions": [
        {
            "id": "prolongate",
            "enabled": true,
            "free_renewal_available": false,
            "url": "https://api.zarplata.ru/vacancies/123456789/prolongate",
            "method": "POST"
        }
    ]
}
```

К вакансии может быть подключена опция продления вакансии без списания публикации со счёта раз в n часов (условия регулируются действующим прайс-листом).  
Для того, чтобы его сделать нужно воспользоваться `free_renewal_url`. При этом вакансию можно продлить со списанием используя `url`.
Пример ответа, когда для вакансию можно продлить без списания: 

```json
{
    "id": "123456789",
    "expires_at": "2015-11-19T17:10:48+0300",
    "actions": [
        {
            "id": "prolongate",
            "enabled": true,
            "url": "https://api.zarplata.ru/vacancies/123456789/prolongate",
            "method": "POST",
            "free_renewal_available": true,
            "next_free_renewal_date": "2015-11-18T12:00:00+0300",
            "free_renewal_url": "https://api.zarplata.ru/vacancies/123456789/prolongate?free_renewal=true"
        }
    ]
}
```

Если интервал до следующего продления без списания ещё не истёк, то поля `free_renewal_url` в ответе не будет. 
При этом вакансию по-прежнему можно продлить со списанием используя урл из поля `url`.
Пример ответа, когда вакансию можно продлить без списания, но время до следующего такого продления ещё не истекло:

```json
{
    "id": "123456789",
    "expires_at": "2015-11-19T17:10:48+0300",
    "actions": [
        {
            "id": "prolongate",
            "enabled": true,
            "url": "https://api.zarplata.ru/vacancies/123456789/prolongate",
            "method": "POST",
            "free_renewal_available": "true",
            "next_free_renewal_date": "2015-11-18T12:00:00+0300"
        }
    ]
}
```
Имя | Тип | Описание
---- | --- | --------
actions | object | Cписок действий, которые можно предпринять для продления вакансии. В данный момент поддерживается только обычное продление.
actions.id | string | Идентификатор действия
actions.enabled | boolean | Флаг возможно ли действие
actions.disable_reason | object | Причина, по которой совершить действие невозможно. Элемент справочника [vacancy_not_prolonged_reason](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki/paths/~1dictionaries/get) 
actions.url | string | url, с которыми нужно сделать запрос, чтобы совершить действие
actions.method | string | HTTP-метод, с которыми нужно сделать запрос, чтобы совершить действие
actions.free_renewal_available | boolean | Применена ли к вакансии опция продления без списания
actions.next_free_renewal_date | date ISO string или null| Дата следующего продления без списания
actions.free_renewal_url | string или null| Урл для продления вакансии без списания со счёта

### Ошибки

* `403 Forbidden` – текущий пользователь не является работодателем.
* `404 Not Found` – текущему пользователю недоступно получение информации о вакансии.
* `404 Not Found` – вакансия с переданным идентификатором не существует.


> > !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/vacancy-prolongation)

## Информация о возможности продления вакансии
> > !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/get-prolongation-vacancy-info)

<a name="active"></a>
## Список опубликованных вакансий

> > !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Vakansii/operation/get-active-vacancy-list)

<a name="archive"></a>
## Архивация вакансий

> !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/add-vacancy-to-archive)

<a name="archived"></a>
## Список архивных вакансий

> !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/get-archived-vacancies)

<a name="hide"></a>
## Удаление вакансий

> !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/add-vacancy-to-hidden)

<a name="hidden"></a>
## Список удаленных вакансий

> !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/get-hidden-vacancies)

<a name="restore"></a>
## Восстановление из удаленных

> !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/restore-vacancy-from-hidden)

<a name="stats"></a>
## Статистика по вакансии

> !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/get-vacancy-stats)

<a name="visitors"></a>
## Просмотры вакансии

> !! Данный метод доступен в [OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Vakansii/operation/get-vacancy-visitors)
