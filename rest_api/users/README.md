# Ресурс пользователи

## Получение списка всех пользователей

```http request
GET http://localhost:8000/users
```

## Добавление нового пользователя

```http request
POST http://localhost:8000/users
```

## Получение информации о конкретном пользователе

```http request
GET http://localhost:8000/users/{login}
```

## Редактирование информации конкретного пользователя

```http request
PUT http://localhost:8000/users/{login}
```

## Удаление конкретного пользователя

```http request
DELETE http://localhost:8000/users/{login}
```

## Получение списка адресов конкретного пользователя

```http request
GET http://localhost:8000/users/{login}/addresses
```

## Добавление адреса конкретного пользователя

```http request
POST http://localhost:8000/users/{login}/addresses
```

## Получение информации об конкретном адресе конкретного пользователя

```http request
GET http://localhost:8000/users/{login}/addresses/{address_id}
```

## Редактирование информации конкретного адреса конкретного пользователя

```http request
PUT http://localhost:8000/users/{login}/addresses/{address_id}
```

## Удаление конкретного адреса конкретного пользователя

```http request
DELETE http://localhost:8000/users/{login}/addresses/{address_id}
```

## Получение списка номеров телефонов конкретного пользователя 

```http request
GET http://localhost:8000/users/{login}/phones
```

## Добавление номера телефона конкретного пользователю

```http request
POST http://localhost:8000/users/{login}/phones
```

## Получение информации о конкретном номере телефона конкретного пользователя

```http request
GET http://localhost:8000/users/{login}/phones/{phone_id}
```

## Редактирование информации о конкретном номере телефона конкретного пользователя

```http request
PUT http://localhost:8000/users/{login}/phones/{phone_id}
```

## Удаление конкретного номера телефона конкретного пользователя

```http request
DELETE http://localhost:8000/users/{login}/phones/{phone_id}
```

## Получение списка заказов конкретного пользователя

```http request
GET http://localhost:8000/users/{login}/orders
```