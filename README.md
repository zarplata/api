# Зарплата.ру API

Зарплата.ру API — это инструментарий для интеграции
[Зарплата.ру](http://hr.zarplata.ru/) в ваш продукт.

Для начала ознакомьтесь с [общей информацией](https://api.zarplata.ru/openapi/redoc#section/Obshaya-informaciya) по работе API.

Зарегистрированное приложение может запрашивать у пользователей hr.zarplata.ru
разрешение доступа к их персональным данным, без получения и хранения их
логина и пароля.


> ‼️ Обратите внимание, что методы для работы с сообщениями в рамках отклика/приглашения от имени  
> [менеджера работодателя](docs/employer_negotiations.md#get-messages) устарели, и новые возможности чатов в них не будут поддерживаться. 
> В связи с этим переписка может некорректно отображаться. 

> Для уточнения информации об API необходимо обратиться к Вашему персональному менеджеру или позвонить по телефону:
> +7 800 234‑35‑00

## [OpenAPI](https://api.zarplata.ru/openapi/redoc)

Доступная в [OpenAPI](https://api.zarplata.ru/openapi/redoc) документация будет со временем дополняться.
Методы, описанные в данной документации и доступные в OpenAPI, имеют соответствующую ссылку.

Спецификация Зарплата.ру API: [openapi.yml](https://api.zarplata.ru/openapi/specification/public).

<a name="content"></a>
## Содержание

Пометки в документации:

* <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> –
  актуально для анонимных запросов, не требует авторизации.
* <img src="http://zarplata.github.io/api/badges/client.png" alt="client" /> – актуально для запросов от имени приложения, требует [авторизацию приложения](docs/authorization_for_application.md)
* <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" /> –
  актуально для бесплатных методов работодателя, требует  [авторизацию пользователя](docs/authorization_for_user.md).


<a name="general"></a>
### Общая информация

* [Общая информация](https://api.zarplata.ru/openapi/redoc#section/Obshaya-informaciya) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Условия использования сервиса API](https://dev.hr.zarplata.ru/admin/developer_agreement) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Требования к использованию логотипов](https://dev.hr.zarplata.ru/articles/logos) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Требования к названию приложений](https://dev.hr.zarplata.ru/articles/apps) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Авторизация](docs/authorization.md) <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Кэширование](docs/cache.md) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Ошибки и коды ответов](docs/errors.md) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Новая модель работы с базой резюме (поддержка в API)](docs/payable/resume.md) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />

<a name="resources"></a>
<a name="context"></a>
### Контекст

* Информация об авторизованном пользователе или приложении <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * Получение информации об авторизованном пользователе:
    * [Соискатель](https://api.zarplata.ru/openapi/redoc#tag/Informaciya-o-soiskatele/operation/get-current-user-info)
    * [Работодатель](https://api.zarplata.ru/openapi/redoc#tag/Informaciya-o-menedzhere/operation/get-current-user-info)
  * [Редактирование информации авторизованного пользователя](https://api.zarplata.ru/openapi/redoc#tag/Informaciya-o-soiskatele/operation/edit-current-user-info)
  * [Получение информации об авторизованном приложении](https://api.zarplata.ru/openapi/redoc#tag/Informaciya-o-prilozhenii/operation/get-current-user-info)
* Информация о менеджере
  * [Рабочие аккаунты менеджера](https://api.zarplata.ru/openapi/redoc#tag/Menedzhery-rabotodatelya/operation/get-manager-accounts) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Предпочтения менеджера](https://api.zarplata.ru/openapi/redoc#tag/Menedzhery-rabotodatelya/operation/get-manager-settings) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Локализация](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki/operation/get-locales) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />



<a name="resume"></a>
### Резюме

* [Поиск резюме](https://api.zarplata.ru/openapi/redoc#tag/Poisk-rezyume/operation/search-for-resumes) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Сохраненные поиски резюме](https://api.zarplata.ru/openapi/redoc#tag/Sohranennye-poiski-rezyume) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Список сохраненных поисков резюме](https://api.zarplata.ru/openapi/redoc#tag/Sohranennye-poiski-rezyume/operation/get-saved-resume-searches) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Получение единичного сохраненного поиска резюме](https://api.zarplata.ru/openapi/redoc#tag/Sohranennye-poiski-rezyume/operation/get-saved-resume-search) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Создание нового сохраненного поиска резюме](https://api.zarplata.ru/openapi/redoc#tag/Sohranennye-poiski-rezyume/operation/create-saved-resume-search) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Обновление сохраненного поиска резюме](https://api.zarplata.ru/openapi/redoc#tag/Sohranennye-poiski-rezyume/operation/update-saved-resume-search) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Удаление сохраненного поиска резюме](https://api.zarplata.ru/openapi/redoc#tag/Sohranennye-poiski-rezyume/operation/delete-saved-resume-search) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Передача сохраненного поиска резюме другому менеджеру](https://api.zarplata.ru/openapi/redoc#tag/Sohranennye-poiski-rezyume/operation/move-saved-resume-search) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Просмотр резюме](https://api.zarplata.ru/openapi/redoc#tag/Prosmotr-rezyume/operation/get-resume) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [История откликов/приглашений по резюме](https://api.zarplata.ru/openapi/redoc#tag/Otklikipriglasheniya-rabotodatelya/operation/get-resume-negotiations-history) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />

<a name="vacancies"></a>
### Вакансии

* [Получение вакансий](docs/vacancies.md) <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Поиск по вакансиям](https://api.zarplata.ru/openapi/redoc#tag/Poisk-vakansij/operation/get-vacancies) <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
    * [Кластеры](https://api.zarplata.ru/openapi/redoc#tag/Poisk-vakansij/Klastery-v-poiske-vakansij) <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Получение информации о вакансии](docs/vacancies.md#item) <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Поиск по вакансиям, похожим на вакансию](https://api.zarplata.ru/openapi/redoc#tag/Poisk-vakansij/operation/get-vacancies-similar-to-vacancy) <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Работа с вакансиями](docs/employer_vacancies.md) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Возможные варианты публикации вакансий](docs/employer_vacancies.md#available_types) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Публикация вакансий](docs/employer_vacancies.md#creation) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Редактирование вакансий](docs/employer_vacancies.md#edit) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Продление вакансий](docs/employer_vacancies.md#prolongate) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Список опубликованных вакансий](docs/employer_vacancies.md#active) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Архивация вакансий](docs/employer_vacancies.md#archive) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Список архивных вакансий](docs/employer_vacancies.md#archived) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Удаление вакансий](docs/employer_vacancies.md#hide) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Список удаленных вакансий](docs/employer_vacancies.md#hidden) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Список улучшений для вакансии](https://api.zarplata.ru/openapi/redoc#tag/Upravlenie-vakansiyami/operation/get-vacancy-upgrade-list) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Статистика по вакансии](docs/employer_vacancies.md#stats) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Просмотры вакансии](docs/employer_vacancies.md#visitors) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Черновики вакансий](https://api.zarplata.ru/openapi/redoc#tag/Chernoviki-vakansij) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Получение списка черновиков](https://api.zarplata.ru/openapi/redoc#tag/Chernoviki-vakansij/operation/get-vacancy-draft-list) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Удаление черновика](https://api.zarplata.ru/openapi/redoc#tag/Chernoviki-vakansij/operation/delete-vacancy-draft) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Создание черновика](https://api.zarplata.ru/openapi/redoc#tag/Chernoviki-vakansij/operation/create-vacancy-draft) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Публикация вакансий на основе черновика](https://api.zarplata.ru/openapi/redoc#tag/Chernoviki-vakansij/operation/publish-vacancy-from-draft) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Получение черновика](https://api.zarplata.ru/openapi/redoc#tag/Chernoviki-vakansij/operation/get-vacancy-draft) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Изменение черновика](https://api.zarplata.ru/openapi/redoc#tag/Chernoviki-vakansij/operation/change-vacancy-draft) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />

<a name="applicants"></a>
### Соискатели

* [Комментарии к соискателю](https://api.zarplata.ru/openapi/redoc#tag/Kommentarii-k-soiskatelyu) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />

<a name="employers"></a>
### Работодатели/компании

* [Поиск компаний](https://api.zarplata.ru/openapi/redoc#tag/Rabotodatel/operation/search-employer) <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Получение информации о компании](https://api.zarplata.ru/openapi/redoc#tag/Rabotodatel/operation/get-employer-info) <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Услуги работодателя](https://api.zarplata.ru/openapi/redoc#tag/Uslugi-rabotodatelya) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Авторизация работодателя](https://api.zarplata.ru/openapi/redoc#tag/Avtorizaciya-rabotodatelya) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Менеджеры работодателя](https://api.zarplata.ru/openapi/redoc#tag/Menedzhery-rabotodatelya) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />

<a name="employer_managers"></a>
### Менеджеры работодателя

* [Менеджеры](docs/employer_managers.md) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Добавление менеджера](docs/employer_managers.md#add) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Редактирование менеджера](docs/employer_managers.md#edit) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Удаление менеджера](docs/employer_managers.md#delete) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Справочник менеджеров работодателя](docs/employer_managers.md#list) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Получение информации о менеджере](docs/employer_managers.md#item) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Дневной лимит просмотра резюме для текущего менеджера](https://api.zarplata.ru/openapi/redoc#tag/Menedzhery-rabotodatelya/operation/get-employer-manager-limits) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />

<a name="negotiations"></a>
### Переписка (отклики/приглашения)

* [Переписка для работодателя](docs/employer_negotiations.md) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Модель работы, термины и процедуры](docs/employer_negotiations.md#model) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Общее описание процесса работы с откликами/приглашениями](docs/employer_negotiations.md#flow) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Коллекции и работодательские состояния откликов/приглашений](docs/employer_negotiations.md#collections) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Список откликов/приглашений](docs/employer_negotiations.md#negotiations-list) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Просмотр отклика/приглашения](docs/employer_negotiations.md#get-negotiation) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Работа с сообщениями по отклику/приглашению для работодателя](docs/employer_negotiations.md#get-messages) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Приглашение соискателя на вакансию](docs/employer_negotiations.md#add-invite) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Действия по отклику/приглашению (смена состояния)](docs/employer_negotiations.md#actions) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Отметить отклики прочитанными](https://api.zarplata.ru/openapi/redoc#tag/Otklikipriglasheniya-rabotodatelya/operation/post-negotiations-topics-read) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Статистика по работе с откликами](docs/employer_negotiations_statistics.md) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Тексты сообщений](docs/negotiation_message_templates.md) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Изменение шаблона ответа соискателю](https://api.zarplata.ru/openapi/redoc#tag/Otklikipriglasheniya-rabotodatelya/operation/put-mail-templates-item) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Инструменты оценки](docs/assessment.md)  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />


<a name="dictionaries"></a>
### Справочники
* [Справочники в OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Регионы](docs/areas.md) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Профессиональные роли](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki/operation/get-professional-roles-dictionary) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Станции метро в указанном городе](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki/operation/get-metro-stations-in-city) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Станции метро во всех городах](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki/operation/get-metro-stations) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Языки](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki/operation/get-languages) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Отрасли компаний](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki/operation/get-industries) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Учебные заведения](docs/educational_institutions.md) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Основная информация об учебных заведениях](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki/operation/get-educational-institutions-dictionary) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Факультеты учебных заведений](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki/operation/get-educational-institutions-dictionary) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Справочники работодателя](docs/employer_dictionaries.md) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Адреса](https://api.zarplata.ru/openapi/redoc#tag/Adresa-rabotodatelya) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Типы и права менеджера](docs/employer_managers.md#dict) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Менеджеры работодателя](docs/employer_managers.md#list) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Департаменты](https://api.zarplata.ru/openapi/redoc#tag/Informaciya-o-rabotodatele/operation/get-employer-departments) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Тесты](https://api.zarplata.ru/openapi/redoc#tag/Spravochniki-rabotodatelya/operation/get-tests-dictionary) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Регионы вакансий](https://api.zarplata.ru/openapi/redoc#tag/Informaciya-o-rabotodatele/operation/get-employer-vacancy-areas) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [Брендированные шаблоны вакансий](https://api.zarplata.ru/openapi/redoc#tag/Informaciya-o-rabotodatele/operation/get-vacancy-branded-templates-list) <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Ключевые навыки](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki/operation/get-skills) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Прочие справочники](https://api.zarplata.ru/openapi/redoc#tag/Obshie-spravochniki/operation/get-dictionaries) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />


<a name="suggests"></a>
### Подсказки (autosuggest, autocomplete)
* [Подсказки в OpenAPI](https://api.zarplata.ru/openapi/redoc#tag/Podskazki) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
* [Подсказки](docs/suggests.md) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [по названиям университетов](docs/suggests.md#educational_institutions) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [по организациям](docs/suggests.md#companies) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [по специализациям](docs/suggests.md#specializations) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [по ключевым навыкам](docs/suggests.md#key-skills) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [по должностям резюме](docs/suggests.md#resume-positions) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [по регионам](docs/suggests.md#areas) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />
  * [по ключевым словам поиска вакансий](docs/suggests.md#vacancy-search-keyword) <img src="http://zarplata.github.io/api/badges/anon.png" alt="anonymous" /> <img src="http://zarplata.github.io/api/badges/client.png" alt="client" />  <img src="http://zarplata.github.io/api/badges/emp.png" alt="employer" />


<a name="feedback"></a>
## Поддержка, обратная связь, новости

Общайтесь с нами через почту support@zarplata.ru.

Если вы нашли баг в работе Зарплата.ру API  загляните в
[issues](https://github.com/zarplata/api/issues), возможно, про него мы уже знаем и
чиним. Если нет, лучше всего сообщить о нём там. Там же вы можете оставлять свои
пожелания и предложения.

Если вы нашли проблему на одном из сайтов Зарплата.ру,
[напишите в поддержку по сайту](https://hr.zarplata.ru/feedback) или в
[сообщество поддержки](https://feedback.hr.zarplata.ru/).

За новостями вы можете следить по
[коммитам](https://github.com/zarplata/api/commits/master) в этом репозитории.
[RSS](https://github.com/zarplata/api/commits/master.atom).

Часто задаваемые вопросы собраны в [FAQ](docs/FAQ.md).
