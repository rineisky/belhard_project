# Ресурс типы доставки

## Получение списка всех типов доставки

Request:
```http request
GET http://localhost:8000/delivery-types
```

Response (code 200):
```json
[
    {
        "id": "DELIVERY",
        "name": "Delivery"
    },
    {
        "id": "SELF-PICKUP",
        "name": "Self-pickup"
    }
]
```

## Создание типа доставки

Request:
```http request
POST http://localhost:8000/delivery-types
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

## Просмотр информации по конкретному типу доставки

Request:
```http request
GET http://localhost:8000/delivery-types/{delivery_type_id}
```

Response (code 200):
```json
{
    "id": "DELIVERY",
    "name": "Delivery"
}
```

## Редактирование конкретного типа доставки

Request:
```http request
PUT http://localhost:8000/delivery-types/{delivery_type_id}
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
DELETE http://localhost:8000/delivery-types/{delivery_type_id}
```

Response (code 200):
```json
{
    "id": "DELIVERY",
    "name": "Delivery"
}
```