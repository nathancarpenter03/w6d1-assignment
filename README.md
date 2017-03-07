#h2 Week 6 Day 1: SQL and Databases

1. How many users are there? 
    50 

    select count (*) from users;

2. What are the 5 most expensive items?

    25|Small Cotton Gloves|Automotive, Shoes & Beauty|Multi-layered modular service-desk|9984
    83|Small Wooden Computer|Health|Re-engineered fault-tolerant adapter|9859
    100|Awesome Granite Pants|Toys & Books|Upgradable 24/7 access|9790
    40|Sleek Wooden Hat|Music & Baby|Quality-focused heuristic info-mediaries|9390
    60|Ergonomic Steel Car|Books & Outdoors|Enterprise-wide secondary firmware|9341

    select * from items order by price DESC;

3. What's the cheapest book? (Does that change for "category is exactly 'book'" versus "category contains 'book'"?)

    76|Ergonomic Granite Chair|Books|De-engineered bi-directional portal|1496

    select * from items where category like '%book%' order BY price ASC;

    Yes, it differs. category = 'book' does not return anything 

4. Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address?

    select user_id from addresses where street = '6439 Zetta Hills' and city = "Willmouth" and state = "WY";

    40

    select first_name and last_name from 

    Corrine Little

5. Correct Virginie Mitchell's address to "New York, NY, 10108"

    select id from users where last_name like '%Mitchell%' and first_name like '%Virginie%';

    39

    update addresses set city = "New York", state = "NY", zip = "10108" where user_id = 39;

6. How much would it cost to buy one of each tool?

    select sum(price) as total_cost from items where category like '%tool%';

    46477

7. How many total items did we sell?

    select sum(quantity) as total_items_sold from orders;

    2125

8. How much was spent on books?

    select sum(orders.quantity*items.price) as total_spent_on_books from orders join items on orders.item_id = items.id where items.category like '%book%';

    1081352

9. Simulate buying an item by inserting a User for yourself and an Order for that User.

    insert into users (first_name, last_name, email) values ('Nathan', 'Carpenter', 'email@gmail.com');
    insert into orders (user_id, item_id, quantity, created_at) values (51, 5, 1, 2017-03-06 '17:00:00');








