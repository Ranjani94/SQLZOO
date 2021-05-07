
1. SELECT name FROM world
  WHERE population >
     (SELECT population FROM world
      WHERE name='Russia')
      
2. select name from world
where continent= 'Europe' AND gdp/population > (select gdp/population from world where name='United Kingdom')

3. select name, continent from world 
where continent IN (select continent from world where name IN ('Argentina', 'Australia')) order by name

4. select name, population from world
where population > (select population from world where name='Canada') AND
 population < (select population from world where name='Poland') 
 
 5. SELECT name, CONCAT(ROUND(100*population/(SELECT population FROM world WHERE name = 'Germany')), '%') FROM world WHERE continent = 'Europe'

We can use the word ALL to allow >= or > or < or <=to act over a list. 

6. select name from world 
where gdp > ALL(select gdp from world where gdp>0 AND continent='Europe')

7. SELECT continent, name, area FROM world x
  WHERE area >= ALL
    (SELECT area FROM world y
        WHERE y.continent=x.continent
          AND area>0)
      
8. select continent, name from world x
where name <= ALL(select name from world y where y.continent = x.continent)

9. select name, continent, population from world 
where continent IN (select continent from world x where 25000000 >= (select max(population) from world y where y.continent = x.continent))

10. 
