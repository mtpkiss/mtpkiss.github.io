---
title: mysql数据去重
date: 2017-12-05 09:30:55
tags: mysql
---
# MySql 去重

### sql语句来自网络,个人收集,未进行测试,请使用前备份

```sql
DELETE consum_record
FROM
  consum_record,
  (
    SELECT
      min(id) id,
      user_id,
      monetary,
      consume_time
    FROM
      consum_record
    GROUP BY
      user_id,
      monetary,
      consume_time
    HAVING
      count(*) > 1
  ) t2
WHERE
  consum_record.user_id = t2.user_id
AND consum_record.monetary = t2.monetary
AND consum_record.consume_time = t2.consume_time
AND consum_record.id > t2.id;
```

<!--more-->

1. 查询出重复记录形成一个集合（临时表t2），集合里是每种重复记录的最小ID
   ```sql
   SELECT
    min(id) id,
    user_id,
    monetary,
    consume_time
  FROM
    consum_record
  GROUP BY
    user_id,
    monetary,
    consume_time
  HAVING
    count(*) > 1
  ) t2
   ```
2. 关联判断重复基准的字段根据条件，删除原表中id大于t2中id的记录

    ```sql
        consum_record.user_id = t2.user_id
    AND consum_record.monetary = t2.monetary
    AND consum_record.consume_time = t2.consume_time
    AND consum_record.id > t2.id
    ```
