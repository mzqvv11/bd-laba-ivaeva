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

Создайте таблицу users для хранения информации о пользователях сайта.
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

Создайте таблицу calendar для хранения календаря посетителей.
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


Создайте таблицу users , в которой будут следующие поля:

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
