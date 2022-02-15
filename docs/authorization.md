# Авторизация

Для выполнения большинства запросов к API необходимо передавать access-токен.
Авторизация осуществляется по протоколу [OAuth 2.0](#links).

Зарегистрированное приложение может запрашивать у пользователей zarplata.ru
разрешение доступа к их персональным данным, без получения и хранения их
логина и пароля.

API поддерживает следующие уровни авторизации:
* [авторизация приложения](authorization_for_application.md)
* [авторизация пользователя](authorization_for_user.md)

> Внимание! Для авторизации нужно использовать домен zarplata.ru, домен m.zarplata.ru больше не доступен.

* [Получение access-токена](#get-access_token)
* [Использование access-токена](#use-access_token)
* [Проверка access-токена](#check-access_token)
* [Полезные ссылки](#links)

<a name="get-access_token"></a>
## Получение access-токена

* Получение [токена приложения](authorization_for_application.md#get-client-auth)
* Получение [токена пользователя](authorization_for_user.md#get-auth)

<a name="use-access_token"></a>
## Использование access-токена

Приложение должно использовать полученный `access_token` для авторизации,
передавая его в заголовке в формате:

```Authorization: Bearer ACCESS_TOKEN```

[Описание ошибок авторизации](errors.md#oauth).

<a name="check-access_token"></a>
## Проверка access-токена

Для тестирования токена удобно использовать метод `/me`:

* [для авторизованного приложения](me.md#application-info)
* [для авторизованного пользователя](me.md#user-info)

<a name="links"></a>
## Полезные ссылки

* Подробная документация по протоколу: [RFC 6749](http://tools.ietf.org/html/rfc6749)
* Библиотека [ScribeJava](https://github.com/scribejava/scribejava),
  поддерживающая авторизацию в API zarplata.
  * [Habrahabr: ScribeJava — даже ваша бабушка сможет работать с OAuth](https://habrahabr.ru/company/hh/blog/278957/)