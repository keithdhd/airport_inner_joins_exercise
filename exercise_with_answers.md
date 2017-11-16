## Setup

1. Create a database called airport_manager (createdb airport_manager)
2. Run the SQL script (psql -d airport_manager -f airport_manager.sql)

## Questions

1. Using an inner join, select the flight number and airport name for all the flights

```
select flights.number, airports.name 
from airports
inner join flights
on flights.airport_id = airports.id
```

2. Add aliases so that the resulting columns are called flight_number and airport_name

```
select flights.number as flight_number, airports.name as airport_name
from airports
inner join flights
on flights.airport_id = airports.id
```

3. Using an inner join, select the flight number and airport name for all the flights that belong to Heathrow

```
select flights.number as flight_number, airports.name as airport_name 
from airports
inner join flights
on flights.airport_id = airports.id
where airports.name = 'Heathrow'
```

4. Using an inner join, select all the flight and airport details for flight BA1453

```
select flights.*, airports.* 
from airports
inner join flights
on flights.airport_id = airports.id
where flights.number = 'BA1453'
```

5. Using inner joins, select the flight number of the flights that Tom Cruise is on

```
BA1453
RY786
```

```
select flights.number as flight_number 
from flights
inner join passengers_flights
on passengers_flights.flight_id = flights.id
inner join passengers
on passengers_flights.passenger_id = passengers.id
where passengers.first_name = 'Tom' and passengers.last_name = 'Cruise'
```

6. Using inner joins, select all of Sian's flight numbers and all of Tom's flight numbers (NOTE: you'll have to us some brackets in the where clause to separate your ANDs and ORs)

```
select flights.number as flight_number, passengers.first_name 
from flights
inner join passengers_flights
on passengers_flights.flight_id = flights.id
inner join passengers
on passengers_flights.passenger_id = passengers.id
where (passengers.first_name = 'Tom' and passengers.last_name = 'Cruise')
or (passengers.first_name = 'Sian' and passengers.last_name = 'RD')
```

7. What changes would you make to the structure of the flights table so that we can identify a flight's departure and destination airports? 

```
Remove airport_id and add destination_airport_id and departure_airport_id
```
