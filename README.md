# Зарплата.ру API

Зарплата.ру API — это инструментарий для интеграции
[Зарплата.ру](http://zarplata.ru/) в ваш продукт.

Для начала ознакомьтесь с [общей информацией](docs/general.md) по работе API.

Зарегистрированное приложение может запрашивать у пользователей zarplata.ru
разрешение доступа к их персональным данным, без получения и хранения их
логина и пароля.


> ‼️ Обратите внимание на [Поддержку нового каталога специализаций (профессиональных ролей)](docs/role_catalog_article.md) .

> Для уточнения информации об API необходимо обратиться к Вашему персональному менеджеру или позвонить по телефону:
> +7 800 234‑35‑00

## [OpenAPI](https://api.zarplata.ru/openapi/redoc)

Доступная в [OpenAPI](https://api.zarplata.ru/openapi/redoc) документация будет со временем дополняться.
Методы, описанные в данной документации и доступные в OpenAPI, имеют соответствующую ссылку.

Спецификация Зарплата.ру API: [openapi.yml](https://api.zarplata.ru/openapi/specification/public).

<a name="content"></a>
## Содержание

Пометки в документации:

* <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> –
  актуально для анонимных запросов, не требует авторизации.
* <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> – актуально для запросов от имени приложения, требует [авторизацию приложения](docs/authorization_for_application.md)
* <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/> –
  актуально для запросов от имени работодателя, требует  [авторизацию пользователя](docs/authorization_for_user.md).


<a name="general"></a>
### Общая информация

* [Общая информация](docs/general.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Авторизация](docs/authorization.md) <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Кэширование](docs/cache.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Ошибки и коды ответов](docs/errors.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Новая модель работы с базой резюме (поддержка в API)](docs/payable/resume.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Новый каталог специализаций (профессиональных ролей). Поддержка в API Зарплата.ру](docs/role_catalog_article.md)  <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>

<a name="resources"></a>
<a name="context"></a>
### Контекст

* [Информация об авторизованном пользователе или приложении](docs/me.md) <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Получение информации об авторизованном пользователе](docs/me.md#user-info) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Редактирование информации авторизованного пользователя](docs/me.md#user-edit) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Получение информации об авторизованном приложении](docs/me.md#application-info) <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/>
* Информация о менеджере
  * [Рабочие аккаунты менеджера](docs/manager_accounts.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Предпочтения менеджера](docs/manager_settings.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Локализация](docs/locales.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>


<a name="resume"></a>
### Резюме

* [Поиск резюме](docs/resumes_search.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Сохраненные поиски резюме](docs/resumes_saved_searches.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Список сохраненных поисков резюме](docs/resumes_saved_searches.md#resumes-saved-search-list) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Получение единичного сохраненного поиска резюме](docs/resumes_saved_searches.md#resumes-saved-search-item) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Создание нового сохраненного поиска резюме](docs/resumes_saved_searches.md#resumes-saved-search-create) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Обновление сохраненного поиска резюме](docs/resumes_saved_searches.md#resumes-saved-search-update) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Удаление сохраненного поиска резюме](docs/resumes_saved_searches.md#resumes-saved-search-delete) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Передача сохраненного поиска резюме другому менеджеру](docs/resumes_saved_searches.md#resumes-saved-search-move-to-other-manager) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Просмотр резюме](docs/employer_resumes.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [История откликов/приглашений по резюме](docs/resume_negotiations_history.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>

<a name="vacancies"></a>
### Вакансии

* [Получение вакансий](docs/vacancies.md) <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Поиск по вакансиям](docs/vacancies.md#search) <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
    * [Кластеры](docs/clusters.md) <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
    * [Описание использованных параметров](docs/vacancies_search_arguments.md) <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Получение информации о вакансии](docs/vacancies.md#item) <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Поиск по вакансиям, похожим на вакансию](docs/vacancies.md#similar) <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Работа с вакансиями](docs/employer_vacancies.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Возможные варианты публикации вакансий](docs/employer_vacancies.md#available_types) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Публикация вакансий](docs/employer_vacancies.md#creation) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Редактирование вакансий](docs/employer_vacancies.md#edit) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Продление вакансий](docs/employer_vacancies.md#prolongate) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Список опубликованных вакансий](docs/employer_vacancies.md#active) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Архивация вакансий](docs/employer_vacancies.md#archive) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Список архивных вакансий](docs/employer_vacancies.md#archived) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Удаление вакансий](docs/employer_vacancies.md#hide) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Список удаленных вакансий](docs/employer_vacancies.md#hidden) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Список улучшений для вакансии](docs/employer_vacancy_upgrades.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Статистика по вакансии](docs/employer_vacancies.md#stats) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Черновики вакансий](docs/vacancy_drafts.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Получение списка черновиков](docs/vacancy_drafts.md#draft_list) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Удаление черновика](docs/vacancy_drafts.md#draft_delete) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Отмена автопубликации](docs/vacancy_autopublication.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>

<a name="applicants"></a>
### Соискатели

* [Комментарии к соискателю](docs/applicant_comments.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>


<a name="employers"></a>
### Работодатели/компании

* [Поиск компаний](docs/employers.md#search) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Получение информации о компании](docs/employers.md#item) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>

<a name="employer_managers"></a>
### Менеджеры работодателя

* [Менеджеры](docs/employer_managers.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Добавление менеджера](docs/employer_managers.md#add) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Редактирование менеджера](docs/employer_managers.md#edit) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Удаление менеджера](docs/employer_managers.md#delete) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Справочник менеджеров работодателя](docs/employer_managers.md#list) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Получение информации о менеджере](docs/employer_managers.md#item) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Дневной лимит просмотра резюме для текущего менеджера](docs/employer_manager_resume_limit.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>

<a name="negotiations"></a>
### Переписка (отклики/приглашения)

* [Переписка для работодателя](docs/employer_negotiations.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Модель работы, термины и процедуры](docs/employer_negotiations.md#model) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Общее описание процесса работы с откликами/приглашениями](docs/employer_negotiations.md#flow) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Коллекции и работодательские состояния откликов/приглашений](docs/employer_negotiations.md#collections) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Список откликов/приглашений](docs/employer_negotiations.md#negotiations-list) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Просмотр отклика/приглашения](docs/employer_negotiations.md#get-negotiation) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Работа с сообщениями по отклику/приглашению для работодателя](docs/employer_negotiations.md#get-messages) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Приглашение соискателя на вакансию](docs/employer_negotiations.md#add-invite) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Действия по отклику/приглашению (смена состояния)](docs/employer_negotiations.md#actions) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Статистика по работе с откликами](docs/employer_negotiations_statistics.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Тексты сообщений](docs/negotiation_message_templates.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Инструменты оценки](docs/assessment.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>


<a name="dictionaries"></a>
### Справочники

* [Регионы](docs/areas.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Специализации](docs/specializations.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Метро](docs/metro.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Языки](docs/languages.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Отрасли компаний](docs/industries.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Учебные заведения](docs/educational_institutions.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Основная информация об учебных заведениях](docs/university.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Факультеты учебных заведений](docs/faculties.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Справочники работодателя](docs/employer_dictionaries.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Адреса](docs/employer_addresses.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Типы и права менеджера](docs/employer_managers.md#dict) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Менеджеры работодателя](docs/employer_managers.md#list) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Департаменты](docs/employer_departments.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Тесты](docs/employer_tests.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Регионы вакансий](docs/employer_vacancy_areas_active.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [Брендированные шаблоны вакансий](docs/employer_vacancy_branded_templates.md) <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Ключевые навыки](docs/key_skills.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
* [Прочие справочники](docs/dictionaries.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>


<a name="suggests"></a>
### Подсказки (autosuggest, autocomplete)

* [Подсказки](docs/suggests.md) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [по названиям университетов](docs/suggests.md#educational_institutions) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [по организациям](docs/suggests.md#companies) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [по специализациям](docs/suggests.md#specializations) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [по проффесиональным ролям](docs/suggests.md#proff-roles) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [по ключевым навыкам](docs/suggests.md#key-skills) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [по должностям](docs/suggests.md#positions) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [по регионам](docs/suggests.md#areas) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>
  * [по ключевым словам поиска вакансий](docs/suggests.md#vacancy-search-keyword) <img alt="anonymous" src="http://zarplata.github.io/api/badges/anon.png"/> <img alt="client" src="http://zarplata.github.io/api/badges/client.png"/> <img alt="employer" src="http://zarplata.github.io/api/badges/emp.png"/>


## Поддержка, обратная связь, новости

Общайтесь с нами через почту support@zarplata.ru.

Если вы нашли баг в работе Зарплата.ру API или
[issues](https://github.com/zarplata/api/issues), возможно, про него мы уже знаем и
чиним. Если нет, лучше всего сообщить о нём там. Там же вы можете оставлять свои
пожелания и предложения.

Если вы нашли проблему на одном из сайтов Зарплата.ру,
[напишите в поддержку по сайту](https://zarplata.ru/feedback) или в
[сообщество поддержки](https://feedback.zarplata.ru/).

За новостями вы можете следить по
[коммитам](https://github.com/zarplata/api/commits/master) в этом репозитории.
[RSS](https://github.com/zarplata/api/commits/master.atom).
