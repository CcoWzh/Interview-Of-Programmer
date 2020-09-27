# MySQL入门基础

### 1.基本语法

```mysql
-- 显示所有数据库
show databases;

-- 创建数据库
CREATE DATABASE test;

-- 切换数据库
use test;

-- 显示数据库中的所有表
show tables;

-- 创建数据表
CREATE TABLE IF NOT EXISTS `pet`(
   `runoob_id` INT UNSIGNED AUTO_INCREMENT, //自增
   `runoob_title` VARCHAR(100) NOT NULL,
   `runoob_author` VARCHAR(40) NOT NULL,
   `submission_date` DATE,
   PRIMARY KEY ( `runoob_id` ) //指定主键
)ENGINE=InnoDB DEFAULT CHARSET=utf8; //指定使用的数据库引擎、编码格式

-- 查看数据表结构
-- describe pet;
desc pet;

-- 查询表
SELECT * from pet;

-- 插入数据
INSERT INTO pet VALUES ('puffball', 'Diane', 'hamster', 'f', '1990-03-30', NULL);

-- 修改数据
UPDATE pet SET name = 'squirrel' where owner = 'Diane';

-- 删除数据
DELETE FROM pet where name = 'squirrel';

-- 删除表
DROP TABLE myorder;
```







### 参考

- [20000 字干货笔记，一天搞定 MySQL ！](https://mp.weixin.qq.com/s/XF56o9RNdJkOgQ3fEP4yAA)
- [MySQL数据库面试题（2020最新版）](https://mp.weixin.qq.com/s/zsjX-AltvUQqEJ0F-wqIRw)

