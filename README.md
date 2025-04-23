# root password
ranka132

# laba1

`
1) Выберите из таблицы orders все заказы: 
`
SELECT * FROM orders
`

![Image](https://i.imgur.com/jfUJubL.png)

2) Выберите из таблицы orders все заказы кроме новых. У новых заказов status равен "new". Использовать in: 
`
SELECT * FROM orders
WHERE STATUS NOT IN ('new') 
`

![Image](https://i.imgur.com/jYuAKgE.png)

3) Выберите из таблицы orders все новые и отмененные заказы. У отмененных заказов status равен "cancelled". У новых заказов status равен "new":
`
SELECT * FROM orders
WHERE STATUS IN ('NEW', 'CANCELLED')
`

![Image](https://i.imgur.com/0adiqVl.png)

4) Выберите из таблицы orders все заказы содержащие более 3 товаров (products_count). Вывести нужно только номер (id) и сумму (sum) заказа:
`
SELECT id, SUM
FROM orders
WHERE products_count > 3
`

![Image](https://i.imgur.com/tkyuS2Y.png)

![Image](https://i.imgur.com/ZaTRYwC.png)

# laba2

`
1.  Выберите из таблицы orders 3 самых дешевых заказа за всё время. Данные нужно отсортировать в порядке убывания цены. Отмененные заказы не учитывайте.
`
SELECT * 
FROM orders
WHERE status != 'cancelled'
ORDER BY sum ASC
LIMIT 3;
`

![Image](https://i.imgur.com/BgZOQ19.png)

2) Выберите из таблицы orders 2 самых дорогих заказов за всё время. Данные нужно отсортировать в порядке убывания цены. Отмененные заказы не учитывайте.
`
SELECT * 
FROM orders
WHERE status != 'cancelled'
ORDER BY sum DESC
LIMIT 2;
`

![Image](https://i.imgur.com/w0d5ihF.png)

3) Добавьте в таблицу orders данные о новом заказе стоимостью 8000 рублей. В заказе 4 товара (products).
`
INSERT INTO orders (id, products, sum)
VALUES (6, 4, 8000);
`

![Image](https://i.imgur.com/gXAja9Y.png)

![Image](https://i.imgur.com/F5JPKFK.png)

4.  Добавьте в таблицу products новый товар — «VR-очки», стоимостью 70000 рублей в количестве (count) 2 штук.
`
INSERT INTO products (id, name, count, price)
VALUES (7, 'VR-очки', 2, 70000);
`

![Image](https://i.imgur.com/h5d2ztx.png)
![Image](https://i.imgur.com/MA5ym8E.png)

5.  В таблицу products внесли данные с ошибкой, вместо "PS5" в наименовании написали IMAC. Исправьте ошибку.
`
UPDATE products
SET name = 'PS5' 
WHERE name = 'IMAC';
`

![Image](https://i.imgur.com/ptRvIop.png)
![Image](https://i.imgur.com/ZaTRYwC.png)

# laba3

```
CREATE TABLE users (
	id INT,
	first_name VARCHAR(50),
	last_name VARCHAR(50)
);

INSERT INTO users (id, first_name, last_name) VALUES
	(1, 'Дмитрий', 'Иванов'),
	(2, 'Анатолий', 'Белов'),
	(3, 'денис', 'Давыдов');
```

![Image](https://i.imgur.com/pDxdNHq.png)
![Image](https://i.imgur.com/VXkDbbn.png)

# zadachi

1) Создайте таблицу users для хранения информации о пользователях сайта.
В таблице должны быть следующие поля:

id – идентификатор, целое положительное;
email – адрес электронной почты, строка не более 100 символов;
date_joined – дата регистрации (достаточно хранить дату, без времени)
last_activity – дата и время последней активности (с точностью до секунд).

![Image](https://i.imgur.com/n0LeII7.jpeg)

Неверное решение: 

```
CREATE TABLE users(
id INT UNSIGNED,
email VARCHAR(100),
date_joined DATE,
last_activity DATETIME
);

INSERT INTO users (id, email, date_joined, last_activity)
VALUES (1, "user1@domain.com", "2014-12-12", "2016-04-08 12:34:54")
INSERT INTO users (id, email, date_joined, last_activity)
VALUES (2, "user2@domain.com", "2014-12-12", "2017-02-13 11:46:53")
INSERT INTO users (id, email, date_joined, last_activity)
VALUES (3, "user3@domain.com", "2014-12-13", "2017-04-04 05:12:07")
```

ПЕРЕД КАЖДЫМ ЗАПРОСОМ (INSERT INTO) НУЖНО СТАВИТЬ ТОЧКУ С ЗАПЯТОЙ ;

Верное решение: 

```
create table users (
id int(10) unsigned,
email varchar (100),
date_joined date,
last_activity datetime
);
insert into users (id, email, date_joined,last_activity)
values
(1,'user1@domain.com', '2014-12-12','2016-04-08 12:34:54'),
(2,'user2@domain.com', '2014-12-12','2017-02-13 11:46:53'),
(3,'user3@domain.com', '2014-12-13','2017-04-04 05:12:07');
```

2) Создайте таблицу calendar для хранения календаря посетителей.
В таблице должны быть следующие поля:

id – идентификатор записи в календаре, целое положительное;
user_id – идентификатор пользователя, целое положительное;
doctor_id – идентификатор доктора, целое положительное;
visit_date – дата и время визита (точность до секунд).

![Image](https://i.imgur.com/cA7ihuZ.jpeg)

Неверное решение:

```
Create table calendar (
id int unsigned,
user_id int unsigned,
doctor_id int unsigned,
visit_date datetime);
Insert into calendar (id, user_id, doctor_id, visit_date)
Values (1, 1914 , 1, '2017-04-08 12:00:00'),
(2, 12, 1, '2017-04-08 12:30:00'),
(3, 4641, 2, '2017-04-09 09:00:00'),
(4, 4641, 2,'2017-04-09 09:00:00'),
(5, 15, 2,'2017-04-09 10:00:00')
```

Верное решение:

```
Create table calendar (
id int unsigned,
user_id int unsigned,
doctor_id int unsigned,
visit_date datetime);
Insert into calendar (id, user_id, doctor_id, visit_date)
Values 
(1, 1914 , 1, '2017-04-08 12:00:00'),
(2, 12, 1, '2017-04-08 12:30:00'),
(3, 4641, 2, '2017-04-09 09:00:00'),
(4, 784, 1,'2017-04-08 13:00:00'),
(5, 15, 2,'2017-04-09 10:00:00')
```

VARCHAR (65535) - максимум

3) Создайте таблицу users , в которой будут следующие поля:

id — идентификатор, целые положительные числа.
first_name— имя, строки до 50 символов.
last_name — фамилия, строки до 60 символов.
bio — биография, текст до 65000 символов.

![Image](https://i.imgur.com/OMl9opC.jpeg)

Неверное решение:

```
create table users (
id int (10) unsigned,
first_name varchar (50) unsigned,
last_name varchar (60) unsigned,
bio text
);
INSERT INTO users (id, first_name, last_name, bio)
VALUES
(1,'Антон','Кулик','С отличием окончил 39 лицей.'),
(2,'Сергей','Давыдов',''),
(3,'Дмитрий','Соколов','Профессиональный программист.')
```

Верное решение:

```
create table users (
id int (10) unsigned,
first_name varchar (50),
last_name varchar (60),
bio text
);
INSERT INTO users (id, first_name, last_name, bio)
VALUES
(1,'Антон','Кулик','С отличием окончил 39 лицей.'),
(2,'Сергей','Давыдов',''),
(3,'Дмитрий','Соколов','Профессиональный программист.')
```

# laba4


1) Выберите из таблицы orders 4 самых дорогих заказов за всё время. Данные нужно отсортировать в порядке убывания цены. Отмененные заказы не учитывайте.

```
SELECT id, user_id, products_count, sum, status
FROM orders
WHERE status != 'cancelled'
ORDER BY sum DESC
LIMIT 4;
```

![Image](https://i.imgur.com/RLyVW2d.png)


2) Выберите из таблицы products название и цены четырех самых дешевых товаров, которые есть на складе.

```
SELECT name, price
FROM products
WHERE COUNT > 0 
ORDER BY price ASC
LIMIT 4;
```

![Image](https://i.imgur.com/GtSHEoz.png)


3) Выберите из таблицы orders три последних заказа (по дате date) стоимостью от 3200 рублей и выше.
Данные отсортируйте по дате в обратном порядке.

```
SELECT id, user_id, products_count, sum, status, date
FROM orders
WHERE sum >= 3200
ORDER BY date DESC
LIMIT 3;
```

![Image](https://i.imgur.com/J5K9e8A.png)


4) Создайте данную таблицу:

![Image](https://i.imgur.com/cjIqDgr.png)

```
CREATE TABLE products (
	id INT,
	NAME VARCHAR(255), 
	COUNT INT, 
	price INT
);

INSERT INTO products (id, NAME, COUNT, price) VALUES
	 (1, 'Стиральная машина', 5, 10000),
    (2, 'Холодильник', 0, 10000),
    (3, 'Микроволновка', 3, 4000),
    (4, 'Пылесос', 2, 4500),
    (5, 'Вентилятор', 0, 700),
    (6, 'Телевизор', 7, 31740),
    (7, 'Тостер', 2, 2500),
    (8, 'Принтер', 4, 3000),
    (9, 'Активные колонки', 1, 2900),
    (10, 'Ноутбук', 4, 36990),
    (11, 'Посудомоечная машина', 0, 17800),
    (12, 'Видеорегистратор', 23, 4000),
    (13, 'Смартфон', 8, 12300),
    (14, 'Флешка', 4, 1400),
    (15, 'Блендер', 0, 5500),
    (16, 'Газовая плита', 5, 11900),
    (17, 'Клавиатура', 3, 1800);
```

![Image](https://i.imgur.com/EZIFD2W.png)


5) Из этой таблицы сделать выборку на основе задания: Сайт выводит товары по 5 штук. 
Выберите из таблицы products товары, которые пользователи увидят на 3 странице каталога при сортировке в порядке возрастания цены (price).

```
SELECT id, name, count, price
FROM products
ORDER BY price ASC
LIMIT 5 OFFSET 10;
`

![Image](https://i.imgur.com/A0MHIXA.png) 

```

# zadachi


1) Создайте таблицу articles для хранения данных о статьях. В таблице должны быть следующие поля:
id — идентификатор, целое положительное, NULL запрещен
name — название статьи, строка до 80 символов.text — текст статьи.
state — статус статьи. Поле из 3 вариантов: draft (черновик), correction (корректура), public (опубликована).Добавьте 3 записи так, чтобы получалась таблица ниже:


![Image](https://i.imgur.com/JWcczMy.jpeg)

```
Create table articles (
id int unsigned not null,
name varchar (80),
text text,
state enum('draft', 'correction', 'public')
);
insert into articles (id, name, text, state)
VALUES
(1, 'Новое в Python 3.6', '', 'draft'),
(2, 'Оптимизация SQL запросов', 'При больших объемах данных ...', 'correction'),
(3, 'Транзакции в MySQL', 'По долгу службы мне приходится ...', 'public')
```

```
Когда можно выбрать 1 вариант - используем ENUM
когда можно выбрать несколько вариантов - используем SET
```


2) Создайте таблицу rooms для хранения номеров в отеле:

id — идентификатор, целое положительное.
number — номер комнаты, целое положительное. Всего в отеле 107 комнат. NULL запрещен.
beds — количество спальных мест. Выбор из 1+1, 2+1, 2+2. Можно выбрать только один вариант. NULL запрещен.
additional — дополнительные удобства в номере. Можно выбрать несколько вариантов из списка: conditioner, bar, fridge и wifi.
Добавьте 3 записи так, чтобы получалась таблица ниже:


![Image](https://i.imgur.com/aCOoHpJ.jpeg)

```
create table rooms (
id int unsigned not null,
number tinyint unsigned not null,
beds enum('1+1','2+1','2+2') not null,
additional set('conditioner','bar','fridge','wifi')
);
insert into rooms (id,number,beds,additional)
values
(1,10,'1+1','conditioner,bar,wifi'),
(2,12,'2+1',''),
(3,24,'2+2','fridge,bar,wifi')
```


3) Выберите из таблицы products название, цену и страны всех товаров из России и Белоруссии (в поле country обязательно должна присутствовать или Россия, или Белоруссия).
Выбирайте только товары, у которых задана категория.
Данные отсортируйте по цене в обратном порядке.

Поле country относится к типу SET('RU', 'UA', 'BY', 'KZ') NOT NULL.

![Image](https://i.imgur.com/KFOZKXS.jpeg)

```
SELECT name,price,country FROM products 
WHERE (find_in_set ('RU',country) OR find_in_set ('BY',country)) AND category_id IS NOT NULL ORDER BY price DESC
```

# laba5

1) Создайте таблицу orders для хранения списка заказов:

id — идентификатор, целое положительное.
user_id — идентификатор пользователя, который оформил заказ. Целое положительное, NULL запрещен.
amount — стоимость заказа. Целое положительное число не более 1 млн. NULL запрещен, по умолчанию 0.
created — дата и время создания заказа. NULL запрещен.
state — статус заказа. Выбор из new, cancelled, in_progress, delivered, completed. Можно выбрать только один вариант. NULL запрещен. По умолчанию должен стоять new.
Добавьте 3 записи так, чтобы получалась таблица ниже:

![Image](https://i.imgur.com/sIqb7Zd.jpeg)

```

```

2) Создайте таблицу users для хранения списка пользователей сайта:

id — идентификатор, целое положительное.
first_name — имя, строка до 20 символов. NULL запрещен.
last_name — фамилия, строка до 20 символов. NULL запрещен.
patronymic — отчество, строка до 20 символов. NULL запрещен, по умолчанию пустая строка.
is_active — отметка об активности пользователя. Логическое поле, по умолчанию TRUE.
is_superuser — отметка администратора. Логическое поле, по умолчанию FALSE.
Добавьте 3 записи так, чтобы получалась таблица ниже:

![Image](https://i.imgur.com/3jhtWz4.jpeg)

```

```

3) Создайте таблицу products для хранения товаров в интернет магазине:

id — идентификатор, целое положительное.
category_id — категория, целое положительное. Может принимать NULL. По умолчанию NULL.
name — название, строка до 100 символов. NULL запрещен.
count — количество, целое положительное до 255. NULL запрещен, по умолчанию 0.
price — цена типа DECIMAL с 10 знаками, 2 из которых выделены для копеек. NULL запрещен, по умолчанию 0.00.
Добавьте 3 записи так, чтобы получалась таблица ниже:

![Image](https://i.imgur.com/24K3c3w.jpeg)

```

```

# zadachi

1) Создайте таблицу users с со следующими полями:
id — идентификатор, целое положительное, первичный ключ без автоинкремента, NULL запрещен.
first_name — имя пользователя, строка до 50 символов.
last_name — фамилия пользователя, строка до 50 символов.
birthday — дата рождения. Пользователь может не указать день рождения и тогда в поле нужно хранить NULL.
Добавьте 3 записи так, чтобы получалась таблица ниже:

![Image](https://i.imgur.com/BhgsSul.jpeg)

```
CREATE TABLE users (
id INT(10)UNSIGNED NOT NULL PRIMARY KEY,
first_name VARCHAR (50) NULL,
last_name VARCHAR (50) NULL,
birthday DATE NULL );
INSERT INTO users (id, first_name, last_name, birthday)
VALUES (1,'Дмитрий','Иванов',NULL),
(2,'Анатолий','Белый',NULL),
(3,'Денис','Давыдов','1995-09-08');
```

2) Создайте таблицу orders с автоинкрементальным первичным ключом id, полем state для хранения статуса заказа и полем amount для хранения суммы заказа. Статус заказа умещается в строку длиной 8 символов, а сумма заказа является денежным типом до 1 млн. с двумя знаками после десятичной точки.
Добавьте 3 записи так, чтобы получалась таблица ниже:

![Image](https://i.imgur.com/sQMY1Fd.jpeg)

```
create table orders (
id int unsigned not null primary key auto_increment,
state varchar (8),
amount decimal (8,2)
);
insert into orders (state, amount)
values ('new', 1000.50),
('new', 3400.10),
('delivery', 7300.00)
```
