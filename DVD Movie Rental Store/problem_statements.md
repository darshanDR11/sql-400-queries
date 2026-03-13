```sql
-- +-------------------------------------------------------------------------------------------------+ 
-- |------------------------------------------SELECT Queries-----------------------------------------|
-- +-------------------------------------------------------------------------------------------------+ 

-- 1. Display all records from the actor table.
select * from actor;

-- 2. Show the first name and last name of all actors.
select first_name, last_name from actor;

-- 3. Display all film titles and their release year.
select title, release_year from film;

-- 4. Show all customer first names and emails.
select first_name, email from customer;

-- 5. Display all available film categories.
select category_id, name from category;

-- 6. Show all cities stored in the database.
select city_id, city from city;

-- 7. Display the list of countries.
select  country_id, country from country;

-- 8. Show all rental IDs and rental dates.
select rental_id, rental_date from rental;

-- 9. Display all payment amounts.
select payment_id, amount from payment;

-- 10. Show all staff members.
select concat(first_name, " ", last_name) as name from staff;

-- 11. Display all stores.
select * from store;
 
-- 12. Show film titles with their rental duration.
select title, rental_duration from film;

-- 13. Display language names available in the database.
select language_id, name from language;

-- 14. Show all addresses stored in the address table.
select * from address;

-- 15. Display all film ratings.
select film_id, title, rating from film;

-- 16. Show all inventory IDs with film IDs.
select inventory_id, film_id from inventory;

-- 17. Display all customers with their store ID.
select customer_id, first_name, last_name, store_id from customer;

-- 18. Show staff first names and last names.
select staff_id, first_name, last_name from staff;

-- 19. Display film titles and replacement costs.
select film_id, title, replacement_cost from film;

-- 20. Show all actors ordered by last name.
select * from actor order by last_name;
 
--  
 
--  
 
--

-- +-------------------------------------------------------------------------------------------------+ 
-- |-----------------------------------------Filtering Queries---------------------------------------|
-- +-------------------------------------------------------------------------------------------------+ 
  
-- 21. Find actors whose first name is "Nick".
select * from actor where first_name = "Nick";

-- 22. Display actors whose last name starts with "A".
select * from actor where last_name like "A%";

-- 23. Find films longer than 120 minutes.
select film_id, title, length from film where length > 120 order by film_id asc;

-- 24. Display films with rating "PG".
select film_id, title, rating from film where rating = "PG";

-- 25. Show films with rental rate greater than 3.
select film_id, title, rental_rate from film where rental_rate > 3 order by rental_rate;

-- 26. Find customers whose email contains "sakilacustomer".
select * from customer where email like "%sakilacustomer%";

-- 27. Display payments greater than 8 dollars.
select * from payment where amount > 8;

-- 28. Show rentals made after January 1, 2006.
select * from rental where rental_date > "2006-01-01" order by rental_date;

-- 29. Find films with replacement cost between 15 and 25.
select film_id, title, replacement_cost from film where replacement_cost between 15 and 25;

-- 30. Display actors whose last name ends with "SON".
select actor_id, first_name, last_name from actor where last_name like "%SON";

-- 31. Find cities belonging to country ID 44.
select * from city where country_id = 44;

-- 32. Display addresses located in district "California".
select * from address where district = "California";

-- 33. Show films with rental duration equal to 7 days.
select film_id, title, rental_duration from film where rental_duration = 7;

-- 34. Display actors whose first name begins with "J".
select actor_id, first_name, last_name from actor where first_name like "J%";

-- 35. Find customers named "Mary".
select customer_id, first_name, last_name from customer where first_name = "Mary";

-- 36. Show films with length between 90 and 120 minutes.
select film_id, title, length from film where length between 90 and 120 order by length;

-- 37. Display customers whose store ID is 1.
select customer_id, first_name, last_name, email from customer where store_id = 1;

-- 38. Find films with rating "G" or "PG".
select * from film where rating in ("G","PG") order by rating;

-- 39. Show payments less than 2 dollars.
select payment_id,customer_id, staff_id, amount from payment where amount < 2 order by amount;

-- 40. Display customers whose last name starts with "S".
select * from customer where last_name like "S%";

--  
 
--  
 
--

-- +-------------------------------------------------------------------------------------------------+ 
-- |-------------------------------------------Aggregation-------------------------------------------|
-- +-------------------------------------------------------------------------------------------------+ 
 
-- 41. Count total number of actors.
select count(actor_id) as total_actors from actor;

-- 42. Count total number of films.
select count(film_id) as Total_Films from film;

-- 43. Count total number of customers.
select count(distinct customer_id) as Total_Cutomers from customer;

-- 44. Find the average film length.
select round(avg(length),2) as Average_Length from film;

-- 45. Find maximum replacement cost among films.
select max(replacement_cost) as Maximum_Replacement_Cost from film;

-- 46. Find minimum rental rate.
select min(rental_rate) as Minimum_Rental_Rate from film;

-- 47. Count films for each rating category.
select rating, count(film_id) as Total_Film from film group by rating order by Total_Film;

-- 48. Find total payments received.
select round(sum(amount),2) as total_payments from payment;

-- 49. Calculate average payment amount.
select round(avg(amount),2) as average_payment from payment;

-- 50. Count rentals made by each customer.
select customer_id, count(rental_id) as total_rental from rental group by customer_id;

-- 51. Find total payment made by each customer.
select customer_id, round(sum(amount),2) as total_payment from payment group by customer_id;

-- 52. Count number of films in each category.
select category_id, count(film_id) as total_film from film_category group by category_id;
-- +-----------------------------------------OR-----------------------------------------+
select fc.category_id, name, count(film_id) as total_film from film_category as fc join category as c on fc.category_id = c.category_id group by fc.category_id;

-- 53. Find number of actors appearing in each film.
select film_id, count(actor_id) as total_actor from film_actor group by film_id;
-- +-----------------------------------------OR-----------------------------------------+
select fc.film_id, title, count(actor_id) as total_actor from film_actor as fc, film as f where fc.film_id = f.film_id group by film_id;

-- 54. Count films available in each store.
select store_id, count(film_id) from inventory group by store_id;

-- 55. Find total revenue generated by each store.
select staff_id, round(sum(amount),2) as Total_Revenue from payment group by staff_id;

-- 56. Count number of rentals handled by each staff member.
select staff_id, count(rental_id) as Total_Rental from rental group by staff_id;

-- 57. Find number of addresses in each district.
select district, count(address_id) as total from address group by district;

-- 58. Count number of cities in each country.
select country_id, count(city_id) as total_city from city group by country_id;
-- +-----------------------------------OR-----------------------------------+
select CT.country_id, country, count(city_id) as total_city from city as CT, country as CY where CT.country_id = CY.country_id group by CT.country_id;

-- 59. Count customers in each store.
select store_id, count(customer_id) as Total_Customer from customer group by store_id;

-- 60. Count films by language.
select language_id, count(film_id) as Total_Film from film group by language_id;

-- 61. Find total inventory copies per film.
select film_id, count(inventory_id) as Total_Film from inventory group by film_id;

-- 62. Count number of rentals per film.
select film_id, count(rental_id) as total_rental from inventory as i right join rental as r on i.inventory_id = r.inventory_id group by film_id;

-- 63. Calculate average rental rate per rating.
select rating, round(avg(rental_rate),2) as Average_Rental_Rate from film group by rating order by Average_Rental_Rate;

-- 64. Find average film length per category.
select fc.category_id, c.name, round(avg(length),2) as Average_Length from film as f, film_category as fc, category as c where f.film_id = fc.film_id and fc.category_id = c.category_id group by fc.category_id;

-- 65. Count actors with the same last name.
select last_name, count(actor_id) as total_actor from actor group by last_name;

-- 66. Count payments processed by each staff member.
select staff_id, count(payment_id) as total_payment_processed from payment group by staff_id;

-- 67. Count rentals per month.
select extract(month from rental_date) as month, count(rental_id) as total_rental from rental group by month;

-- 68. Count rentals per day.
select extract(day from rental_date) as day, count(rental_id) as total_rental from rental group by day;

-- 69. Find average payment per customer.
select customer_id, round(avg(amount),2) as average_payment from payment group by customer_id;

-- 70. Count films per replacement cost range.
select replacement_cost, count(film_id) as total_film from film group by replacement_cost order by replacement_cost;

--  
 
--  
 
--

-- +-------------------------------------------------------------------------------------------------+
-- |----------------------------------------GROUP BY + HAVING----------------------------------------|
-- +-------------------------------------------------------------------------------------------------+

-- 71. Find customers who rented more than 10 films.
select customer_id, count(rental_id) as total_rented from rental group by customer_id having total_rented > 10 order by total_rented;

-- 72. Show actors who appeared in more than 20 films.
select actor_id, count(film_id) as total_film from film_actor group by actor_id having total_film > 20;

-- 73. Display categories having more than 50 films.
select fc.category_id, name, count(film_id) as total_film from film_category as fc, category as c where fc.category_id = c.category_id group by fc.category_id having total_film > 50;

-- 74. Find customers who paid more than $100 total.
select p.customer_id, first_name, last_name, round(sum(amount),2) as total_paid from payment as p, customer as c where p.customer_id = c.customer_id group by p.customer_id having total_paid > 100;

-- 75. Show films rented more than 30 times.

-- 76. Display cities having more than 5 addresses.
select city_id, count(address_id) as total_address from address group by city_id having total_address > 5;

-- 77. Find staff members who processed more than 100 payments.
select staff_id, count(payment_id) as total_processed_payment from payment group by staff_id having total_processed_payment > 100;

-- 78. Show ratings with more than 100 films.
select rating, count(film_id) as total_film from film group by rating having total_film > 100;

-- 79. Find customers with more than 15 rentals.
select  customer_id, count(rental_id) as total_rental from rental group by customer_id having total_rental > 15;

-- 80. Show films with average rental rate greater than 3.
select film_id, title, rental_rate from film where rental_rate > (select avg(rental_rate) from film);

-- 81. Display actors appearing in more than 15 films.
select actor_id, count(film_id) as total_film from film_actor group by actor_id having total_film > 15;

-- 82. Find customers who made more than 20 payments.
select customer_id ,count(payment_id) as total_payment from payment group by customer_id having total_payment > 20;

-- 83. Show categories with average film length above 120 minutes.
select fc.category_id, name, round(avg(length),2) as average_film_length 
from film as f 
join film_category as fc on f.film_id = fc.film_id 
join category as c on fc.category_id = c.category_id
group by fc.category_id having average_film_length > 120;

-- 84. Find films with more than 5 actors.
select film_id, count(actor_id) as total_actor from film_actor group by film_id having total_actor > 5;

-- 85. Display countries having more than 10 cities.
select c.country_id, country, count(city_id) as total_city from city as c, country as cy where c.country_id = cy.country_id group by c.country_id having total_city > 10;

-- 86. Show stores having more than 500 rentals.
select staff_id, count(rental_id) as total_rental from rental group by staff_id having total_rental > 500;

-- 87. Find films with total revenue greater than 200 dollars.

-- 88. Show customers with average payment above 4 dollars.
select customer_id, round(avg(amount),2) as average_payment from payment group by customer_id having average_payment > 4.0;

-- 89. Find actors with duplicate last names.
select distinct a1.actor_id, a1.first_name, a1.last_name from actor as a1 join actor as a2 on a1.last_name = a2.last_name and a1.actor_id != a2.actor_id order by a1.last_name;

-- 90. Show districts having more than 5 addresses.
select district, count(address_id) as total_address from address group by district having total_address > 5;

-- 

-- 

--

-- +-------------------------------------------------------------------------------------------------+ 
-- |-------------------------------------------JOIN Queries------------------------------------------|
-- +-------------------------------------------------------------------------------------------------+ 

-- 91. Show films with their language name.
select film_id, title, description, release_year, l.language_id, name  
from film as f 
join language as l on f.language_id = l.language_id;

-- 92. Display customers with their address.
select customer_id, first_name, last_name, address, district, postal_code, phone
from customer as c 
join address as a on c.address_id = a.address_id;

-- 93. Show customers with city name.
select customer_id, first_name, last_name, city
from customer as c 
join address as a on c.address_id = a.address_id
join city as ct on a.city_id = ct.city_id;

-- 94. Display customers with country name.
select customer_id, first_name, last_name, country
from customer as c 
join address as a on c.address_id = a.address_id
join city as ct on a.city_id = ct.city_id
join country as cy on ct.country_id = cy.country_id;

-- writing three different queries, we can write a single query like this:-
select customer_id, first_name, last_name, address, district, city, postal_code, country, phone
from customer as c 
join address as a on c.address_id = a.address_id
join city as ct on a.city_id = ct.city_id
join country as cy on ct.country_id = cy.country_id;
-- where we display the full address of the customer along with city, country.

-- 95. Show films with their category name.
select f.film_id, title, description, name as category, release_year, length, rating
from film as f 
join film_category as fc on f.film_id = fc.film_id
join category as c on fc.category_id = c.category_id;


-- 96. List actors and films they acted in.
select fa.actor_id, first_name, last_name, title
from film as f 
join film_actor as fa on f.film_id = fa.film_id
join actor as a on fa.actor_id = a.actor_id; 

-- 97. Show customers and films they rented.
select * from inventory;
select customer_id, f.film_id, title 
from film as f
join inventory as i on f.film_id = i.film_id
join rental as r on i.inventory_id = r.inventory_id
group by customer_id, f.film_id -- May be customer rented the film twice, film_id unique and customer may rented same film twice on different time. 
order by customer_id asc, title asc;
-- here we show only the id of the customers

-- 98. Display rentals with customer names.
select rental_id, r.customer_id, first_name, last_name, rental_date, return_date
from rental as r 
join customer as c on r.customer_id = c.customer_id order by rental_id;

-- 99. Show payments with customer details.
select payment_id, p.customer_id, first_name, last_name, amount, payment_date 
from payment as p 
join customer as c on p.customer_id = c.customer_id;

-- 100. Display staff members with store ID.

-- 101. Show films with number of actors.
select fa.film_id, title, count(actor_id) as total_actor 
from film_actor as fa 
join film as f on fa.film_id = f.film_id 
group by fa.film_id;

-- 102. Display film title with category and language.
select f.film_id, title, c.name, l.name
from film as f
join film_category as fc on f.film_id = fc.film_id
join category as c on fc.category_id = c.category_id
join language as l on f.language_id = l.language_id order by f.film_id;

-- 103. Show rentals with film title and rental date.
select f.film_id, title, rental_rate, rental_date 
from film as f 
join inventory as i on f.film_id = i.film_id
join rental as r on i.inventory_id = r.inventory_id order by film_id asc, rental_date asc;

-- 104. Display payments with staff member names.
select payment_id, payment_date, p.staff_id, first_name, last_name, amount  
from payment as p 
join staff as s on p.staff_id = s.staff_id;

-- 105. Show customers with their store location.
select c.customer_id, first_name, last_name, address, district
from customer as c 
join store as s on c.store_id = s.store_id
join address as a on s.address_id = a.address_id;

-- 106. List films rented by each customer.

-- 107. Show rental history of a specific customer.

-- 108. Display films and their actors.
select f.film_id, title, group_concat(" ",first_name," ",last_name) as actor_name
from film as f 
join film_actor as fa on f.film_id = fa.film_id
join actor as a on fa.actor_id = a.actor_id 
group by f.film_id
order by f.film_id;

-- 109. Show film titles and store inventory count.
select f.film_id, title, count(inventory_id) as total 
from film as f 
left join inventory as i on f.film_id = i.film_id
group by f.film_id;

-- 110. Display film categories with film titles.
select f.film_id, title, c.category_id, name as category_name
from film as f
join film_category as fc on f.film_id = fc.film_id
join category as c on fc.category_id = c.category_id order by f.film_id;

-- 111. Show customers with payment totals.
select p.customer_id, concat(first_name," ",last_name) as full_name, sum(amount) as total_payment 
from payment as p 
join customer as c on p.customer_id = c.customer_id
group by p.customer_id;

-- 112. Display store managers and store IDs.

-- 113. Show rentals and payment amounts.
select r.rental_id, payment_id, amount, rental_date, return_date 
from rental as r 
join payment as p on r.rental_id = p.rental_id 
order by rental_id;

-- 114. Display staff with addresses.
select staff_id, first_name, last_name, address, district, phone 
from staff as s 
join address as a on s.address_id = a.address_id;

-- 115. Show films rented by each store.

-- 116. Display number of rentals per film.
select i.film_id, title, count(i.inventory_id) as total  
from inventory as i 
join rental as r on i.inventory_id = r.inventory_id 
join film as f on i.film_id = f.film_id
group by i.film_id;

-- 117. Show payments made for each rental.
select r.rental_id, amount, rental_date, return_date, r.customer_id, r.staff_id
from rental as r
join payment as p on r.rental_id = p.rental_id order by r.rental_id;

-- 118. Display film title with rental count.
select f.film_id, title, ifnull(count(r.rental_id),0) as total_rental 
from film as f 
left join inventory as i on f.film_id = i.film_id
left join rental as r on i.inventory_id = r.inventory_id group by f.film_id;

-- 119. Show customers who rented a specific film.

-- 120. Display film categories and actor counts.
select c.name, count(f.film_id) as total_actor 
from film as f 
join film_category as fc on f.film_id = fc.film_id
join category as c on fc.category_id = c.category_id
join film_actor as fa on fa.film_id = f.film_id 
group by c.name; 

-- 121. Show staff and payments processed.
select payment_id, amount, p.staff_id, first_name, last_name 
from payment as p
join staff as s on p.staff_id = s.staff_id;

-- 122. Display customers with rental counts.
select c.customer_id, first_name, last_name, count(rental_id) as total_rented 
from rental as r 
join customer as c on r.customer_id = c.customer_id 
group by r.customer_id;

-- 123. Show rentals with film and customer details.
select rental_id, f.film_id, title, c.customer_id, first_name, last_name, rental_date, return_date
from rental as r 
join customer as c on r.customer_id = c.customer_id
join inventory as i on r.inventory_id = i.inventory_id 
join film as f on i.film_id = f.film_id 
order by rental_id;

-- 124. Display film title with actor names.
select f.film_id, title, a.actor_id, first_name, last_name 
from film as f 
join film_actor as fa on f.film_id =  fa.film_id
join actor as a on fa.actor_id = a.actor_id 
order by f.film_id asc, a.actor_id asc;

-- 125. Show films and categories sorted by name.
select f.film_id, title, c.name
from film as f 
join film_category as fc on f.film_id = fc.film_id 
join category as c on fc.category_id = c.category_id 
order by c.name asc, f.film_id asc;

-- 126. Display customers with city and country.
select c.customer_id, concat(first_name," ",last_name) as full_name, city, country
from customer as c
join address as a on c.address_id = a.address_id 
join city as ct on a.city_id = ct.city_id 
join country as cy on ct.country_id = cy.country_id order by c.customer_id;

-- 127. Show inventory and store details.

-- 128. Display rental with staff information.

-- 129. Show total films rented per city.
select a.city_id, city, count(rental_id) as total_rented_film 
from rental as r 
join customer as c on r.customer_id = c.customer_id
join address as a on c.address_id = a.address_id
join city as ct on a.city_id = ct.city_id 
group by a.city_id order by a.city_id;

-- 130. Display payment records with rental date.
select p.rental_id, payment_id, amount, rental_date, return_date 
from payment as p 
join rental as r on p.rental_id = r.rental_id 
order by p.rental_id;

-- 131. Show customers and total rentals. And also total payment amount.
select r.customer_id, concat(first_name," ",last_name) as name, count(r.rental_id) as total_rented_film, sum(amount) as total_amount
from rental as r 
join payment as p on r.rental_id = p.rental_id 
join customer as c on r.customer_id = c.customer_id
group by r.customer_id;

-- 132. Display films with total revenue.
select f.film_id, title, release_year, rating, length, sum(amount) as total_revenue 
from film as f
join inventory as i on f.film_id = i.film_id
join rental as r on i.inventory_id = r.inventory_id
join payment as p on r.rental_id = p.rental_id
group by f.film_id 
order by f.film_id asc;

-- 133. Show actors appearing in a specific category.
-- 134. Display films and average payment.
-- 135. Show films rented per store.

-- 136. Display categories with rental counts.
select fc.category_id, name as category_name, count(r.rental_id) as total_rental
from film as f 
join inventory as i on f.film_id = i.film_id
join rental as r on i.inventory_id = r.inventory_id
join film_category as fc on f.film_id = fc.film_id
join category as c on fc.category_id = c.category_id
group by category_id;

-- 137. Show actor film counts. "How many films did actor made"
select fa.actor_id, first_name, last_name, count(film_id) as total_film
from film_actor as fa 
join actor as a on fa.actor_id = a.actor_id
group by fa.actor_id;

-- 138. Display customer rental statistics.

-- 139. Show payment totals by film.
select f.film_id, title, ifnull(round(sum(amount),2),0) as total_payment
from film as f
left join inventory as i on f.film_id = i.film_id
left join rental as r on i.inventory_id = r.inventory_id
left join payment as p on r.rental_id = p.rental_id
group by f.film_id;

-- 140. Display films with actor count and category.
select f.film_id, title, c.name as category_name, release_year, count(fa.actor_id) as total_actor
from film as f 
join film_actor as fa on f.film_id = fa.film_id
join film_category as fc on f.film_id = fc.film_id
join category as c on fc.category_id = c.category_id 
group by f.film_id, c.category_id 
order by f.film_id;

--  
 
--  
 
--

-- +-------------------------------------------------------------------------------------------------+ 
-- |-------------------------------------------Sub Queries-------------------------------------------|
-- +-------------------------------------------------------------------------------------------------+ 

-- 141. Find films with rental rate above average.
select * from film 
where rental_rate > (select round(avg(rental_rate),2) from film);

-- 142. Find films longer than average film length.
select * from film 
where length > (select round(avg(length),2) from film);

-- 143. Find customers paying above average payment.

-- 144. Find actors appearing in more films than average.
with ans as (select actor_id, count(film_id) as total_films from film_actor group by actor_id) 
select ans.actor_id, first_name, last_name, total_films from ans 
join actor as a on ans.actor_id = a.actor_id
where total_films > (select avg(total_films) from ans);

-- 145. Find films rented more than average times.

-- 146. Find highest payment made.
select * from payment where amount = (select max(amount) from payment);

-- 147. Find customers with highest payment.
with ans as (select customer_id, sum(amount) as total_payment from payment group by customer_id) 
select * from ans where total_payment = (select max(total_payment) from ans);

-- 148. Find films never rented.
-- first film_id may not be in inventory table 
-- second film_id in inventoty table but may not be in rental table
select film_id, title, release_year, rating, length 
from film 
where not film_id in (select f.film_id 
						from film as f 
						join inventory as i on f.film_id = i.film_id
						join rental as r on i.inventory_id = r.inventory_id);


-- 149. Find actors not appearing in any film.
select * from actor where not actor_id in (select distinct actor_id from film_actor);

-- 150. Find customers who never made payments.
select * from rental where not customer_id in (select distinct customer_id from payment);

-- 151. Find films in most popular category.

-- 152. Find customer with most rentals.
select customer_id, count(rental_id) as total from rental group by customer_id order by total desc limit 1;

-- 153. Find film with highest revenue.

-- 154. Find customers paying above store average.

-- 155. Find films with lowest rental rate.
select film_id, title, release_year, length, rating, rental_rate from film where rental_rate = (select min(rental_rate) from film);

-- 156. Find categories with highest rental count.

-- 157. Find actors appearing in highest number of films.
select actor_id, count(film_id) as total_film from film_actor group by actor_id order by total_film desc limit 1;

-- 158. Find films rented by most customers.

-- 159. Find stores generating highest revenue.
with ans as(
select s.store_id, sum(amount) as total_revenue 
from payment as p 
join staff as s on p.staff_id = s.staff_id
group by s.store_id) 
select * from ans where total_revenue = (select min(total_revenue) from ans);

-- 160. Find customers who paid more than store average.

--  
 
--  
 
--

-- +-------------------------------------------------------------------------------------------------+ 
-- |-------------------------------------------CTE Queries-------------------------------------------|
-- +-------------------------------------------------------------------------------------------------+ 
 
-- 161. Create a CTE calculating total payments per customer.
with ans as (
select p.customer_id, concat(first_name," ",last_name) as name , round(sum(amount),2) as total_payments 
from payment as p, customer as c 
where c.customer_id = p.customer_id 
group by customer_id
)

-- 162. Find customers with payments above $200 using CTE.
select * from ans where total_payments > 200;

-- 163. Create a CTE calculating total rentals per film.
with ans as (
select f.film_id, title, rental_rate, count(rental_id) as total_rentals
from film as f 
left join inventory as i on f.film_id = i.film_id
left join rental as r on i.inventory_id = r.inventory_id
group by f.film_id)

-- 164. Show films rented more than 30 times using CTE.
select * from ans where total_rentals > 30;

-- 165. Create a CTE showing revenue per store.
with ans as (
select s.store_id, round(sum(amount),2) as total_revenue 
from payment as p, staff as s 
where p.staff_id = s.staff_id 
group by s.store_id)

-- 166. Find store with highest revenue using CTE.
select * from ans where total_revenue = (select max(total_revenue) from ans);

-- 167. Create a CTE calculating rentals per category.
with ans as (
select fc.category_id, c.name, count(r.rental_id) as total_rental
from film_category as fc
join category as c on fc.category_id = c.category_id
join inventory as i on fc.film_id = i.film_id
join rental as r on i.inventory_id = r.inventory_id
group by fc.category_id)

-- 168. Show top 5 categories by rentals using CTE.
select * from ans order by total_rental desc limit 5;

-- 169. Create a CTE calculating customer rental counts.
with ans as (
select c.customer_id, first_name, last_name, count(rental_id) as total_rentals 
from customer as c 
left join rental as r on c.customer_id = r.customer_id
group by c.customer_id)

-- 170. Show customers with more than 30 rentals.
select * from ans where total_rentals > 30;

-- 171. Create a CTE calculating film revenue.
with ans as (
select f.film_id, title, ifnull(sum(amount),0) as total_revenue
from film as f 
left join inventory as i on f.film_id = i.film_id
left join rental as r on i.inventory_id = r.inventory_id
left join payment as p on r.rental_id = p.rental_id
group by f.film_id)

-- 172. Show top 3 revenue films using CTE.
select * from ans order by total_revenue desc limit 3;

-- 173. Create CTE for average film length per category.
with ans as (
select c.category_id, name, round(avg(length),2) as average_length
from film as f
join film_category as fc on f.film_id = fc.film_id
join category as c on fc.category_id = c.category_id
group by c.category_id
)

-- 174. Show longest category average using CTE.
select * from ans where average_length = (select max(average_length) from ans);

-- 175. Create CTE calculating actor film counts.
with ans as (
select a.actor_id, count(film_id) as total_film
from film_actor as fa
join actor as a on fa.actor_id = a.actor_id 
group by a.actor_id
)

-- 176. Show actors with highest film appearances.
select * from ans where total_film = (select max(total_film) from ans);

-- 177. Create CTE for rental counts per store.
with ans as (
select s.store_id, r.staff_id, count(rental_id) as total_rental 
from rental as r, staff as s 
where r.staff_id = s.store_id 
group by s.store_id
)
-- 178. Show store with most rentals.
select * from ans where total_rental = (select max(total_rental) from ans);

-- 179. Create CTE calculating payments handeled by staff.
with ans as (
select staff_id, count(payment_id) as total_payments 
from payment 
group by staff_id)

-- 180. Show top staff by payments processed.
select * from ans where total_payments = (select max(total_payments) from ans);

--  
 
--  
 
--

-- +-------------------------------------------------------------------------------------------------+ 
-- |-----------------------------------------WINDOW Function-----------------------------------------|
-- +-------------------------------------------------------------------------------------------------+ 
 
-- 181. Assign row numbers to films ordered by rental rate.

-- 182. Rank films by rental rate.

-- 183. Use DENSE_RANK to rank films by length.

-- 184. Rank customers by total payments.

-- 185. Show top 5 customers by payments using RANK.

-- 186. Calculate running total of payments by date.

-- 187. Rank films within each category by rental rate.

-- 188. Partition customers by store and rank payments.

-- 189. Find second highest payment using window functions.

-- 190. Show rental counts per customer using PARTITION BY.

-- 191. Rank actors by number of films.

-- 192. Show top 3 films per category using window functions.

-- 193. Rank stores by revenue.

-- 194. Partition payments by customer and order by date.

-- 195. Find top paying customer in each store.

-- 196. Rank films by number of rentals.

-- 197. Partition films by rating and rank by length.

-- 198. Show top 3 customers per city.

-- 199. Calculate cumulative revenue per store.

-- 200. Rank categories by number of rentals.
```
