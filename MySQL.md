<a name="E9bt6"></a>
# 基本操作
<a name="OY3WC"></a>
### 数据库

- **create**
- **drop**
- **use**
- **示例**
```sql
CREATE DATABASE Anvei;
DROP DATABASE Anvei;
USE Anvei;
```
<a name="MR2Ba"></a>
### 表格

- **create**
- **drop**
```sql
CREATE TABLE table_name (column_name column_type);
DROP TABLE table_name;
```
<a name="T57dn"></a>
### 数据类型
<a name="FvlcN"></a>
##### 数值类型
| 类型 | 大小 | 范围（有符号） | 范围（无符号） | 用途 |
| --- | --- | --- | --- | --- |
| TinyInt | 1 Bytes | (-128，127) | (0，255) | 小整数值 |
| SmallInt | 2 Bytes | (-32 768，32 767) | (0，65 535) | 大整数值 |
| MediumInt | 3 Bytes | (-8 388 608，8 388 607) | (0，16 777 215) | 大整数值 |
| Int或Integer | 4 Bytes | (-2 147 483 648，2 147 483 647) | (0，4 294 967 295) | 大整数值 |
| BigInt | 8 Bytes | (-9,223,372,036,854,775,808，9 223 372 036 854 775 807) | (0，18 446 744 073 709 551 615) | 极大整数值 |
| Float | 4 Bytes | (-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38) | 0，(1.175 494 351 E-38，3.402 823 466 E+38) | 单精度<br />浮点数值 |
| Double | 8 Bytes | (-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 双精度<br />浮点数值 |
| Decimal | 对DECIMAL(M,D) ，如果M>D，为M+2否则为D+2 | 依赖于M和D的值 | 依赖于M和D的值 | 小数值 |

<a name="LdA1R"></a>
##### 字符串类型
| 类型 | 大小 | 用途 |
| --- | --- | --- |
| Char | 0-255 bytes | 定长字符串 |
| VarChar | 0-65535 bytes | 变长字符串 |
| TinyBlob | 0-255 bytes | 不超过 255 个字符的二进制字符串 |
| TinyText | 0-255 bytes | 短文本字符串 |
| Blob | 0-65 535 bytes | 二进制形式的长文本数据 |
| Text | 0-65 535 bytes | 长文本数据 |
| MediumBlob | 0-16 777 215 bytes | 二进制形式的中等长度文本数据 |
| MediumText | 0-16 777 215 bytes | 中等长度文本数据 |
| LongBlob | 0-4 294 967 295 bytes | 二进制形式的极大文本数据 |
| LongText | 0-4 294 967 295 bytes | 极大文本数据 |

<a name="oxeIR"></a>
##### 日期和时间类型
| 类型 | 大小<br />( bytes) | 范围 | 格式 | 用途 |
| --- | --- | --- | --- | --- |
| Date | 3 | 1000-01-01/9999-12-31 | YYYY-MM-DD | 日期值 |
| Time | 3 | '-838:59:59'/'838:59:59' | HH:MM:SS | 时间值或持续时间 |
| Year | 1 | 1901/2155 | YYYY | 年份值 |
| DateTime | 8 | 1000-01-01 00:00:00/9999-12-31 23:59:59 | YYYY-MM-DD HH:MM:SS | 混合日期和时间值 |
| TimeStamp | 4 | 1970-01-01 00:00:00/2038<br />结束时间是第 **2147483647** 秒，北京时间 **2038-1-19 11:14:07**，格林尼治时间 2038年1月19日 凌晨 03:14:07 | YYYYMMDD HHMMSS | 混合日期和时间值，时间戳 |

<a name="VOLAy"></a>
# 表格数据操作
<a name="SnxC2"></a>
### 插入

- **insert **
```sql
INSERT INTO table_name ( field1, field2,...fieldN )
                       VALUES
                       ( value1, value2,...valueN );
```
<a name="mfvnN"></a>
### 更新

- **update**
```sql
UPDATE table_name SET field1=new_value1, field2=new_value2
[WHERE Clause];

# 示例
UPDATE table_name SET col1 = 'anvei'
WHERE col2 > 10;
```
<a name="ugT2T"></a>
### 删除

- **delete**
```sql
DELETE FROM table_name [WHERE Clause];

# 删除表中全部数据
DELETE FROM table_name;
# 使用where过滤
DELETE FROM table_name
WHERE col2 > 10;
```

<a name="lFELQ"></a>
# 查询
<a name="OjYne"></a>
### 注释

1. **--**：单行注释
1. **#**：单行注释
1. **/*	*/**：多行注释
<a name="KQ2Nc"></a>
### select

- **作用**：限定查询结果的列，用于控制输出
- **select**：后接列名，限定查询返回的列
- **from**：select子句，后接表名，指定从哪一个表中查询
- **distinct**：必须放在列名前面
- *** **：通配符，匹配全部列
- **示例**
```sql
SELECT col1, col2, col3 FROM tableName; # 查询tableName中的col1,col2,col3列
SELECT * FROM tableName; # 查询tableName中的所有列
SELECT DISTINCT col FROM tableName; # 查询tableName中的col列的所有不同结果
```
<a name="pxBql"></a>
### limit和offset

- **limit**：限定查询结果的最大数量
- **offset**：设置偏移量
- **示例**
```sql
SELECT col FROM tableName LIMIT 5 OFFSET 6; # 查询从第6行开始的5行数据
SELECT col FROM tableName LIMIT 6, 5; # 简化写法
```
<a name="ykJ5i"></a>
### order

- **order by**：一定需要保证其作为SELECT语句中最后一条子句,默认是升序
- **desc**：降序，只作用于其前一位列名
- **asc**：升序
- **示例**
```sql
SELECT col1, col2,col3 FROM tableName 
ORDER BY col1 ASC, col2 DESC; # 可以单个列排序，也可以按照多个列进行排序
```
<a name="XCHt4"></a>
### where
<a name="tbifI"></a>
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
<a name="L3wj3"></a>
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
<a name="tSWvT"></a>
##### like

- **百分号通配符(%)**：匹配任何字符任意次数， 但是无法匹配null
- **下划线通配符(_)**：匹配单个字符
- **方括号通配符([])**：匹配指定字符集中的一个字符
- **示例**
```sql
SELECT col1, col2 FROM tableName
WHERE col1 LIKE '_F[abcKD]sh%';
```
<a name="Fuy7N"></a>
### group by和having
<a name="uZvJG"></a>
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
<a name="JsnHD"></a>
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
<a name="F5gs4"></a>
### 计算字段
<a name="iw64H"></a>
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
<a name="fpJGt"></a>
##### 算术运算

- **算术运算符：**支持加减乘除
- **示例**
```sql
SELECT col1, col2, col3, col2 * col3 AS newCol
FROM tableName
ORDER BY col4; # 输出四列，其中一列是导出列(别名)
```
<a name="mFMMo"></a>
##### 使用select测试计算

- **示例**
```sql
SELECT 3 * 2;

SELECT Now() AS Now; # 不加FROM子句
```
<a name="rIyih"></a>
# 函数

- **convert()**：数据类型转换
<a name="AqVjA"></a>
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

<a name="d6bDR"></a>
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

<a name="inSap"></a>
### 日期和时间处理函数

- **now**：返回当前日期加上时间
- **curdate()**：返回当前日期
- **curtime()**：返回当前时间
- **year()**：提取日期中的年份
<a name="NXQWS"></a>
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

<a name="dfYW3"></a>
##### 聚集不同值

- **all**：默认模式
- **disdinct**：只计算不同值的列或行
- **示例**
```sql
SELECT Avg(DISTINCT price) AS avg_price
FROM tableName
WHERE vend_id = 'DLL01';
```
<a name="lfGIW"></a>
### 子查询

- **子查询实现过滤**
- **子查询实现计算字段**
- **示例**
```sql
SELECT cust_name, cust_contact
FROM Customers
WHERE cust_id IN (SELECT cust_id
                  FROM Orders
                  WHERE orders_num IN (SELECT order_num
                                       FROM OrderItems
                                       WHERE prod_id = 'RGAN01'));
# 嵌套select实现计算字段
SELECT cust_name, 
       cust_state,
       (SELECT Count(*) FROM Orders	# 完全限定列名，指明了表名和列名
       WHERE Orders.cust_id = Customers.cust_id) AS orders
FROM Customers
ORDER BY cust_name;
```
