# Slow Query Log 

## Walkthrough 

```
# Step 1
/etc/my.cnf.d/mariadb-server.cnf 
[mysqld]
slow-query-log 

# Step 2
mysql>SET GLOBAL slow_query_log = 1 
mysql>SET slow_query_log = 1 
mysql>SET GLOBAL long_query_time = 0.000001 
mysql>SET long_query_time = 0.000001

# Step 3
# run some time / data
# and look into your slow-query-log 
/var/lib/mysql/hostname-slow.log 

```

## Show queries that do not use indexes 

```
SET GLOBAL log_queries_not_using_indexes=ON;
```

## Reference 

  * https://mariadb.com/kb/en/slow-query-log-overview/

