# ArangoDB Foundations

## Running ArangoDB using Docker Compose

```shell
docker-compose up
```

## The database

Dataset of US airports and flights and augmented and simplified it. 

Included are more than 3,000 airports and roughly 300,000 flights from January 1st to 15th, 2008.


### Airports document structure

The data structure of airport documents:

![airports](assets/airports.webp)


### Flights document structure

The data structure of flights documents:

![flights](assets/flights.webp)

## Importing the data

ArangoDB command line tool `arangoimport` is required to import the data into the database.

Airports:

```shell
arangoimport --server.endpoint http://localhost:8529 \
 --create-collection true --create-collection-type document --file 'data/airports.json' \
 --collection airports --server.database _system \
 --server.username root --server.password pass
```

Flights:

```shell
arangoimport --server.endpoint http://localhost:8529 \
 --create-collection true --create-collection-type edge \
 --file 'data/flights.json' --collection flights \
 --server.database _system --server.username root \
 --server.password pass --batch-size 100000000
```

