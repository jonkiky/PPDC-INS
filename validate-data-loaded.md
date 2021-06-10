# Validate Data loaded

Clickhouse:

There are three tables to check the number of records in each table. 

**ot.associations\_otf log** :    27297042  

```text
select count(*) from ot.associations_otf_log
```

![](.gitbook/assets/screen-shot-2021-06-09-at-11.09.32-pm.png)

