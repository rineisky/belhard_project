# Ресурс типы пользователей

## Получение списка всех типов пользователей

Request:
```http request
GET http://localhost:8000/user-types
```

Response (code 200):
```json
[
    {
        "id": "ADMIN",
        "name": "Administrator"
    },
    {
        "id": "USER",
        "name": "User"
    }
]
```

## Создание типа пользователя

Request:
```http request
POST http://localhost:8000/user-types
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

## Просмотр информации по конкретному типу пользователя

Request:
```http request
GET http://localhost:8000/user-types/{id}
```

Response (code 200):
```json
{
    "id": "ADMIN",
    "name": "Administrator"
}
```

## Редактирование конкретного типа пользователя

Request:
```http request
PUT http://localhost:8000/user-types/{id}
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

## Удаление конкретного типа пользователя

```http request
DELETE http://localhost:8000/user-types/{id}
```

Response (code 200):
```json
{
    "id": "ADMIN",
    "name": "Administrator"
}
```