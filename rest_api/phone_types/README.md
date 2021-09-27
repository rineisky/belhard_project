# Ресурс типы номеров телефонов

## Получение списка всех типов номеров телефонов

Request:
```http request
GET http://localhost:8000/phone-types
```

Response (code 200):
```json
[
    {
        "id": "WORK",
        "name": "Work phone number"
    },
    {
        "id": "HOME",
        "name": "Home phone number"
    },
    {
        "id": "MOBILE",
        "name": "Mobile phone number"
    },
    {
        "id": "OTHER",
        "name": "Other phone number"
    }
]
```

## Создание типа номера телефона

Request:
```http request
POST http://localhost:8000/phone-types
```

Payload:
```json
{
    "id": "NEW",
    "name": "New"
}
```

Response (code 201):
```json
{
    "id": "NEW",
    "name": "New"
}
```

## Просмотр информации по конкретному типу номера телефона

Request:
```http request
GET http://localhost:8000/phone-types/{id}
```

Response (code 200):
```json
{
    "id": "WORK",
    "name": "Work phone number"
}
```

## Редактирование конкретного типа номера телефона

Request:
```http request
PUT http://localhost:8000/phone-types/{id}
```

Payload:
```json
{
    "id": "NEW",
    "name": "New"
}
```

Response (code 200):
```json
{
    "id": "NEW",
    "name": "New"
}
```

## Удаление конкретного типа номера телефона

```http request
DELETE http://localhost:8000/phone-types/{id}
```

Response (code 200):
```json
{
    "id": "WORK",
    "name": "Work phone number"
}
```