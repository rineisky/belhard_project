# База данных проекта

В качестве БД (базы данных) для проекта необходимо использовать РСУБД `MySQL` или
`PostgreSQL`. Может быть использована локальная база данных или работающая в Docker
(В зависимости от уровня сложности).
Для демонстрации работы проекта необходимо, чтобы БД содержала некоторые тестовые
данные (была предзаполнена).

*К сведению: во всех связях должно быть установлено каскадное обновление и удаление*

В проекте должна быть реализована схема интернет-магазина, торгующего комплектующими
для компьютеров.

При построении схемы были использованы следующие упрощения, что можно развивать:
- каждый товар находится только в одной категории;
- описание товара не разделено на различные подразделы;
- пароль пользователя хранится в незашифрованном виде;
- у каждого производителя только один адрес;
- в схеме нет реализации курьеров;
- не полноценная реализация адресов (корпус, штат, геолокация и т.д.);
- можно добавить различные триггеры (например, в заказе расчет суммы заказа)
- нет полноценного разделения на пользователей и администраторов;
- и т.д., так как этот список можно продолжать бесконечно.

## Схема данных

### Таблица `categories` - "категории товаров"

- id [`NOT NULL`, `VARCHAR(50)`, `PRIMARY KEY`] - уникальный идентификатор категории
- name [`NOT NULL`, `VARCHAR(50)`] - название категории

Вставить в таблицу следующие значения:

- GPU - Graphics Processing Unit
- CPU - Central Processing Unit
- MB - Motherboard
- RAM - Random Access Memory
- SSD - Solid-State Drive
- HDD - Hard Disk Drive
- CASE - Case
- POWER - Power Supply
- COOL - Cooling

### Таблица `user_types` - "типы пользователей"

- id [`NOT NULL`, `VARCHAR(50)`, `PRIMARY KEY`] - уникальный идентификатор типа пользователя
- name [`NOT NULL`, `VARCHAR(50)`] - название типа пользователя

Вставить в таблицу следующие значения:

- ADMIN - Administrator
- USER - User

### Таблица `phone_types` - "типы номеров телефонов"

- id [`NOT NULL`, `VARCHAR(50)`, `PRIMARY KEY`] - уникальный идентификатор типа номера телефона
- name [`NOT NULL`, `VARCHAR(50)`] - название типа номера телефона

Вставить в таблицу следующие значения:

- WORK - Work phone number
- HOME - Home phone number
- MOBILE - Mobile phone number
- OTHER - Other phone number

### Таблица `delivery_types` - "типы продажи"

- id [`NOT NULL`, `VARCHAR(50)`, `PRIMARY KEY`] - уникальный идентификатор типа продажи
- name [`NOT NULL`, `VARCHAR(50)`] - название типа продажи

Вставить в таблицу следующие значения:

- DELIVERY - Delivery
- SELF-PICKUP - Self-pickup

### Таблица `order_statuses` - "статусы заказа"

- id [`NOT NULL`, `VARCHAR(50)`, `PRIMARY KEY`] - уникальный идентификатор статуса заказа
- name [`NOT NULL`, `VARCHAR(50)`] - название статуса заказа

Вставить в таблицу следующие значения:

- CLOSED - Closed
- CANCELLED - Cancelled
- OPENED - Opened

### Таблица `addresses` - "адреса"

- id [`NOT NULL`, `INT`, `AUTOINCREMENT`] - уникальный идентификатор адреса
- country [`NOT NULL`, `VARCHAR(50)`] - страна
- city [`NOT NULL`, `VARCHAR(50)`] - город
- street [`NOT NULL`, `VARCHAR(50)`] - улица
- house [`NOT NULL`, `VARCHAR(50)`] - дом
- postal_code [`NOT NULL`, `VARCHAR(50)`] - почтовый индекс

### Таблица `companies` - "компании-производители"

- id [`NOT NULL`, `INT`, `AUTOINCREMENT`] - уникальный идентификатор компании
- name [`NOT NULL`, `VARCHAR(50)`] - название компании
- address_id [`NOT NULL`, `INT`, `REFERENCES addresses(id)`] - адрес

### Таблица `items` - "товары"

- id [`NOT NULL`, `INT`, `AUTOINCREMENT`] - уникальный идентификатор товара
- name [`NOT NULL`, `VARCHAR(100)`] - название товара
- price [`NOT NULL`, `DECIMAL(7,2)`] - цена товара
- description [`NOT NULL`, `VARCHAR(255)`] - описание товара
- warranty_period [`NOT NULL`, `INT`] - гарантия (месяцев)
- category_id [`NOT NULL`, `VARCHAR(50)`, `REFERENCES categories(id)`] - категория товара
- company_id [`NOT NULL`, `VARCHAR(50)`, `REFERENCES companies(id)`] - компания-производитель

### Таблица `users` - "пользователи"

- login [`NOT NULL`, `VARCHAR(50)`, `PRIMARY KEY`] - логин пользователя
- password [`NOT NULL`, `VARCHAR(255)`] - пароль пользователя
- surname [`NOT NULL`, `VARCHAR(50)`] - фамилия пользователя
- name [`NOT NULL`, `VARCHAR(50)`] - имя пользователя
- last_name [`VARCHAR(50)`] - отчество пользователя
- user_type_id [`NOT NULL`, `VARCHAR(50)`, `REFERENCES user_types(id)`] - тип пользователя

### Таблица `user_addresses` - "адреса пользователей или пользователи, которые живут по некоторому адресу"

*MM связь между `users` и `addresses`*

- user_login [`NOT NULL`, `VARCHAR(50)`, `REFERENCES users(login)`] - логин пользователя
- address_id [`NOT NULL`, `INT`, `REFERENCES addresses(id)`] - адрес

### Таблица `phones` - "номера телефонов пользователей"

- id [`NOT NULL`, `INT`, `AUTOINCREMENT`] - уникальный идентификатор номера телефона
- number [`NOT NULL`, `VARCHAR(50)`] - номер телефона
- phone_type_id [`NOT NULL`, `VARCHAR(50)`, `REFERENCES phone_types(id)`] - тип номера телефона
- user_login [`NOT NULL`, `VARCHAR(50)`, `REFERENCES user(id)`] - пользователь с данным номером телефона

### Таблица `orders` - "заказы"

- id [`NOT NULL`, `INT`, `AUTOINCREMENT`] - уникальный идентификатор заказа
- sale_date [`NOT NULL`, `DATETIME`] - дата продажи
- user_login [`NOT NULL`, `VARCHAR(50)`, `REFERENCES users(login)`] - логин пользователя
- order_status_id [`NOT NULL`, `VARCHAR(50)`, `REFERENCES order_statuses(id)`] - статус заказа
- delivery_type_id [`NOT NULL`, `VARCHAR(50)`, `REFERENCES delivery_types(id)`] - тип продажи
- address_id [``INT``, `REFERENCES addresses(id)`] - адрес доставки
- created_at [`DATETIME`, `DEFAULT NOW()`] - дата и время создания заказа

### Таблица `order_items` - "товары в заказе"

*MM связь между `orders` и `items`*

- order_id [`NOT NULL`, `INT`, `REFERENCES orders(id)`] - заказ
- item_id [`NOT NULL`, `INT`, `REFERENCES items(id)`] - товар
- count [`NOT NULL`, `INT`] - количество

***

Полученная схема должна выглядеть следующим образом:

![Database schema](schema.JPG)

## SQLAlchemy

1. Создать пакет ```db```.
2. Создать модуль ```base.by```:

    ```python
    from sqlalchemy.ext.declarative import declarative_base
    
    Base = declarative_base()
    ```

3. Создать модуль ```session.by```:

    ```python
    from sqlalchemy import create_engine
    from sqlalchemy.orm import sessionmaker
    from contextlib import contextmanager
    
    
    engine = create_engine(
        'mysql+pymysql://user:password@localhost:3306/database',
        pool_pre_ping=True,
        pool_recycle=3600,
    )
    Session = sessionmaker(bind=engine)
    
    
    @contextmanager
    def session_scope():
        session = Session()
        try:
            yield session
            session.commit()
        except:
            session.rollback()
            raise
        finally:
            session.close()
    ```

4. Создать в пакете ```db``` пакет ```tables```.
5. В пакете ```tables``` описать таблицы.
6. Сделать файл ```__init__.py``` в пакете ```db``` и в пакете ```tables```и описать в нем инструкции импорта пакета.