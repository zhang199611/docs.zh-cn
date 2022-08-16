
# COUNT

## 功能

用于返回满足要求的行的数目。

## 语法

```Haskell
COUNT(expr)
COUNT(DISTINCT expr [,expr,...])
```

## 参数说明

`expr`: 被选取的表达式。当使用DISTINCT关键字时，可以指定多个expr

## 返回值说明

返回值为数值类型。

## 示例

假设有表test, 按照订单id展示每个订单的国家、商品类别、供应商代号。

```sql
select * from test;
+------+----------+----------+------------+
| id   | country  | category | supplier   |
+------+----------+----------+------------+
| 1002 | Thailand | A        | supplier_2 |
| 1004 | US       | A        | supplier_2 |
| 1001 | US       | A        | supplier_1 |
| 1003 | Turkey   | B        | supplier_3 |
| 1005 | China    | C        | supplier_4 |
| 1006 | Japan    | D        | supplier_3 |
+------+----------+----------+------------+
```

1. 查看共有多少订单
```sql
select count(id) from test;
+--------------------+
| count(DISTINCT id) |
+--------------------+
|                  6 |
+--------------------+
```

2. 查看订单来自多少不同的国家
```sql
select count(distinct country) from test;
+-------------------------+
| count(DISTINCT country) |
+-------------------------+
|                       5 |
+-------------------------+
```

3. 查看商品类别（category）和供应商（supplier）共有多少种不同的组合
```sql
select count(distinct category, supplier) from test;
+------------------------------------+
| count(DISTINCT category, supplier) |
+------------------------------------+
|                                  5 |
+------------------------------------+
```
