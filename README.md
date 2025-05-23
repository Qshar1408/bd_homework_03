# Домашнее задание к занятию «SQL. Часть 1»

### Грибанов Антон. FOPS-31

Задание можно выполнить как в любом IDE, так и в командной строке.

### Задание 1

Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

```bash
select district as Районы from address
where district like 'K%a' and district not like '% %';
```
 ![bd_003](https://github.com/Qshar1408/bd_homework_03/blob/main/img/bd_03_001.png)

### Задание 2

Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года **включительно** и стоимость которых превышает 10.00.

```bash
select * from payment
where date(payment_date) >= '2005-06-15' and date(payment_date) <= '2005-06-18' and amount > 10.00
order by payment_date asc;
```
 ![bd_003](https://github.com/Qshar1408/bd_homework_03/blob/main/img/bd_03_002.png)

### Задание 3

Получите последние пять аренд фильмов.

```bash
SELECT rental_date
FROM rental
ORDER BY rental_date DESC
LIMIT 5;
```
 ![bd_003](https://github.com/Qshar1408/bd_homework_03/blob/main/img/bd_03_003.png)
 
### Задание 4

Одним запросом получите активных покупателей, имена которых Kelly или Willie. 

Сформируйте вывод в результат таким образом:
- все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
- замените буквы 'll' в именах на 'pp'.

```bash
SELECT CONCAT((REPLACE(LOWER(first_name), 'll', 'pp')), " ", LOWER(last_name)) AS 'Имя и фамилия' , active
FROM customer
WHERE active = 1 AND first_name IN ('Kelly', 'Willie');
```
![bd_003](https://github.com/Qshar1408/bd_homework_03/blob/main/img/bd_03_004.png)

## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

### Задание 5*

Выведите Email каждого покупателя, разделив значение Email на две отдельных колонки: в первой колонке должно быть значение, указанное до @, во второй — значение, указанное после @.

```bash
SELECT lower(email) AS Почтовый_адрес, lower(substring_index(email, '@', 1)) as Почтовый_адрес_до, right(email, length(email)-position('@' in email)) as Почтовый_адрес_после
from customer 
order by email asc;
```
![bd_003](https://github.com/Qshar1408/bd_homework_03/blob/main/img/bd_03_005.png)

