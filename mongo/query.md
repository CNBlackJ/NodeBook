# Query

### 常用查询

##### 查询重复值
```
// 查询出现次数大于1的name
db.yd_coupon.aggregate(
    {"$group" : { "_id": "$name", "count": { "$sum": 1 } } },
    {"$match": {"_id" :{ "$ne" : null } , "count" : {"$gt": 1} } }
)
```