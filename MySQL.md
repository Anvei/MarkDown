# 查询
### 注释

1. **--**：单行注释
1. **#**：单行注释
1. **/*	*/**：多行注释
### select
作用：限定查询结果的列，用于控制输出

- **select**：后接列名，限定查询返回的列
- **from**：后接表名，指定从哪一个表中查询
- **distinct**：必须放在列名前面
- *** **：通配符，匹配全部列
- 示例
```sql
SELECT col1, col2, col3 FROM tableName; # 查询tableName中的col1,col2,col3列
SELECT * FROM tableName; # 查询tableName中的所有列
SELECT DISTINCT col FROM tableName; # 查询tableName中的col列的所有不同结果
```
### limit和offset

- **limit**：限定查询结果的最大数量
- **offset**：设置偏移量
- **示例**
```sql
SELECT col FROM tableName LIMIT 5 OFFSET 6; # 查询从第6行开始的5行数据
SELECT col FROM tableName LIMIT 6, 5; # 简化写法
```
### order

- **order by**：一定需要保证其作为SELECT语句中最后一条子句,默认是升序
- **desc**：降序，只作用于其前一位列名
- **asc**：升序
- **示例**
```sql
SELECT col1, col2,col3 FROM tableName 
ORDER BY col1 ASC, col2 DESC; # 可以单个列排序，也可以按照多个列进行排序
```
### where
##### where基本用法
| **WHERE子句操作符** |  |  |  |
| --- | --- | --- | --- |
| = | 等于 | > | 大于 |
| <> | 不等于 | >= | 大于等于 |
| != | 不等于 | !> | 不大于 |
| < | 小于 | between | 在指定的两个值之间 |
| <= | 小于等于 | is null | 为NULL值 |
| !< | 不等于 |  |  |

- **示例**
```sql
SELECT col1, col2 FROM tableName
WHERE col1 < 10;

SELECT col1, col2 FROM tableName
WHERE col2 BETWEEN 5 AND 10; # 范围值检查

SELECT col1, col2 FROM tableName
WHERE col1 IS NULL; # 空值检查
```
##### where高级用法

- **and**：多层过滤
- **or**：多层过滤，优先级低于and，可以使用括号来限定
- **in**：去括号内的某值，，括号内值与值之间使用逗号分隔，和or功能相同
- **not**：否定其后所跟的任何条件
- **示例**
```sql
SELECT col1 , col2 FROM tableName
WHERE col1 = 'hello' AND col2 <= 4;

SELECT col1, col2, col3 FROM tableName
WHERE (col1 = 'hello' OR col2 = 'world') AND col3 >= 10;
# and优先级比or优先级高，所以需要加上圆括号
       
SELECT col1, col2 FROM tableName
WHERE col1 IN ('hello', 'world')
ORDER BY col2;

SELECT col1, col2 FROM tableName
WHERE NOT col1 = 'hello'
ORDER BY col2 DESC;
```
##### like

- **百分号通配符(%)**：匹配任何字符任意次数， 但是无法匹配null
- **下划线通配符(_)**：匹配单个字符
- **方括号通配符([])**：匹配指定字符集中的一个字符
- **示例**
```sql
SELECT col1, col2 FROM tableName
WHERE col1 LIKE '_F[abcKD]sh%';
```
### group by和having
##### group by
> 指定分组方式

- **示例**
```sql
SELECT vend_id, Count(*) AS num_prods
FROM Products
GROUP BY vend_id;
# 按照vend_id分组，之后对每一个组都进行Count(*)计算,所以会输出多条数据
```

- GROUP BY子句必须出现在WHERE子句之后，ORDER BY子句之前
##### having
> 过滤分组

- **示例**
```sql
SELECT cust_id, COUNT(*) AS orders
FROM Orders
GROUP BY cust_id
HAVING Count(*) >= 2;
```

- WHERE是在数据分组之前进行过滤，HAVING在数据分组之后进行过滤
### 计算字段
##### 拼接字段

- **concat(string1, string2, ...)**：无缝拼接，如果拼接的字段有一个是null，则返回null
- **concat_ws(separator, string1, string2, ...)**：将指定的separator作为分隔符进行拼接
- **rtrim(string)**：去掉两短的空格
- **as**：指定别名（alias）
- **示例**
```sql
SELECT Concat(RTrim(col1), ' (', RTrim(col2), ')') AS newCol FROM tableName
ORDER BY col1; #返回拼接形成的新的列
```
##### 算术运算

- **算术运算符：**支持加减乘除
- **示例**
```sql
SELECT col1, col2, col3, col2 * col3 AS newCol
FROM tableName
ORDER BY col4; # 输出四列，其中一列是导出列(别名)
```
##### 使用select测试计算

- **示例**
```sql
SELECT 3 * 2;

SELECT Now() AS Now; # 不加FROM子句
```
# 函数

- **convert()**：数据类型转换
### 常用文本处理函数
| **函数** | **说明** |
| --- | --- |
| _left()_ | 返回字符串左边的字符 |
| _right()_ | 返回字符串右边的字符 |
| _length()_ | 返回字符串的长度 |
| _lower()_ | 将字符串转换为小写 |
| _upper()_ | 将字符串转换为大写 |
| _ltrim()_ | 去除字符串左边的空格 |
| _rtrim()_ | 去除字符串右边的空格 |
| _trim()_ | 去除字符串两边的空格 |
| _substring()_ | 提取字符串的组成部分 |
| _concat()_ | 连接字符串 |
| _soundex_ | 返回字符串的SOUNDEX值，相似读音的字符串具有相同的值 |

### 数值处理函数
| **函数** | **说明** |
| --- | --- |
| _abs()_ | 返回一个数的绝对值 |
| _cos()_ | 返回一个角度的余弦 |
| _sin()_ | 返回一个角度的正弦 |
| _tan()_ | 返回一个角度的正切 |
| _exp()_ | 返回一个数的以e为底的指数值 |
| _sqrt()_ | 返回一个数的平方根 |
| _PI()_ | 返回圆周率的值 |

### 日期和时间处理函数

- **now**：返回当前日期加上时间
- **curdate()**：返回当前日期
- **curtime()**：返回当前时间
- **year()**：提取日期中的年份
### 聚集函数
> 对某些行和列运行的函数，计算并返回一个值
> 以下函数都会忽略null值，但是count(*)不忽略null值的列

| **函数** | **说明** |
| --- | --- |
| _avg()_ | 返回某列的平均值 |
| _count()_ | 返回某列的行数 |
| _max()_ | 返回某列的最大值 |
| _min()_ | 返回某列的最小值 |
| _sum()_ | 返回某列值的和 |

##### 聚集不同值

- **all**：默认模式
- **disdinct**：只计算不同值的列或行
- **示例**
```sql
SELECT Avg(DISTINCT price) AS avg_price
FROM tableName
WHERE vend_id = 'DLL01';
```
