# Ресурс категории товаров

## Получение списка всех категорий:

Request:
```http request
GET http://localhost:8000/categories
```

Response (code 200):
```json
[
    {
        "id": "GPU",
        "name": "Graphics Processing Unit"
    },
    {
        "id": "CPU",
        "name": "Central Processing Unit"
    },
    ...
]
```

## Создание категории

Request:
```http request
POST http://localhost:8000/categories
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

## Просмотр информации по конкретной категории

Request:
```http request
GET http://localhost:8000/categories/{id}
```

Response (code 200):
```json
{
    "id": "GPU", 
    "name": "Graphics Processing Unit"
}
```

## Редактирование конкретной категории

Request:
```http request
PUT http://localhost:8000/categories/{id}
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

## Удаление конкретной категории

```http request
DELETE http://localhost:8000/categories/{id}
```

Response (code 200):
```json
{
    "id": "GPU", 
    "name": "Graphics Processing Unit"
}
```