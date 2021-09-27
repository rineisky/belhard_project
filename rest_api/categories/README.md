# Ресурс категории товаров

## Получение списка всех категорий

Запрос:
```http request
GET http://localhost:8000/categories
```

Коды ответа:
- `200 OK` - успешно выполнено. Получен список категорий

Пример ответа при коде 200:
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

Запрос:
```http request
POST http://localhost:8000/categories
```

Коды ответа:
- `201 Created` - успешно создано. Создана новая категория

Пример запроса:
```json
{
    "id": "NEW",
    "name": "New"
}
```

Пример ответа при коде 201:
```json
{
    "id": "NEW",
    "name": "New"
}
```

## Просмотр информации по конкретной категории

Запрос:
```http request
GET http://localhost:8000/categories/{category_id}
```

Коды ответа:
- `200 OK` - успешно выполнено. Получена информация о конкретной категории
- `404 Not Found` - не найдено. Категория с заданным `category_id` не существует

Пример ответа при коде 200:
```json
{
    "id": "GPU", 
    "name": "Graphics Processing Unit"
}
```

## Редактирование конкретной категории

Запрос:
```http request
PUT http://localhost:8000/categories/{category_id}
```

Коды ответа:
- `200 OK` - успешно выполнено. Информация категории успешно отредактирована
- `204 No Content` **OPTIONAL** - обновление не произошло, так как нет новых данных
- `400 Bad Request` **OPTIONAL** - если данный запрос нельзя выполнить с переданным телом
- `403 Forbidden` **OPTIONAL** - пользователю запрещен доступ к ресурсу
- `404 Not Found` - не найдено. Категория с заданным `category_id` не существует
- `405 Method Not Allowed` **OPTIONAL** - если данный метод не поддерживается
- `422 Unprocessable Entity` **OPTIONAL** - если тело запроса содержит ошибки (напр. не тот тип данных)

Пример тела запроса:
```json
{
    "id": "NEW",
    "name": "New"
}
```

Пример ответа при коде 200:
```json
{
    "id": "NEW",
    "name": "New"
}
```

## Удаление конкретной категории

```http request
DELETE http://localhost:8000/categories/{category_id}
```

Response (code 200):
```json
{
    "id": "GPU", 
    "name": "Graphics Processing Unit"
}
```

## Получение списка товаров для конкретной категории

```http request
GET http://localhost:8000/categories/{category_id}/items
```

## Добавление товара в конкретную категорию

```http request
POST http://localhost:8000/categories/{category_id}/items
```

## Получение информации о конкретном товаре в конкретной категории

```http request
GET http://localhost:8000/categories/{category_id}/items/{item_id}
```

## Редактирование информации конкретного товара конкретной категории

```http request
PUT http://localhost:8000/categories/{category_id}/items/{item_id}
```

## Удаление конкретного товара в конкретной категории

```http request
DELETE http://localhost:8000/categories/{category_id}/items/{item_id}
```