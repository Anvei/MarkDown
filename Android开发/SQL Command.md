1 . 删除表格tableName
```SQL
drop table if exists tableName
```
2 . 查找表格tableName中的全部数据
```SQL
select * from tableName
```
3 . 创建一个表格
```SQL
create table Book(
    id integer primary key autoincrement ,
    author text ,
    name text ,
    price real ,
    pages integer
)
```