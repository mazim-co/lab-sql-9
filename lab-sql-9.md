-- Lab | SQL Queries 9
-- 1. Create a table rentals_may to store the data from rental table with information for the month of May.

drop table if exists rentals_may;
CREATE TABLE rentals_may (
   rental_id int NOT NULL AUTO_INCREMENT,
   rental_date datetime NOT NULL,
  inventory_id mediumint unsigned NOT NULL,
  customer_id smallint unsigned NOT NULL,
  return_date datetime DEFAULT NULL,
  staff_id tinyint unsigned NOT NULL,
  last_update timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
   PRIMARY KEY (rental_id)
);
-- 2. Insert values in the table rentals_may using the table rental, filtering values only for the month of May.
insert into rentals_may
select rental_id, rental_date, inventory_id, customer_id, return_date, staff_id, last_update
from sakila.rental
where rental_date between '2005-05-01' and '2005-05-31';



-- 3. Create a table rentals_june to store the data from rental table with information for the month of June.

drop table if exists rentals_june;
CREATE TABLE rentals_june (
   rental_id int NOT NULL AUTO_INCREMENT,
   rental_date datetime NOT NULL,
  inventory_id mediumint unsigned NOT NULL,
  customer_id smallint unsigned NOT NULL,
  return_date datetime DEFAULT NULL,
  staff_id tinyint unsigned NOT NULL,
  last_update timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
   PRIMARY KEY (rental_id)
);

-- 4. Insert values in the table rentals_june using the table rental, filtering values only for the month of June.
insert into rentals_june
select rental_id, rental_date, inventory_id, customer_id, return_date, staff_id, last_update
from sakila.rental
where rental_date between '2005-06-01' and '2005-06-30';



-- 5. Check the number of rentals for each customer for May.


select customer_ID, count(*) from sakila.rentals_may
group by customer_ID
order by count(*) desc;


-- 6. Check the number of rentals for each customer for June.

select customer_ID, count(*) from sakila.rentals_june
group by customer_ID
order by count(*) desc;

