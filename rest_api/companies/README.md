# Ресурс компании-изготовители

## Получение списка всех компаний-изготовителей

Request:
```http request
GET http://localhost:8000/companies
```

Response (code 200):
```json
[
    {
        "id": 1,
        "name": "Some Big Company",
        "address": {
            "id": 1,
            "country": "Belarus",
            "city": "Minsk",
            "street": "Nezavisimosti",
            "house": "56",
            "postal_code": "220022"
        }
    }
]
```

## Создание компании-изготовителя

Request:
```http request
POST http://localhost:8000/companies
```

Payload создание, когда адрес уже есть:
```json
{
    "name": "Some Big Company",
    "address": {
        "id": 1
    }
}
```

Payload создание, когда адреса еще нет:
```json
{
    "name": "Some Big Company",
    "address": {
        "country": "Belarus",
        "city": "Minsk",
        "street": "Nezavisimosti",
        "house": "56",
        "postal_code": "220022"
    }
}
```

Response (code 201):
```json
{
    "id": 1,
    "name": "Some Big Company",
    "address": {
        "id": 1,
        "country": "Belarus",
        "city": "Minsk",
        "street": "Nezavisimosti",
        "house": "56",
        "postal_code": "220022"
    }
}
```

## Просмотр информации по конкретной компании

Request:
```http request
GET http://localhost:8000/companies/{company_id}
```

Response (code 200):
```json
{
    "id": 1,
    "name": "Some Big Company",
    "address": {
        "id": 1,
        "country": "Belarus",
        "city": "Minsk",
        "street": "Nezavisimosti",
        "house": "56",
        "postal_code": "220022"
    }
}
```

## Редактирование конкретной компании

Request:
```http request
PUT http://localhost:8000/companies/{company_id}
```

Payload:
```json
{
    "name": "Some Little Company"
}
```

Response (code 200):
```json
{
    "id": 1,
    "name": "Some Little Company",
    "address": {
        "id": 1,
        "country": "Belarus",
        "city": "Minsk",
        "street": "Nezavisimosti",
        "house": "56",
        "postal_code": "220022"
    }
}
```

## Удаление конкретной компании

```http request
DELETE http://localhost:8000/companies/{company_id}
```

Response (code 200):
```json
{
    "id": 1,
    "name": "Some Little Company",
    "address": {
        "id": 1,
        "country": "Belarus",
        "city": "Minsk",
        "street": "Nezavisimosti",
        "house": "56",
        "postal_code": "220022"
    }
}
```

## Получение списка товаров конкретного изготовителя

```http request
GET http://localhost:8000/companies/{company_id}/items
```

## Добавление товара конкретного изготовителя

```http request
POST http://localhost:8000/companies/{company_id}/items
```

## Получение информации о конкретном товаре конкретного изготовителя

```http request
GET http://localhost:8000/companies/{company_id}/items/{item_id}
```

## Редактирование информации конкретного товара конкретного изготовителя

```http request
PUT http://localhost:8000/companies/{company_id}/items/{item_id}
```

## Удаление конкретного товара конкретного изготовителя

```http request
DELETE http://localhost:8000/companies/{company_id}/items/{item_id}
```