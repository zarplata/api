# Поиск резюме

Смотрите также:

* [Просмотр резюме](https://github.com/zarplata/api/blob/master/docs/resumes.md#item)
  * [Платные услуги для работодателя связанные с резюме](https://github.com/zarplata/api/blob/master/docs/resumes.md#paid-services)

<a name="search-params"></a>
## Запрос

`GET /resumes` вернёт результаты поиска резюме.

Некоторые параметры принимают множественные значения: `key=value&key=value`.

> Внимание! Неизвестные параметры и параметры с ошибкой в названии игнорируются.

* `text` — поисковая фраза. Найдет резюме, в которых встречаются все слова
  заданной фразы. Возможно указание нескольких значений. Каждый дополнительный
  `text` уточняет поиск. В качестве поисковой фразы можно использовать
  [язык поисковых запросов](http://hr.zarplata.ru/article.xml?articleId=1175).
  Специально для этого поля есть [автодополнение](suggests.md#resume-search-keyword).
  Для тонкой настройки по фразе можно использовать параметры `text.logic`,
  `text.field`, `text.period`. При использовании дополнительных `text.*` полей,
  необходимо указывать весь набор (триаду) параметров. 

* `text.logic` – описывает, как производится поиск. Справочник с возможными
  значениями: `resume_search_logic` в [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md).

* `text.field` – описывает, где должны встречаться слова из поисковой фразы
  `text`. В параметре text.field можно укзать несколько значений через запятую,
  например – `?text.field=education,keywords`. Справочник с возможными
  значениями: `resume_search_fields` в [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md).

* `text.period` – период для поиска в опыте работы. Параметр имеет смысл
  только для `text.field` равного одному из: `experience`, `experience_company`,
  `experience_position`, `experience_description`, но указывать его необходимо
  всегда  при указании других `text.*`. В этом случае он может быть пустым.

* `age_from`, `age_to` — возраст соискателя в годах, диапазон от и до. Обратите внимание, по умолчанию в выдачу добавляются так же резюме с неуказанным возрастом, для выдачи резюме только с указанным возрастом используйте специальный [label](#resume_search_label) "only_with_age"

* `area` — регион. Справочник с возможными значениями: [/areas](https://github.com/zarplata/api/blob/master/docs/areas.md).
  Можно указать несколько значений. По умолчанию выбираются
  резюме, в которых соискатели живут в указанных регионах или готовы в них
  переехать, поменять это поведение можно указанием поля `relocation`.

* `relocation` — готовность к переезду. Справочник с возможными
  значениями: `resume_search_relocation` в [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md).
  Необходимо указывать вместе с параметром `area`.

* `period` — в днях, ищет резюме опубликованные за указанный период.
  Если не указан, поиск ведется без ограничений по дате публикации.

* `date_from` – дата, от которой нужно начать поиск. Значение указывается в формате
  [ISO 8601](https://github.com/zarplata/api/blob/master/docs/general.md#date-format) -
  `YYYY-MM-DD` или с точность до секунды `YYYY-MM-DDThh:mm:ss±hhmm`. Нельзя передавать вместе с параметром `period`.

* `date_to` – дата, до которой нужно искать. Значение указывается в формате
  [ISO 8601](https://github.com/zarplata/api/blob/master/docs/general.md#date-format) -
  `YYYY-MM-DD` или с точность до секунды `YYYY-MM-DDThh:mm:ss±hhmm`. Можно передавать только в паре
  с параметром `date_from`. Нельзя передавать вместе с параметром `period`.

* `education_level` —  уровень образования. Справочник с возможными значениями:
  `education_level` в [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md). Если не указан, поиск
  ведется без ограничений на уровень образования.

* `employment` — тип занятости.
  Справочник с возможными значениями: `employment` в
  [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md). Можно указать несколько значений.

* `experience` — опыт работы. Справочник с возможными значениями: `experience`
  в [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md).

* `skill` - ключевые навыки. Указывается один или несколько идентификаторов
  ключевых навыков. Значения можно получить из поля `id` в
  [подсказке по ключевым навыкам](https://github.com/zarplata/api/blob/master/docs/suggests.md#key-skills).

* `gender` — пол. Справочник с возможными значениями: `gender` в
  [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md). По умолчанию вне зависимости от значения
  параметра будут найдены резюме, в которых пол не указан, убрать такие резюме
  можно с помощью `label=only_with_gender`.

<a name="resume_search_label"></a>
* `label` — дополнительный фильтр. Справочник с возможными значениями:
  `resume_search_label` в [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md). Можно указать
  несколько значений.

* `language` — знание языка. Можно указать несколько значений. Задается в
  формате language.level, где:
     * `language` — значение из справочника [/languages](https://github.com/zarplata/api/blob/master/docs/languages.md),
     * `level` — значение из справочника `language_level`
       [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md).

* `metro` — линия, либо станция метро. Справочник с возможными значениями:
  [/metro](https://github.com/zarplata/api/blob/master/docs/metro.md).

* `currency` — код валюты. Справочник с возможными значениями: `currency`
  (ключ code) в [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md).

* `salary_from`, `salary_to` — диапазон желаемой заработной платы (ЗП), от и до. Обратите внимание, по умолчанию в выдачу добавляются так же резюме с неуказанной ЗП, для выдачи резюме только с указанной ЗП используйте специальный [label](#resume_search_label) "only_with_salary"

* `schedule` — график работы. Справочник с возможными значениями:
  `schedule` в [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md). Можно указать несколько
  значений.

* `specialization` — профобласть или специализация. Справочник с возможными
  значениями: [/specializations](https://github.com/zarplata/api/blob/master/docs/specializations.md). Можно указать несколько
  значений. Будет заменен профессиональными ролями (параметр `professional_role`), в настоящее время работает в режиме обратной совместимости.

* `order_by` — сортировка списка резюме. Справочник с возможными значениями:
  `resume_search_order` в [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md).

* `citizenship` — страна желаемого гражданства. Возможные значения можно
  посмотреть в справочнике стран. Возможно указание нескольких значений.

* `work_ticket` — страна, в которой есть разрешение на работу. Возможные
  значения можно посмотреть в справочнике стран. Возможно указание нескольких
  значений.

* `educational_institution` – учебные заведения соискателя. В качестве
  параметров используются подсказки по названиям университетов
  [/suggests/educational_institutions](https://github.com/zarplata/api/blob/master/docs/suggests.md). Возможно указание
  нескольких значений.

* `search_in_responses` — `true`: искать только по резюме, которыми соискатели
  откликались на вакансии компании текущего пользователя, `false`: искать
  по всем резюме. Если параметр не указан, по умолчанию используется поиск по
  всем резюме.
  
* `by_text_prefix` — `true`: включает поиск по префиксу. Для каждого параметра `text` будут находиться не только полные 
  совпадения слов, но еще и слова, начинающиеся с `text`. По умолчанию стоит значение `false`.
  
* `driver_license_types` — категории водительских прав. Справочник с возможными значениями:
  `driver_license_types` в [/dictionaries](https://github.com/zarplata/api/blob/master/docs/dictionaries.md).
  
* `vacancy_id` — идентификатор вакансии для поиска похожих резюме. Необходимо передавать идентификатор активной или архивной вакансии работодателя.

* `per_page` — количество результатов на страницу (не может превышать 50).

* `page` — номер страницы.

* `professional_role` — профессиональная роль. Элемент справочника
  [professional_roles](professional_roles.md). Можно указать несколько
  значений. Замена специализациям (параметр `specialization`)

* `folder` — один или несколько идентификаторов папок с отобранными резюме.
Если данный параметр передан, поиск будет ограничен содержимым указанных папок.
Можно передавать идентификаторы нескольких папок, например: `folder=111&folder=222&folder=333`

* `include_all_folders` — признак, указывающий, нужно ли вести поиск по всем папкам с отобранными резюме.
Если у менеджера есть доступ к избранным папкам, то поиск проходит по умолчанию в избранных папках.
Если передать параметр `include_all_folders=false`, то поиск не будет ограничен папками.
Если будут переданы параметры `folder` и `include_all_folders` в одном запросе, вернется ошибка `400 Bad Request`.

При указании параметров пагинации (`page`, `per_page`) работает ограничение:
глубина возвращаемых результатов не может быть больше 2000. Например, возможен
запрос `per_page=10&page=199` (выдача с 1991 по 2000 резюме), но запрос с
`per_page=10&page=200` вернёт ошибку (выдача с 2001 до 2010 резюме).

Примеры запросов:

* `GET /resumes?text=программист` – найдет все резюме, в любом месте которого
  встречается заданное слово 'программист'.

* `GET /resumes?text=программист&text=java` – найдет резюме, в любом месте
  которого встречаются слова 'программист' и 'java'.

* `GET /resumes?text=программист%20java&text.logic=any&text.field=everywhere&text.period=all_time` –
  найдет резюме, в любом месте которого встречается любое из слов заданной
  фразы в параметре `text` ('программист' или 'java'). При использовании
  дополнительных полей, они должны быть указаны все.

* `GET /resumes?text=zarplata&text.logic=all&text.field=experience&text.period=last_three_years` –
  найдет все резюме, в опыте работы которых за последние 3 года встречается
  'zarplata'.

* `GET /resumes?text=менеджер%20проекта&text.logic=all&text.field=experience%2Cskills&text.period=last_year&text=ответственный&text.logic=all&text.field=everywhere&text.period=all_time` –
  найдет все резюме, в опыте работы за последний год и ключевых навыках которых
  встречаются слова 'менеджер' и 'проекта', а также слово 'ответственный'
  в любом месте резюме. Отметим, что дополнительные параметры
  `text.logic=all&text.field=experience%2Cskills&text.period=last_year`
  указаны для `text=менеджер%20проекта`, а
  `text.logic=all&text.field=everywhere&text.period=all_time` для параметра
  `text=ответственный`.
  
<a name="search-results"></a>
## Ответ

Успешный ответ приходит с кодом `200 OK` и содержит тело:

```json
{
    "found": 2099341,
    "per_page": 20,
    "page": 0,
    "pages": 250,
    "items": [
        {
            "id": "0123456789abcdef",
            "title": "Начинающий специалист",
            "url": "https://api.zarplata.ru/resumes/0123456789abcdef",
            "first_name": "Иван",
            "last_name": "Иванов",
            "middle_name": "Иванович",
            "can_view_full_info": true,
            "age": 19,
            "alternate_url": "http://hr.zarplata.ru/resume/0123456789abcdef",
            "created_at": "2015-02-06T12:00:00+0300",
            "updated_at": "2015-04-20T16:24:15+0300",
            "area": {
                "id": "1",
                "name": "Москва",
                "url": "https://api.zarplata.ru/areas/1"
            },
            "certificate": [
                {
                    "achieved_at": "2015-01-01",
                    "owner": null,
                    "title": "тест",
                    "type": "custom",
                    "url": "http://example.com/"
                }
            ],
            "education": {
                "primary": [
                    {
                        "name": "Российский государственный социальный университет, Москва",
                        "name_id": "39420",
                        "organization": "Факультет информационных технологий",
                        "organization_id": null,
                        "result": "Информатика",
                        "result_id": null,
                        "year": 2012
                    }
                ]
            },
            "total_experience": {
                "months": 118
            },
            "experience": [
                {
                    "position": "пастух",
                    "start": "2010-01-01",
                    "end": null,
                    "company": "Рога и копыта",
                    "industries": [
                        {
                            "id": "51.643",
                            "name": "Благоустройство и уборка территорий и зданий"
                        },
                        {
                            "id": "29.503",
                            "name": "Земледелие, растениеводство, животноводство"
                        }
                    ],
                    "company_url": "http://example.com/",
                    "area": {
                        "id": "1",
                        "name": "Москва",
                        "url": "https://api.zarplata.ru/areas/1"
                    },
                    "company_id": null,
                    "employer": null
                },
                {
                    "start": "2005-01-01",
                    "end": "2009-03-01",
                    "company": "zarplata",
                    "area": {
                        "id": "1",
                        "name": "Москва",
                        "url": "https://api.zarplata.ru/areas/1"
                    },
                    "industries": [
                        {
                            "id": "7.513",
                            "name": "Интернет-компания (поисковики, платежные системы, соц.сети, информационно-познавательные и развлекательные ресурсы, продвижение сайтов и прочее)"
                        }
                    ],
                    "company_url": "http://hr.zarplata.ru",
                    "company_id": "1455",
                    "employer": {
                        "alternate_url": "http://hr.zarplata.ru/employer/1455",
                        "id": "1455",
                        "logo_urls": {
                            "90": "http://hr.zarplata.ru/employer/logo/1455"
                        },
                        "name": "zarplata",
                        "url": "https://api.zarplata.ru/employers/1455"
                    }
                }
            ],
            "gender": {
                "id": "male",
                "name": "Мужской"
            },
            "salary": {
                "amount": 1000000,
                "currency": "RUR"
            },
            "photo": {
                "medium": "http://hr.zarplata.ru/...",
                "small": "http://hr.zarplata.ru/...",
                "id": "1337"
            },
            "owner": {
                "comments": {
                    "url": "https://api.zarplata.ru/applicant_comments/123456",
                    "counters": {
                        "total": 7
                    }
                }
            },
            "negotiations_history": {
                "url": "https://api.zarplata.ru/resumes/0123456789abcdef/negotiations_history"
            },
            "last_negotiation": {
                "employer_state": {
                    "id": "offer",
                    "name": "Предложение о работе"
                },
                "created_at": "2017-08-10T13:09:28+0300"
            }
        }
    ]
}
```

<a name="resume-keys"></a>
Параметры:

* `last_name` — фамилия;
* `first_name` — имя;
* `middle_name` — отчество;
* `birth_date` — день рождения (ГГГГ-ММ-ДД);
* `gender` — пол. Элемент справочника [gender](dictionaries.md);
* `photo` — фотография пользователя. см. [артефакты](artifacts.md);
* `portfolio` — портфолио пользователя. см. [артефакты](artifacts.md);
* `area` — город проживания. Элемент справочника [areas](areas.md);
* `metro` — ближайшая станция метро. Элемент справочника [metro](metro.md). Если передать метро не принадлежащее переданной `area`, поле проигнорируется
  Имеет смысл указывать только для `area` с метро;
* `relocation` — возможен ли переезд в другой город. Состоит из полей:
  * `type` — элемент справочника [relocation_type](dictionaries.md);
  * `area` — город, в который возможен переезд (список). Имеет смысл
    только с соответствующим полем `type`. Элемент справочника
    [areas](areas.md);
* `business_trip_readiness` — готовность к командировкам. Элемент справочника
  [business_trip_readiness](dictionaries.md#business_trip_readiness)
* `contact` — контактная информация (список).
  Про обязательность полей и данных смотрите в [условиях заполнения контактов](#conditions-contacts).
  Состоит из полей:
  * `type` — элемент справочника [preferred_contact_type](dictionaries.md)
  * `value` — значение контакта. Для телефона состоит из четырех полей (`country `, `city`, `number`, `formatted`),
    для электронного адреса — строка.
  * `preferred` — предпочитаемый вид связи (`true` или `false`);
  * `comment` — комментарий к контакту;
* `site` — присутствие на других сайтах. Состоит из полей:
  * `type` — тип сайта. Элемент справочника
    [resume_contacts_site_type](dictionaries.md);
  * `url` — ссылка на профиль, либо идентификатор на стороннем сайте/сервисе;
* `title` — желаемая должность;
* `specialization` — специализация соискателя (список). Элемент справочника
  [specializations](specializations.md);
* `professional_roles` — профессиональные роли соискателя (список). Элемент справочника
  [professional_roles](professional_roles.md);
* `salary` — желаемая зарплата. Состоит из полей:
  * `amount` — сумма;
  * `currency` — идентификатор [валюты](dictionaries.md);
* `employments` — занятость. Элементы справочника [employment](dictionaries.md)
* `schedules` — график работы. Список из элементов справочника [schedule](dictionaries.md)
* `education` — образование. Состоит из полей:
  * `elementary` — среднее образование (список). Обычно заполняется только
    при отсутствии высшего образования. Состоит из полей:
    * `year` — год окончания;
    * `name` — название учебного заведения;
  * `additional` — курсы повышения квалификации (список). Состоит из полей:
    * `organization` — организация, проводившая курс;
    * `name` — название курса;
    * `result` — специальность / специализация;
    * `year` — год окончания;
  * `attestation` — тесты, экзамены (список):
    * `organization` — организация, проводившая тест или экзамен;
    * `name` — название тест или экзамена;
    * `result` — специальность / специализация;
    * `year` — год сдачи;
  * `primary` — образование выше среднего (список). Состоит из полей:
    * `name` — название учебного заведения;
    * `name_id` — идентификатор учебного заведения, можно получить из
      [подсказок по названиям вузов](suggests.md#universities);
    * `organization` — факультет;
    * `organization_id` — идентификатор факультета, можно получить из
      [справочника факультетов](faculties.md);
    * `result` — специальность / специализация;
    * `result_id` — идентификатор специальности / специализации, можно
      получить из
      [подсказок по специализациям](suggests.md#specializations);
    * `year` — год окончания;
  * `level` — уровень образования. Элемент справочника
    [education_level](dictionaries.md)
* `language` — владение языками (список).
  * `id` - значение из справочника [languages](languages.md)
  * `level` - значение из справочника [language_level](dictionaries.md)
* `experience` — опыт работы (список). Состоит из полей:
  * `company` — организация;
  * `company_id` — идентификатор организации, можно получить из
    [подсказок по организациям](suggests.md#companies);
  * `area` — регион расположения организации. Элемента справочника
    [areas](areas.md);
  * `company_url` — сайт компании;
  * `industries` — отрасли компании. Элемент справочника
    [/industries](industries.md)
  * `position` — должность;
  * `start` — начало работы (ГГГГ-ММ-ДД);
  * `end` — окончание работы (ГГГГ-ММ-ДД);
  * `description` — обязанности, функции, достижения;
* `skills` — дополнительная информация, описание навыков в свободной форме;
* `skill_set` — ключевые навыки (список уникальных строк).
* `citizenship` — гражданство (список). Элемента справочника [areas](areas.md);
* `work_ticket` — разрешение на работу (список). Элемента справочника
  [areas](areas.md);
* `travel_time` — желательное время в пути до работы. Элемент справочника
  [travel_time](dictionaries.md);
* `recommendation` — рекомендации (список). Состоит из полей:
  * `name` — имя;
  * `position` — должность;
  * `organization` — организация;
* `resume_locale` — локаль резюме. Элемент справочника [локали резюме](locales.md).
* `driver_license_types` - cписок категорий водительских прав соискателя. Элемент справочника [тип водительских прав](dictionaries.md).
* `has_vehicle` - наличие личного автомобиля у соискателя
* `hidden_fields` - [скрытые поля](#hidden-fields) в резюме (список). Элемент справочника [resume_hidden_fields](dictionaries.md).
* `access` - [видимость резюме](#access_type)
  * `type` - тип видимости. Элемент справочника [resume_access_type](dictionaries.md)


Контактная информация (ФИО) будет присутствовать только после [открытия контактой информации в резюме](/docs/payable/resume.md)

Для получения полной информации необходимо запросить [полное резюме](https://github.com/zarplata/api/blob/master/docs/resumes.md#item).
У соискателя запрос резюме будет отражён в истории просмотров.

Настройки вывода полей в поиске резюме на сайте не влияют на выдачу в API.

Возвращаемые результаты группируются по соискателю: один и тот же соискатель не может вернуться в выборке несколько раз. 
Если у соискателя есть несколько резюме, которые подходят под запрос, то только одно из его резюме вернется в качестве элемента в массиве `items`. 
Поле `found` содержит количество найденных соискателей. `per_page` работает по этому полю.

Резюме выводится не целиком. В объекте опыта отсутствует описание
(поле `description`), а также должность (поле `position`) доступна только в
последнем опыте. Образование выводится только основное.

Дополнительно работодателю выдаются следующие поля:
* `owner.comments.url` — содержит url, GET запрос на который возвращает
[список комментариев к владельцу резюме](https://github.com/zarplata/api/blob/master/docs/applicant_comments.md#list)
* `owner.comments.counters.total` — общее количество таких комментариев
* `last_negotiation` — информация о последнем статусе в истории откликов/приглашений. Поля `employer_state` и
`created_at` аналогичны соответствующим полям в
[истории откликов/приглашений по резюме](https://github.com/zarplata/api/blob/master/docs/resume_negotiations_history.md#response).

## Ошибки

* `400 Bad Request` — в случае ошибки в переданных полях.
* `403 Forbidden` — ошибка авторизации или отсутствие доступа у работодателя. Дополнительно к коду
   могут вернуться [причины ошибки](/docs/errors.md#ошибки-доступа-к-платному-методу).
