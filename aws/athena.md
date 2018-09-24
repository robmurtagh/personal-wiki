# AWS Athena

## Add columns:

```sql
ALTER TABLE db.table ADD COLUMNS (column_name string)
```

## Change column type \(doesn't work\):

```sql
ALTER TABLE db.table CHANGE column_name column_name timestamp;
```

## List all partitions:

```sql
SHOW PARTITIONS appsflyer_stream
```

## Special characters can be e.g. quoted

  ```sql
  SELECT column_name_1, "column-name-2", column_name_3, ##
  FROM db.table
  WHERE column_name_3 is not null
  ORDER BY timestamp_column DESC;
  ```

## Using a substring:

```sql
SELECT event_name, substr(timestring, 1, 10) as datestring, count(##) AS count
FROM stream
WHERE test_mode != 'true' AND event_name = 'event_a'
GROUP BY event_name, substr(timestring, 1, 10)
ORDER BY datestring DESC
```

## Between timestamps:

```sql
WHERE timestamp BETWEEN timestamp '2017-06-13 15:50:00.000' AND timestamp '2017-06-13 16:52:29.000'
```

## Null handling:

```sql
WHERE column IS null
```

## Casting:

```sql
SUM(CAST(sysvar_sales AS Double)) AS Sales
```

## Literals:

```sql
true AS picnic_install
```

