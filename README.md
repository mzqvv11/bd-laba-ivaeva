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
