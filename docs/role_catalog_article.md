# Новый каталог специализаций (профессиональных ролей). Поддержка в API Зарплата.ру.

[В Зарплата.ру появился новый каталог специализаций профессиональных ролей.

##### ВАЖНО: На время, пока производители интегрированных систем не поддержат новый каталог, в интегрированной системе клиенты могут использовать и "старый" каталог специализаций при публикации, наш сервис автоматически подберет значение нового каталога по параметрам опубликованной вакансии ( [подробнее](#backward) ).

В API так же добавлена поддержка использования нового каталога специализаций (профессиональных ролей), а так же реализована [обратная совместимость](#backward) для интеграций использующих старый каталог специализаций. 

Все ранее опубликованные вакансии автоматически получили значения из нового каталога профессиональных ролей, дополнительно изменять эти вакансии не требуется.

## Подробнее о поддержке нового каталога в API:

Новый каталог специализаций (профессиональных ролей, поле - `professional_roles`) приходит на замену [специализациям](https://github.com/zarplata/api/blob/main/docs/specializations.md). В настоящее время новый каталог специализаций (профессиональных ролей) и устаревший каталог специализации используются параллельно для обеспечения обратной совместимости.

Для нового каталога специализаций (профессиональных ролей) создан отдельный [справочник](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki/operation/get-professional-roles-dictionary) и [подсказки (autosuggest, autocomplete)](https://api.zarplata.ru/openapi/redoc#tag/Podskazki/operation/get-professional-roles-suggests) 

На текущий момент поддержка нового каталога специализаций (профессиональных ролей) не полностью завершена в API, ниже представлен список методов с поддержкой нового каталога (список будет пополняться со временем)

### Для вакансий:

1. [Публикация вакансий](https://github.com/zarplata/api/blob/main/docs/employer_vacancies.md#creation) - добавлен параметр `with_professional_roles` и поле `professional_roles`. 

2. [Условия заполнения полей при добавлении и редактировании вакансий](https://github.com/zarplata/api/blob/main/docs/employer_vacancies.md#%D1%83%D1%81%D0%BB%D0%BE%D0%B2%D0%B8%D1%8F-%D0%B7%D0%B0%D0%BF%D0%BE%D0%BB%D0%BD%D0%B5%D0%BD%D0%B8%D1%8F-%D0%BF%D0%BE%D0%BB%D0%B5%D0%B9-%D0%BF%D1%80%D0%B8-%D0%B4%D0%BE%D0%B1%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B8-%D0%B8-%D1%80%D0%B5%D0%B4%D0%B0%D0%BA%D1%82%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B8-%D0%B2%D0%B0%D0%BA%D0%B0%D0%BD%D1%81%D0%B8%D0%B9) - добавлен параметр `with_professional_roles` и поле `professional_roles`. 

3. [Просмотр вакансии](https://github.com/zarplata/api/blob/main/docs/vacancies.md#item) - добавлено поле `professional_roles`

4. [Публикация вакансии на основе черновика](https://api.zarplata.ru/openapi/redoc#tag/Chernoviki-vakansij/operation/publish-vacancy-from-draft) - добавлен параметр `with_professional_roles`

5. [Редактирование вакансии](https://github.com/zarplata/api/blob/main/docs/employer_vacancies.md#edit) - добавлен параметр `with_professional_roles`.

### Для резюме:

1. [Просмотр резюме](https://github.com/zarplata/api/blob/main/docs/employer_resumes.md#item) - добавлено поле `professional_roles`

### Для поисковых методов:

1. [Поиск резюме](https://github.com/zarplata/api/blob/main/docs/resumes_search.md) - добавлен параметр `professional_role` (при использовании параметра `specialization` работает режим обратной совместимости, т.е. автоматичски будет подобрано значение из справочника `professional_role`)

2. [Поиск по вакансиям](https://github.com/zarplata/api/blob/main/docs/vacancies.md#search) - добавлен параметр `professional_role` (при использовании параметра `specialization` работает режим обратной совместимости, т.е. автоматичски будет подобрано значение из справочника `professional_role`)

<a name="backward"></a>
## Обратная совместимость нового каталога в API:

Поддержка обратной совместимости будет осуществляться до **1-го декабря 2022 года**. После этого срока, все интегрированные системы должны будут перейти полностью на использование нового каталога специализаций (профессиональных ролей), поддержка обратной совместимости будет отключена и использование [специализаций](https://github.com/zarplata/api/blob/main/docs/specializations.md) будет приводить к ошибкам.

Процесс выбора специализации из нового каталога специализаций (профессиональных ролей) происходит автоматически после публикации вакансии/резюме (ранее опубликованные вакансии так же автоматически получили значения из нового каталога специализаций (профессиональных ролей), они не требуют каких-то дополнительных действий) и основан на пользовательском опыте, а также поведении пользователей. Т.е. мы подберем оптимальную позицию из нового каталога специализаций (профессиональных ролей) не на основе простого маппинга, а на основе реальной пользовательской активности (на основе статистических закономерностей на рынке труда - групп резюме и вакансий, между которыми происходят отклики и приглашения на собеседования)

Например, при использовании метода публикации вакансий, достаточно передать все значение из устаревшего справочника специализации, после публикации (с небольшим временным лагом) в данной вакансии будет автоматически проставлена наиболее подходящее значение из нового каталога специализаций (профессиональных ролей).
