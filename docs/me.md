# Информация об авторизованном пользователе или приложении

* [Получение информации об авторизованном пользователе](#user-info)
* [Получение информации об авторизованном приложении](#application-info)


<a name="general"></a>
Обратите внимание, что в зависимости от типа переданного токена приходят разные ответы. В случае токена для приложения ответ будет содержать только некоторые флаги.


<a name="user-info"></a>
## Получение информации об авторизованном пользователе

`GET /me` вернёт информацию о текущем авторизованном пользователе.

### Ответ

Успешный ответ приходит с кодом `200 OK` и содержит тело:

```json
{
    "id": "12345678",
    "last_name": "Фамилия",
    "first_name": "Имя",
    "middle_name": "Отчество",
    "is_admin": false,
    "is_applicant": false,
    "is_employer": true,
    "is_application": false,
    "email": "contact@example.com",
    "employer": {
        "manager_id": "4062820",
        "id": "1455",
        "name": "zarplata"
    },
    "manager": {
        "id": "87654321",
        "has_admin_rights": true,
        "is_main_contact_person": true,
        "manager_settings_url": "https://api.zarplata.ru/employers/1455/managers/87654321/settings",
        "has_multiple_manager_accounts": true
    },
    "personal_manager": {
        "id": "1234567",
        "first_name": "Иван",
        "last_name": "Иванов",
        "email": "ivanov@example.com",
        "photo_urls": {
            "big": "https://zarplatacdn.ru/file/big.jpg",
            "small": "https://zarplatacdn.ru/file/small.jpg"
        },
        "is_available": false,
        "unavailable": {
            "until": "2016-07-01T08:00:00+0400"
        }
    },
    "counters": {
        "unread_negotiations": 0,
        "new_resume_views": 2,
        "resumes_count": 5
    },
    "negotiations_url": "https://api.zarplata.ru/negotiations"
}
```


 Имя | Тип | Описание
 --- | --- | ---
 id | строка | идентификатор пользователя
 last_name | строка | фамилия
 first_name | строка | имя
 middle_name | строка, null | отчество, при отсутствии — null
 is_admin | логический | является ли пользователь администратором сайта
 is_employer | логический | true, если пользователь – работодатель
 is_application | логический | true, если авторизация приложения
 email | строка, null | электронный адрес
 employer | объект, null | [информация о компании](#employer-info), если текущий пользователь — работодатель, или null в остальных случаях
 personal_manager | объект, null | [информация о персональном менеджере](#personal-manager-info), если текущий пользователь — работодатель, или null в остальных случаях
 manager | объект, null | [информация о пользователе как о менеджере компании](#manager-info), если текущий пользователь — работодатель, или null в остальных случаях
 resumes_url | строка | ссылка на api-сервис списка резюме текущего пользователя
 negotiations_url | строка | ссылка на api-сервис списка откликов/приглашений текущего пользователя
 counters | объект, отсутствует | [информация о счетчиках](#counters-info)


<a name="employer-info"></a>
#### Объект `employer`

Имя | Тип | Описание
--- | --- | ------
 id | строка | идентификатор компании
 manager_id | строка | идентификатор персонального менеджера
 name | строка | название компании


<a name="manager-info"></a>
#### Объект `manager`

Имя | Тип | Описание
--- | --- | ------
id | строка | идентификатор менеджера
has_admin_rights | логический | обладает ли текущий менеджер правами администратора
is_main_contact_person | логический | является ли текущий менеджер главным контактным лицом компании
manager_settings_url | строка | url, на который нужно сделать GET запрос, чтобы получить [предпочтения менеджера](manager_settings.md)
has_multiple_manager_accounts | логический | существуюет ли у пользователя несколько [рабочих аккаунтов](manager_accounts.md)

<a name="personal-manager-info"></a>
#### Объект `personal_manager`

Информация о персональном менеджере для работодателя.

Имя | Тип | Описание
--- | --- | ---
 id | строка | Идентификатор персонального менеджера
 email | строка | email персонального менеджера
 first_name | строка | Имя менеджера
 last_name | строка | Фамилия менеджера
 photo_urls | объект, null | фотографии менеджера, либо `null`, если их нет
 photo_urls.big | строка, null | url большой фотографии менеджера, либо `null`, если её нет
 photo_urls.small | строка, null | url маленькой фотографии менеджера, либо `null`, если её нет
 is_available | логическое | доступен ли менеджер в данный момент
 unavailable | объект, null | информация об отсутствии менеджера, либо `null`, если менеджер доступен
 unavailable.until | строка (дата) | время, до которого менеджер недоступен для контакта


<a name="counters-info"></a>
#### Объект `counters`

Все значения ключей — числа.

Имя | Описание
--- | ---
unread_negotiations | Количество новых непрочитанных переписок (у которых `has_updates: true`)
new_resume_views | Общее количество новых просмотров всех резюме текущего пользователя
resumes_count | Общее количество созданных резюме текущего пользователя

### Ошибки

* `403 Forbidden` – ошибка авторизации пользователя.

<a name="application-info"></a>
## Получение информации об авторизованном приложении

`GET /me` вернёт ответ с телом, аналогичным ответу [получение информации о текущем пользователе](#user-info), но содержит только флаги.

```json
{
    "is_admin": false,
    "is_employer": false,
    "is_application": true
}
```

### Ошибки

* `403 Forbidden` – ошибка авторизации приложения.