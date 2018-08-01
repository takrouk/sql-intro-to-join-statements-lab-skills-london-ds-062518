
# Introduction to JOIN Statements Lab

In this lab we will practice writing JOIN statements to query across two tables.  The tables will be associated through a "has many" and "belongs to" relationship.

## Objectives

1. Become comfortable writing various SQL JOIN statements
2. Select rows on both tables where certain values match using `INNER JOIN`
3. Write `LEFT JOIN` statements to get all the rows from the left table and the matching rows from the right table

## Superheroes and Super Squads

![](https://img.cinemablend.com/cb/1/2/d/c/d/5/12dcd57724f3c02e6f802dda3d56bd09996e236b062a2214f7c97c3e3f17a690.jpg)

### Download the Database
> Download the repo with dabase `superheroes.db` from [this link](https://github.com/learn-co-curriculum/sql-intro-to-join-statements-lab-skills)

> Open the database with SQLite Browser

Our database contains two tables: `superheroes` and `squads`.  We have seeded the database with fifteen superheroes and three superhero teams.  The superheroes table contains a column of foreign keys called `squad_id`.  Each superhero is assigned to one of the `squads` depending upon the assigned `squad_id`.  Therefore, a superhero "belongs to" the team with that matching `id`.  The two tables are shown below:


`Squads:`

id  |name
----|--------
1   |Avengers
2   |Justice League
3   |The Illuminati




`Superheroes:`

id  |name           |real_identity        |superpower                     |weakness          |squad_id
----|---------------|---------------------|-------------------------------|------------------|---------
1   |Batman         |Bruce Wayne          |works hard                     |mortal human      |2
2   |Superman       |Clark Kent           |superstrength                  |kryptonite        |2
3   |Thor           |Thor Odinson         |summons lightning              |ego               |1
4   |Iron Man       |Tony Stark           |ultra smart                    |mortal human      |1
5   |Wonder Woman   |Diana Prince         |superstrength                  |broken bracelets  |2
6   |Captain America|Steve Rogers         |superstrength                  |mortal human      |1
7   |Aquaman        |Arthur Curry         |breaths underwater             |needs water nearby|2
8   |Black Panther  |T'Challa             |speed and agility              |mortal human      |1
9   |Black Widow    |Natasha Romanoff     |expert martial artist          |mortal human      |1
10  |Hulk           |Bruce Banner         |rage                           |rage              |1
11  |Cyborg         |Victor Stone         |technorganic physiology        |hackers           |2
12  |Megaman        |NULL                 |elemental-mechanical physiology|hackers           |NULL
13  |StretcherFlex  |Jean-Claude Van Damme|enhanced flexibility           |mortal human      |NULL
14  |Goku           |Kakarot              |superstrength                  |myopia            |NULL
15  |Green Lantern  |Alan Scott           |magic ring                     |the color yellow  |2

## Queries

Write your queries in the "Execute SQL" tab in SQLIte broswer.  

#### 1.  `select_hero_names_and_squad_names_of_heroes_belonging_to_a_team`

Write a query that returns superhero names and the squad name for only the superheroes that belongs to a squad.

The query's return dataset should like like the following:

name            |name          
----------------|--------------
Batman          |Justice League
Superman        |Justice League
Thor            |Avengers      
Iron Man        |Avengers      
Wonder Woman    |Justice League
Captain America |Avengers      
Aquaman         |Justice League
Black Panther   |Avengers      
Black Widow     |Avengers      
Hulk            |Avengers      
Cyborg          |Justice League
Green Lantern   |Justice League

#### 2. `reformatted_query`

Great!  We selected all the superheroes belonging to a team.  However, our formatting is messy.  Let’s rewrite this query to group all the above superheroes according to their team name.  Also, both columns are called `name`, so let’s alias the `squads.name` to `team`.

The query should return the following:

name            |team          
----------------|--------------
Thor            |Avengers
Iron Man        |Avengers
Captain America |Avengers      
Black Panther   |Avengers      
Wonder Woman    |Avengers
Hulk            |Avengers      
Batman          |Justice League
Superman        |Justice League      
Wonder Woman    |Justice League      
Aquaman         |Justice League      
Cyborg          |Justice League
Green Lantern   |Justice League

#### 3.  `all_superheroes`

Cool!  However, let's take another look at our `superheroes` table.  Aren’t there some heroes belonging to no team?  Write a query that returns the `name`s and `superpower`s of all `superheroes` regardless of their affiliation to a team.  Again, make sure to also include `squads.name` aliased as `team`.

The query should return the following:

name             |superpower                      |team      
-----------------|--------------------------------|----------
Megaman          |elemental-mechanical physiology |           
StretcherFlex    |enhanced flexibility            |           
Goku             |superstrength                   |           
Thor             |summons lightning               |Avengers  
Iron Man         |ultra smart                     |Avengers  
Captain America  |superstrength                   |Avengers  
Black Panther    |speed and agility               |Avengers  
Black Widow      |expert martial artist           |Avengers  
Hulk             |rage                            |Avengers  
Batman           |works hard                      |Justice League
Superman         |superstrength                   |Justice League
Wonder Woman     |superstrength                   |Justice League
Aquaman          |breaths underwater              |Justice League
Cyborg           |technorganic physiology         |Justice League
Green Lantern    |magic ring                      |Justice League

#### 4. `all_squads`

Take another look at our `squads` table.  Notice that there is also one squad with NO members!  Write a `JOIN` statement that returns the `name` of each squad and a count for all of its members aliased as `num_of_members`.  (*Hint:* You will need to use a `GROUP BY clause` here.)

Note that we are using sqlite3, which does not support `RIGHT JOIN` or `FULL OUTER JOIN`.  We need to reformat our query so that we can use `LEFT JOIN` to get the result we want.  

The query should return the following:

name          |num_of_members
--------------|--------------
Avengers      |6             
Justice Leauge|6             
The Illuminati|0             

The Illuminati haven't existed since the late 18th Century, so perhaps their lack of members isn't such a surprise!

## Summary

Great job! In this lab, we practiced writing JOIN statements that return to us information from two tables instead of just one table, like when we were writing SELECT statements. 
