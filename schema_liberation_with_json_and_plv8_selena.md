Schema Liberation with JSON and PLV8 - Selena Deckelmann
===========

Twitter: [@selenamarie](http://twitter.com/selenamarie)
Email: selena@mozilla.org

hstore: key value storage, has been there for a long time.

## What is Schema Liberation?

Based on conversations on MongoDB. "Freedom". 

> "Schema flexibility means that you can model your documents in MongoDB so that they can closely resemble and reflect apyldcation level documents.
> - mongo docs

Example, insert statements vs JSON input. JSON is more developer friendly clearly.

## Can Postgres bet flexible ?

JSON features are now in 9.3 Postgres* plv8 or 9.2 + json_enhancements.

## v8: JS engine

Take an existing schema and convert to JSON

    select row_to_json(row) from (select * from reports) as row;

But I want a table

    CREATE TABLE liberated as (
      select row_to_json(row) from (select * from reports) as row
    )

and you get:

    Column  | Type | Modifiers
    --------------------------
    json   JSON

Penalty for denormalization

2Gb originality goes to 4Gb: there is a penalty for denormalization.

I wrote a script to convert all the tables to JSON that is in plv8 sql with inlined Javascript in it.

## JSON is First Class Type

    insert into birds VALUES('{"name": "Great Egret"}');

### Functions

    select json_object_field_text(sighting, 'name') from birds;

    json_object_field

    json_object_keys

## plv8 is Trusted

can run raw SQL and JSON is directly supported. And cursors too. You can use eval too!

## In Production

Crash stats for Mozilla for analyzing when mozilla crashes. 

Converted the table for storing crashes to use JSON. raw_crashes, and it takes about 5Gb. Normalized table 0.8k vs 2k per crash storage. You are going to burn some disk by doing JSON.

But when you don't really know what reports you want ahead of time, this is helpful.

## Advantage: 24 seconds vs map reduce: 30 minutes

map reduce against hbase took 30 minutes, vs with sql statement using JSON it took just 24 seconds. This is the main motivation, faster developer feedback.

## Why use Postgres?

1. Use "bulkbag" schema design + schema evolution. JSON to start, normalize to optimize.
2. Easily scale to multi-terabyte DBs: for write-heavy or read-heavy loads, non-cloud storage
3. Can use js to manage data.

## Links

<http://www.postgresql.org/develper/beta>
<http://code.google.com/p/plv8js/wiki/PSV8>
<http://gist.github.com/selenamarie/5646494>
<http://www.pgxn.org/dist/json_enhancements/doc/json_enhancements.html>