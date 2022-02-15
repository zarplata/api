# Справочник профессиональных ролей

`GET /professional_roles`

Возвращает профессиональные роли, их категории и другую информацию о профессиональных ролях. Профессиональные роли приходят на замену [специализациям](specializations.md). 
В настоящее время профессиональные роли и специализации используются параллельно для обеспечения обратной совместимости.

```json5
{
  "categories":[
    {
      "id":"19",
      "name":"Автомобильный бизнес",
      "roles":[
        {
          "id":"4",
          "name":"Автомойщик",
          "accept_incomplete_resumes":true,
          "is_default":false
        },
        {
          "id":"5",
          "name":"Автослесарь, автомеханик",
          "accept_incomplete_resumes":true,
          "is_default":false
        }
      ]
    }
  ]
}
```

Имя | Тип | Описание
 --- | --- | ---
categories | array | Информация о категории профессиональной роли
categories.roles | array | Список профессиональных ролей, входящих в эту категорию
categories.roles.accept_incomplete_resumes | boolean | Информация о категории профессиональной роли
categories.roles.is_default | boolean | Дефолтная роль

