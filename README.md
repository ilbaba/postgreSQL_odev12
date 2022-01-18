# postgreSQL_odev12
PostgreSQL -  On ikinci ödev - Ilgar Babashli

# _Q1_ 
film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

# _Ans_
SELECT COUNT (*) FROM film
WHERE length > (SELECT AVG (length) FROM film);

# _Q2_ 
film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

# _Ans_
SELECT COUNT (*) FROM film
WHERE rental_rate =
(SELECT(MAX (rental_rate)) FROM film);

# _Q3_ 
film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
# _Ans_
SELECT * FROM film
WHERE rental_rate = 
(SELECT MIN (rental_rate) FROM film)
AND replacement_cost =
(SELECT MIN (replacement_cost) FROM film);

# _Q4_ 
payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

# _Ans_
SELECT customer_id, SUM(amount) FROM payment 
GROUP BY customer_id ORDER BY SUM(amount) DESC;
