# Домашнее задание к занятию «Работа с данными (DDL/DML)» - Стрельцов Владимир

## Задание 1

1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

1.2. Создайте учётную запись sys_temp.

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

![img](/img/2023-10-25_09-38-15.png)

1.4. Дайте все права для пользователя sys_temp.

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

![img](/img/2023-10-25_11-38-48.png)

1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос:

ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.7. Восстановите дамп в базу данных.

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

![img](/img/2023-10-25_11-24-01.png)

![img](/img/2023-10-25_11-24-58.png)

Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.

```
mysql> CREATE USER 'sys_temp’@‘localhost' IDENTIFIED BY '12345';

mysql> SELECT user FROM mysql.user;

mysql> GRANT ALL PRIVILEGES ON *.* TO ‘sys_temp’@‘localhost';

mysql> SHOW GRANTS FOR sys_temp@localhost;

mysql> ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH mysql_native_password BY ‘12345’;

docker exec -i net-mysql sh -c 'exec mysql -uroot -p"***"' < /Users/joos/Downloads/sakila-db/sakila-schema.sql 

docker exec -i net-mysql sh -c 'exec mysql -uroot -p"***"' < /Users/joos/Downloads/sakila-db/sakila-data.sql

mysql> USE sakila;

mysql> SHOW TABLES;
```



## Задание 2

Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. 

Пример: (скриншот/текст)

```
Название таблицы | Название первичного ключа
customer         | customer_id
```

```
Название таблицы             | Название первичного ключа
actor                        | actor_id
actor_info                   | 
address                      | address_id
category                     | category_id
city                         | city_id
country                      | country_id
customer                     | customer_id
customer_list                | 
film                         | film_id
film_actor                   | actor_id, film_id
film_category                | film_id, category_id
film_list                    | 
film_text                    | film_id
inventory                    | inventory_id
language                     | language_id
nicer_but_slower_film_list   | 
payment                      | payment_id
rental                       | rental_id
sales_by_film_category       | 
sales_by_store               | 
staff                        | staff_id
staff_list                   | 
store                        | store_id
```
