## SQL Questions

First create a database called fringe_shows
```
  #terminal
  psql
  create database fringe_shows;
  \q
```

Populate the data using the script - fringeshows.sql
```
  #terminal
  psql -d fringe_shows -f fringeshows.sql
```

Using the SQL Database file given to you as the source of data to answer the questions.  Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.


## Section 1

  Revision of concepts that we've learnt in SQL today

  1. Select the names of all users.  
  `fringe_shows=# select name from users;`  
  `name`  
  `--------------`  
  `Rick Henri`  
  `Jay Chetty`  
  `Keith Douglas`  
  `Marc Dinardo`

  2. Select the names of all shows that cost less than £15.
  `fringe_shows=# SELECT name FROM shows WHERE price < 15;`
`name`             
`-------------------------------`  
`Le Haggis`  
 `Paul Dabek Mischief`  
 `Best of Burlesque`  
 `Two become One`  
 `Urinetown`  
 `Two girls, one cup of comedy`

  3. Insert a user with the name "Val Gibson" into the users table.
  `fringe_shows=# INSERT INTO users(name) VALUES ('Valerie');`                               
`INSERT 0 1`
`fringe_shows=# select name from users;`  
`name`  
`---------------`  
`Rick Henri`  
`Jay Chetty`  
`Keith Douglas`  
`Marc Dinardo`  
`Valerie`

  4. Select the id of the user with your name.
  `fringe_shows=# SELECT id FROM users WHERE name = 'Valerie';`  
  `id`  
  `---`  
  `5`

  5. Insert a record that Val Gibson wants to attend the show "Two girls, one cup of comedy".
  `fringe_shows=# ALTER TABLE users ADD to_do varchar(255);`
`ALTER TABLE`  
`fringe_shows=# select * from users;`

 id |     name      | to_do 
----+---------------+-------
  1 | Rick Henri    | 
  2 | Jay Chetty    | 
  3 | Keith Douglas | 
  4 | Marc Dinardo  | 
  5 | Valerie       | 

 
  `fringe_shows=# INSERT INTO users (name, to_do) VALUES ('Val Gibson', 'attend Two girls, one cup of medy');`
`INSERT 0 1`  
`fringe_shows=# select * from users;`

 id |     name      |               to_do               
----+---------------+-----------------------------------
  1 | Rick Henri    | 
  2 | Jay Chetty    | 
  3 | Keith Douglas | 
  4 | Marc Dinardo  | 
  5 | Valerie       | 
  6 | Val Gibson    | attend Two girls, one cup of comedy

  6. Updates the name of the "Val Gibson" user to be "Valerie Gibson".
`fringe_shows=# UPDATE users SET name = 'Valerie Gibson' WHERE name = 'Val Gibson';`
`UPDATE 1`  
`fringe_shows=# select * from users;` 
 
 id |      name      |               to_do               
----+----------------+-----------------------------------
  1 | Rick Henri     | 
  2 | Jay Chetty     | 
  3 | Keith Douglas  | 
  4 | Marc Dinardo   | 
  5 | Valerie        | 
  6 | Valerie Gibson | attend Two girls, one cup of comedy

  7. Deletes the user with the name 'Valerie Gibson'.
  `fringe_shows=# DELETE FROM users WHERE name = 'Valerie Gibson';`
`DELETE 1`  
`fringe_shows=# select * from users;`  

 id |     name      | to_do 
----+---------------+-------
  1 | Rick Henri    | 
  2 | Jay Chetty    | 
  3 | Keith Douglas | 
  4 | Marc Dinardo  | 
  5 | Valerie       | 
 

  8. Deletes the shows for the user you just deleted.  
  Since I have decided to create a new row by altering the table in order to add the record 'to attend the show' (Task 6.), as I have deleted the user (TASK 7.) I have also deleted its 'to_do'.  
  If I understood the assignment though, I have to delete the show itself from TABLE shows.  
  The code as follows,  
  `fringe_shows=# DELETE FROM shows WHERE name = 'Two girls, one cup of comedy';`
`DELETE 1`  
`fringe_shows=# select * from shows;`  


 id | created_at |                  name                   | price 
----+------------+-----------------------------------------+-------
  1 | 2015-08-23 | Le Haggis                               | 12.99
  2 | 2015-08-23 | Shitfaced Shakespeare                   | 16.50
  3 | 2015-08-23 | Camille O'Sullivan                      | 17.99
  4 | 2015-08-23 | Game of Thrones - The Musical           | 16.50
  5 | 2015-08-23 | Paul Dabek Mischief                     | 12.99
  6 | 2015-08-23 | Joe Stilgoe: Songs on Film – The Sequel | 16.50
  7 | 2015-08-23 | Aaabeduation – A Magic Show             | 17.99
  8 | 2015-08-23 | Edinburgh Royal Tattoo                  | 32.99
  9 | 2015-08-23 | Best of Burlesque                       |  7.99
 10 | 2015-08-23 | Two become One                          |  8.50
 11 | 2015-08-23 | Urinetown                               |  8.50
 13 | 2015-08-23 | Balletronics                            | 32.00

## Section 2

  This section involves more complex queries.  You will need to go and find out about aggregate funcions in SQL to answer some of the next questions.

  9. Select the names and prices of all shows, ordered by price in ascending order.  
  `SELECT name ||' '|| price FROM shows ORDER BY price LIMIT 1 OFFSET 1;`

  10. Select the average price of all shows.

  11. Select the price of the least expensive show.

  12. Select the sum of the price of all shows.

  13. Select the sum of the price of all shows whose prices is less than £20.

  14. Select the name and price of the most expensive show.

  15. Select the name and price of the second from cheapest show.

  16. Select the names of all users whose names start with the letter "N".

  17. Select the names of users whose names contain "mi".


## Section 3

  The following questions can be answered by using nested SQL statements but ideally you should learn about JOIN clauses to answer them.

  18. Select the time for the Edinburgh Royal Tattoo.

  19. Select the number of users who want to see "Shitfaced Shakespeare".  
  `SELECT count FROM shows_users inner join shows on shows_users, show_id + shows_id where shows, name = ' ';`

  20. Select all of the user names and the count of shows they're going to see.

  21. SELECT all users who are going to a show at 17:15.

## Hints

  - As with anything, if you get stuck, move on, then go back if you have time.
  - Don't spend all night on it!
  - Use resources online to solve harder ones - there are solutions to these questions that work with what we've learnt today, but other tools exist in SQL that could make the queries 'better' or 'easier'.