# mysql
## 常用命令
1. 显示数据库：`mysql>show databases;`
2. 显示数据表：`mysql>show tables;`
3. 显示数据表的所有字段：`mysql>show columns from table_name;`
4. 新增字段：`mysql> ALTER TABLE testalter_tbl ADD i INT;`
    >* 会新增字段在数据表末尾
    >*  如果你需要指定新增字段的位置，可以使用MySQL提供的关键字 FIRST (设定位第一列)， AFTER 字段名（设定位于某个字段之后）。尝试以下 ALTER TABLE 语句, 在执行成功后，使用 SHOW COLUMNS 查看表结构的变化：
    >```mysql
    >ALTER TABLE testalter_tbl DROP i;
    >ALTER TABLE testalter_tbl ADD i INT FIRST;
    >ALTER TABLE testalter_tbl DROP i;
    >ALTER TABLE testalter_tbl ADD i INT AFTER c;
    >```