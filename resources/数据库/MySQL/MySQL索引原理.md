# MySQL索引原理

查找算法：

- 二叉查找树
- B-Tree和B+Tree
- Hash
- BitMap位图

### 索引分类

- 主键索引
- 唯一索引
- 普通索引
- 全文索引

### 索引原理解析

- B+树
- 聚集索引和非聚集索引

### 建立索引

- 创建表时指定
- alter
- create

### 组合索引

- 什么是覆盖索引和回表查询
- 最左匹配原则
- 优化explain

### 面试常考

- 什么时候索引会失效
- 索引建立得越多越好吗？
- 为什么多用组合索引
- B+树和B-树的区别
- InnoDB和MyISAM的区别

 

### 参考

- [MySQL 的覆盖索引与回表](https://zhuanlan.zhihu.com/p/107125866)

- [很用心的为你写了 9 道 MySQL 面试题](https://mp.weixin.qq.com/s/RohdwFtM9Z_xRA2xGLA4pA)

- [深入理解 MySQL 索引底层原理](https://mp.weixin.qq.com/s/qHJiTjpvDikFcdl9SRL97Q)

- [Mysql什么是回表查询和覆盖索引](https://www.cnblogs.com/ghoster/p/12510691.html)

- [什么是覆盖索引?如何利用覆盖索引进行SQL语句优化？](https://blog.csdn.net/qq_15037231/article/details/87891683)