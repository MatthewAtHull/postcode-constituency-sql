# postcode-constituency-sql

PostgreSQL dump of a database that can map postcodes to parliamentary
constituencies.

## Importing

Tested with PostgreSQL 13.

```bash
git clone \
  --depth 1 \
  https://github.com/MatthewAtHull/postcode-constituency-sql.git
cd postcode-constituency-sql
pg_restore --create --dbname=constituency dump.sql
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
