

# 事务的隔离级别

### ACIDS

一说到 MySQL 事务，你肯定能想起来四大特性：`原子性`、`一致性`、`隔离性`、`持久性`，下面再对这事务的四大特性做一个描述

- `原子性(Atomicity)`: 原子性指的就是 MySQL 中的包含事务的操作要么`全部成功`、要么全部`失败回滚`，因此事务的操作如果成功就必须要全部应用到数据库，如果操作失败则不能对数据库有任何影响。

> 这里涉及到一个概念，什么是 MySQL 中的事务？
>
> 事务是一组操作，组成这组操作的各个单元，要不全都成功要不全都失败，这个特性就是事务。
>
> 在 MySQL 中，事务是在引擎层实现的，只有使用 `innodb` 引擎的数据库或表才支持事务。

- `一致性(Consistency)`：一致性指的是一个事务在执行前后其状态一致。比如 A 和 B 加起来的钱一共是 1000 元，那么不管 A 和 B 之间如何转账，转多少次，事务结束后两个用户的钱加起来还得是 1000，这就是事务的一致性。
- `持久性(Durability)`: 持久性指的是一旦事务提交，那么发生的改变就是永久性的，即使数据库遇到特殊情况比如故障的时候也不会产生干扰。
- `隔离性(Isolation)`：隔离性需要重点说一下，当多个事务同时进行时，就有可能出现`脏读(dirty read)`、`不可重复读(non-repeatable read)`、`幻读(phantom read)` 的情况，为了解决这些并发问题，提出了隔离性的概念。

> 脏读：事务 A 读取了事务 B 更新后的数据，但是事务 B 没有提交，然后事务 B 执行回滚操作，那么事务 A 读到的数据就是脏数据
>
> 不可重复读：事务 A 进行多次读取操作，事务 B 在事务 A 多次读取的过程中执行更新操作并提交，提交后事务 A 读到的数据不一致。
>
> 幻读：事务 A 将数据库中所有学生的成绩由 A -> B，此时事务 B 手动插入了一条成绩为 A 的记录，在事务 A 更改完毕后，发现还有一条记录没有修改，那么这种情况就叫做出现了幻读。

### 隔离级别

SQL的隔离级别有四种，它们分别是`读未提交(read uncommitted)`、`读已提交(read committed)`、`可重复读(repetable read)` 和 `串行化(serializable)`。下面分别来解释一下。

读未提交：读未提交指的是一个事务在提交之前，它所做的修改就能够被其他事务所看到。

读已提交：读已提交指的是一个事务在提交之后，它所做的变更才能够让其他事务看到。

可重复读：可重复读指的是一个事务在执行的过程中，看到的数据是和启动时看到的数据是一致的。未提交的变更对其他事务不可见。

串行化：顾名思义是对于同一行记录，`写`会加`写锁`，`读`会加`读锁`。当出现读写锁冲突的时候，后访问的事务必须等前一个事务执行完成，才能继续执行。

这四个隔离级别可以解决脏读、不可重复读、幻象读这三类问题。总结如下

![img](https://mmbiz.qpic.cn/mmbiz_png/libYRuvULTdUjIID8CJZm0kCpUTFyVGvJlYpsic62D3g4pk1dpAtpt22HDoKzS3GtqDUxVbBMuYprLXA15GVQlkw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

其中隔离级别由低到高是：读未提交 < 读已提交 < 可重复读 < 串行化

隔离级别越高，越能够保证数据的完整性和一致性，但是对并发的性能影响越大。大多数数据库的默认级别是`读已提交(Read committed)`，比如 Sql Server、Oracle ，但是 MySQL 的默认隔离级别是 `可重复读(repeatable-read)`。

---

脏读： 正在执行的事务 读取到其他事物未提交的数据

提交读：正在执行的事务 读取到其他事务已提交的数据 读取到其他事务已提交的修改 造成了不可重读， 读取到其他事务的插入 造成了幻读

可重复读： 正在执行的事务 读取不到其他事务已提交或未提交的修改，但能读到其他事务已提交的插入 所以造成幻读

可串行化： 最高的默认级别，强制事务串行执行（即一个事务一个事务执行）。效率极其低下。

幻读： 正在执行的事务 读取倒了其他事务已提交的插入

不可重复读： 正在执行的事务 读取到了其他事务的修改

---

可重复读和可串行化的区别：

- 幻读
- 加锁
- 隔离级别

### MVCC

**多版本并发控制（MVCC）**的实现是通过保存数据在某个时间点的**快照**来实现的。根据事务的创建时间不同，多个并发事务对同一张表，同一时刻看到的数据可能是不一样的。

InnoDB 的 MVCC 是通过在每行记录后面保存两个隐藏的列来实现的：

- 行的**创建时间**；*（创建版本）*
- 行的**过期时间**（或**删除时间**）；*（删除版本）*

存储的实际值是**系统版本号**（system version number）。

**每开始一个新的事务，系统版本号都会递增**。事务开始时刻的系统版本号作为事务的版本号，用来和查询到的每行记录的版本号进行比较。

在 `可重复读` 隔离级别下，MVCC 的具体操作：

- `select`：InnoDB 要查找当前存在的行，并且当前未被删除的行，`同时具体`两个条件：
  - **创建版本号**早于当前事务的版本号
  - **删除版本号**晚于当前事务的版本号
- `insert`：InnoDB 新插入的行，**创建版本号** = 当前事务的版本号
- `delete`：InnoDB 删除的行，**删除版本号** = 当前事务的版本号
- `update`：InnoDB 实际插入新纪录，具体：
  - 对于新纪录，**创建版本号** = 当前事务的创建版本号
  - 对于原纪录，**删除版本号** = 当前事务的创建版本号

### 事务的实现原理

重做日志，回滚日志以及锁技术就是实现事务的基础。

- 事务的原子性是通过 undo log （回滚日志）来实现的
- 事务的持久性性是通过 redo log（重做日志）来实现的
- 事务的隔离性是通过 (读写锁+MVCC)来实现的
- 而事务的终极大 boss **一致性**是通过原子性，持久性，隔离性来实现的！！！

**原子性，持久性，隔离性折腾半天的目的也是为了保障数据的一致性！**

总之，ACID只是个概念，事务最终目的是要保障数据的可靠性，一致性。

### 参考文献

- [快速理解 脏读，提交读（不可重复读）， 可重复读， 可串行化 和 幻读](https://blog.csdn.net/lzq199528/article/details/106239392/)

- [MySQL 技术内幕：事务隔离级别和MVCC](http://ningg.top/inside-mysql-transaction-and-mvcc/)
- [透彻解读mysql的可重复读、幻读及实现原理]([https://blog.csdn.net/sanyuesan0000/article/details/90235335?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param#%E4%BA%8C%E3%80%81mysql%E6%80%8E%E4%B9%88%E5%AE%9E%E7%8E%B0%E7%9A%84%E5%8F%AF%E9%87%8D%E5%A4%8D%E8%AF%BB](https://blog.csdn.net/sanyuesan0000/article/details/90235335?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param#二、mysql怎么实现的可重复读))

- [mysql 事务的实现原理](https://www.cnblogs.com/wyc1994666/p/11367051.html)

- [MySQL 事务的实现原理，写得太好了！](https://mp.weixin.qq.com/s/BLmcN_hhen-lbbSlGIQcCQ)

