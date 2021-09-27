# Ресурс заказы

## Получение списка заказов

```http request
GET http://localhost:8000/orders
```

## Добавление нового заказа

```http request
POST http://localhost:8000/orders
```

## Получение информации о конкретном заказе

```http request
GET http://localhost:8000/orders/{order_id}
```

## Редактирование информации конкретного заказа

```http request
PUT http://localhost:8000/orders/{order_id}
```

## Удаление конкретного заказа

```http request
DELETE http://localhost:8000/orders/{order_id}
```

## Получение списка товаров конкретного заказа

```http request
GET http://localhost:8000/orders/{order_id}/items
```

## Добавление товара в конкретный заказ

```http request
POST http://localhost:8000/orders/{order_id}/items
```

## Получение информации о конкретном товаре конкретного заказа

```http request
GET http://localhost:8000/orders/{order_id}/items/{item_id}
```

## Редактирование информации конкретного товара конкретного заказа

```http request
PUT http://localhost:8000/orders/{order_id}/items/{item_id}
```

## Удаление конкретного товара из конкретного заказа

```http request
DELETE http://localhost:8000/orders/{order_id}/items/{item_id}
```