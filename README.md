# postcode-constituency-sql

PostgreSQL dump of a database that can map postcodes to parliamentary
constituencies.

## Sample

### Constituency

```
+-----------+--------------------------+
| id        | name                     |
+-----------+--------------------------+
| E14000530 | Aldershot                |
| E14000531 | Aldridge-Brownhills      |
| E14000532 | Altrincham and Sale West |
| E14000533 | Amber Valley             |
| E14000534 | Arundel and South Downs  |
+-----------+--------------------------+
```

### Postcode

```
+----------+-----------------+
| postcode | constituency_id |
+----------+-----------------+
| AB10AA   | S14000002       |
| AB10AB   | S14000002       |
| AB10AD   | S14000002       |
| AB10AE   | S14000058       |
+----------+-----------------+
```

## Importing

Tested with PostgreSQL 13.

```bash
git clone \
  --depth 1 \
  https://github.com/MatthewAtHull/postcode-constituency-sql.git
cd postcode-constituency-sql
psql dbname -f dump.sql
```

## Example Query

```sql
SELECT constituency.name
FROM postcode
INNER JOIN constituency
ON constituency.id = postcode.constituency_id
WHERE postcode.postcode = 'HU67TS';
```

## Sources

* [National Statistics Postcode Lookup (February 2021)](https://geoportal.statistics.gov.uk/datasets/national-statistics-postcode-lookup-february-2021) (Custom License)
* [Westminster Parliamentary Constituencies (December 2020)](https://geoportal.statistics.gov.uk/datasets/westminster-parliamentary-constituencies-december-2020-names-and-codes-in-the-united-kingdom) (Custom License)
