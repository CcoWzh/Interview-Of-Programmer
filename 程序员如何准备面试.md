# 程序员如何准备面试

## 这是？

这是我在研二期间，为准备面试而学习的一些知识。在研究生以前，我从来没有正经编程过，对于计算机的了解还停留在一个“荒废大学生”该有的地方。为了不虚度光阴，可以找到一份不错的工作，研究生期间不断学习数据结构和算法、计算机网络和数据库操作等。

所以，与其说这是一份面试前的准备工作，不如说是我这半年来的一些总结。受网上开源的恩惠，这里开源自己的学习经历、计划等，希望对大家在找工作的过程中有所帮助。

## 目录

- [这是？](#这是？)
- [为面试选择一种语言](#为面试选择一种语言)
- [如何学习](#如何学习)
- [数据结构和算法](#数据结构和算法)
  - [栈和队列](#栈和队列（Stack & Queue）)
  - [链表](#链表)
- [计算机网络协议](#计算机网络协议)
  - [TCP和UDP](#TCP和UDP)
  - [socket编程](#socket编程)
- [操作系统](#操作系统)
  - [进程和线程](#进程和线程)
  - [I/O多路复用](#I/O多路复用)
- [数据库](#数据库)
  - [B-树和B+树](#B-树和B+树)
  - [红黑树和HashMap](#红黑树和HashMap)
- [Go语言](#Go语言)
  - [Go并发编程](#Go并发编程)
- [你的简历](#你的简历)

## 为面试选择一种语言

在准备面试前，选择一两个自己熟练掌握的编程语言。在大多数公司的面试当中，你可以在编程这一环节，使用一种自己用起来较为舒适的语言去完成编程。

这里，推荐的是主流语言：

- C++
- Java
- Python

由于笔者的学习经历和研究方法，我的第一开发语言是Go，所以，下面的一些示例是使用go语言编写的。但是笔者认为，编程语言并不是界限，当你掌握的一项技术的底层原理的时候，语言只是你实现原理的工具而已。比如，你知道了`TCP/IP`的网络编程和`socket`，那么你在使用不同语言编程的时候，都是会知道一定要使用什么方法、编程顺序和框架是怎么样子的。

如果你对Go语言感兴趣，可以参考以下学习资料：

- [go语言中文文档](http://www.topgoer.com/)
- [go语言圣经](https://wizardforcel.gitbooks.io/gopl-zh/content/preface.html)
- [为什么这样设计](https://draveness.me/whys-the-design/)

## 如何学习

谈论如何学习，这个话题就很大了，而且感觉我也没有资格教别人如何学习。这里，我分享以下我是如何学习的吧。

首先，是刷题。由于自己的数据结构和算法方面的知识基太差了，这里推荐机构刷题网址：

- [力扣LeetCode](https://leetcode-cn.com/)

- [牛客网](https://www.nowcoder.com/)

关于书籍：

- [ ] 《剑指Offer》
- [ ] 《算法 第4版》
- [ ] 《TCP/IP详解 卷1：协议》
- [ ] 《现代操作系统》
- [ ] 《计算机网络（谢希仁版）》
- [ ] 《计算机网络自顶向下方法》
- [ ] 《操作系统精髓与设计原理》

多上`GitHub`：

- [自学计算机科学](https://github.com/keithnull/TeachYourselfCS-CN/blob/master/TeachYourselfCS-CN.md)  自学计算机编程的人的福音，列举出了经典的计算机学习科目，使知识结构自成系统
- [每个程序员都应该尝试的挑战性项目](https://www.jianshu.com/p/1d3b1c78041a)
- [Effective Go](https://studygolang.com/articles/1976)

公开课：

- [MIT 6.824 Distributed Systems Spring 2020 分布式系统 中文翻译版合集](https://www.bilibili.com/video/BV1x7411M7Sf?p=5)
- [[中字]麻省理工学院公开课：计算机科学的数学 MIT 6.042J&18.062J（共二十五讲）](https://www.bilibili.com/video/BV1Kb411n7oa)

## 数据结构和算法

掌握典型的、常见的数据结构和算法，不仅为了面试，也为了以后的编程生涯，都是必要的。

- ### 栈和队列（Stack & Queue）

  - [ ] 我的文档总结
  - [ ] [数据结构和算法(Golang实现)(14)常见数据结构-栈和队列](https://segmentfault.com/a/1190000022288631)

- ### 链表

- ### 二叉树

- ### BFS和DFS

  - [ ] `BFS`的编程框架

- ### 二分查找

  - [ ] 二分查找的一般框架

- ### 回溯法

  - [回溯算法详解（修订版）](https://mp.weixin.qq.com/s?__biz=MzAxODQxMDM0Mw==&mid=2247484709&idx=1&sn=1c24a5c41a5a255000532e83f38f2ce4&chksm=9bd7fb2daca0723be888b30345e2c5e64649fc31a00b05c27a0843f349e2dd9363338d0dac61&scene=21#wechat_redirect)

- ### 排序算法

  - [各大排序算法对比](https://goa.lenggirl.com/algorithm/sort.html)

- ### 堆和优先队列

  - [ 优先队列及堆排序](https://goa.lenggirl.com/algorithm/heaplike/heaps.html#优先队列及堆排序)
  - [图解排序算法(三)之堆排序](https://www.cnblogs.com/chengxiao/p/6129630.html)

- ### 红黑树和HashMap

  - [数据结构和算法(Golang实现)(29)查找算法-2-3树和左倾红黑树](https://segmentfault.com/a/1190000022289012)
  - [漫画：什么是HashMap？](https://zhuanlan.zhihu.com/p/31610616)
  - [Go 语言设计与实现--3.3哈希表](https://draveness.me/golang/)

- ### LRU缓存算法

  - [动手写分布式缓存 - GeeCache第一天 LRU 缓存淘汰策略](https://geektutu.com/post/geecache-day1.html)
  - [7天用Go从零实现系列](https://github.com/geektutu/7days-golang)

- ### 学习资料

  - [全部文章分类与整理（算法+数据结构+计算机基础），持续更新](https://mp.weixin.qq.com/s/MArPUE8wmDNMAalvzoLgcA)
  - [算法模板(go语言版)](https://greyireland.gitbook.io/algorithm-pattern/)
  - [算法的动态演示](https://www.cs.usfca.edu/~galles/visualization/Algorithms.html)
  - [小浩算法](https://www.geekxh.com/2.0.排序系列/0.hello.html)

## 计算机网络协议

- ### `TCP`和`UDP`

  - [ ] 三次握手和四次挥手
  - [ ] 滑动窗口
  - [ ] 拥塞算法
  - [ ] 重传和丢包处理
  - [计算机网络很难吗？这篇文章足够!](https://www.toutiao.com/i6814395733114880520/?tt_from=weixin&utm_campaign=client_share&wxshare_count=1&timestamp=1586783361&app=news_article&utm_source=weixin&utm_medium=toutiao_android&req_id=20200413210921010129035144022F46FC&group_id=6814395733114880520)
  - [你还在为 TCP 重传、滑动窗口、流量控制、拥塞控制发愁吗？看完图解就不愁了](https://mp.weixin.qq.com/s/Tc09ovdNacOtnMOMeRc_uA)
  - [探究！一个数据包在网络中的心路历程](https://mp.weixin.qq.com/s?__biz=MzUxODAzNDg4NQ==&mid=2247483989&idx=1&sn=7e2ed852770743d3955ef9d5561fcef3&scene=21#wechat_redirect)

- ### socket编程

  - [ ] [socket套接字编程](http://www.topgoer.com/网络编程/socket编程/)

## 操作系统

- ### 进程和线程

  - [ ] 什么是进程，什么是线程
    - [go 中的GMP 原理与调度](http://www.topgoer.com/并发编程/GMP原理与调度.html)
    - [当初我要是这么学习「进程和线程」就好了（附带思维导图）](https://mp.weixin.qq.com/s/zVi45pZka_kPpKIoNXNVBA)

- ### I/O多路复用

  - [ ] select、poll和`epoll`的区别
    - [聊聊IO多路复用之select、poll、epoll详解](https://www.jianshu.com/p/dfd940e7fca2)
    - [【操作系统】I/O 多路复用，select / poll / epoll 详解](https://imageslr.github.io/2020/02/27/select-poll-epoll.html#select-%E4%BD%BF%E7%94%A8%E7%A4%BA%E4%BE%8B)
  - [ ] `epoll`底层实现原理
  
- ### Linux的常见命令

  - [如何查看和监控日志](https://www.cnblogs.com/xiaozengzeng/p/12492580.html)
  - [如何查看CPU](https://blog.csdn.net/yuanchunsi/article/details/79295801)
  - [如何查看进程情况](https://www.jianshu.com/p/002efd45ea46)

## 数据库

- ### B-树和B+树

  - [ ] `MySQL`的数据库底层`InnoDB`
  - [ ] `InnoDB`的索引原理
    - [【面试现场】为什么MySQL数据库要用B+树存储索引？](https://mp.weixin.qq.com/s/-qnYTrKNZeOE9Mvn4kyugg)
    - [高频面试题：什么是B树？为啥文件索引要用B树而不用二叉查找树？](https://mp.weixin.qq.com/s/eM_2ChIEkZb_kSXb6Q9n6g)
    - [MySQL索引背后的数据结构及算法原理](http://blog.codinglabs.org/articles/theory-of-mysql-index.html)

- ### 数据库基础

  - [ ] `MySQL`数据
    - [后端程序员必备：mysql数据库相关流程图/原理图](https://juejin.im/post/5d42f48cf265da03ab422e08)
    - 索引
    - 锁机制
  - [ ] `Redis`数据库
    - [Redis持久化RDB和AOF](https://juejin.im/post/5bb02c42e51d450e92524b6f)


## Go语言

- ### 语法考点

  - [ ] interface编程
  
    - [go 面向对象之接口](http://www.topgoer.com/面向对象/接口.html)
  
    - [Golang中interface内部构造与面试真题分析](https://mp.weixin.qq.com/s/WIjVX-yXHZEOZoayT_m3MA)
  - [ ] go和Java的区别
  - [ ] make和new的区别
  - [ ] Slice的底层实现，和数组的区别
  - [ ] HashMap底层原理
    - [Golang map的底层实现](https://www.cnblogs.com/maji233/p/11070853.html)
    - [数据结构和算法(Golang实现)(26)查找算法-哈希表](https://segmentfault.com/a/1190000022288951)
  - [ ] Go垃圾回收机
    - [深入理解Go-垃圾回收机制](https://segmentfault.com/a/1190000020086769)
    - [[典藏版]Golang三色标记、混合写屏障GC模式图文全分析](https://mp.weixin.qq.com/s?__biz=MzAxMTA4Njc0OQ==&mid=2651439356&idx=2&sn=264a3141ea9a4b29fe67ec06a17aeb99&chksm=80bb1e0eb7cc97181b81ae731d0d425dda1e9a8d503ff75f217a0d77bd9d0eb451555cb584a0&scene=126&sessionid=1588555766&key=c70cad9466e6a572225c8bfccc37707794cb44c1fcdfb5ddd596ee58b390dbd1751cf2fd3799a532fb9265fefbfe8e7e3fbf5a2dfdb8c2741550355f20902bb83f1f5d159fa53553b531c5fa734059f3&ascene=1&uin=OTg2NTk3NTA2&devicetype=Windows+10+x64&version=62090070&lang=zh_CN&exportkey=A7JE9D6MH18m5JR37yDK4zo%3D&pass_ticket=LqNtBMfJ2C4uaOLa5%2FIf7%2BeKoMS8teYE7SzPUQHtQ6Gs7ehxbm0hr5V%2FKVfH2y5j)
    - [不止面试-JVM垃圾回收面试题详解](https://www.cnblogs.com/bailiyi/p/12013756.html)
    - [On-the-fly garbage collection: an exercise in cooperation](http://www.researchgate.net/publication/221621538_On-the-fly_garbage_collection_an_exercise_in_cooperation)
  - [ ] 面试常问
    - [Golang 面试题总结](https://blog.csdn.net/m0_38031406/article/details/104840696)
    - [Golang进阶面试题整理](https://blog.csdn.net/sinat_35406909/article/details/103818364?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param)
    - [golang 面试题整理](https://www.jianshu.com/p/6bf41d9dcb6e)
    - [Golang面试题解析](https://blog.csdn.net/weiyuefei/article/details/77963810?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param)
  
- ### Go并发编程

  - [ ] 什么是`gorountine`?
  - [ ] channel的使用和底层实现
  - [ ] select的底层原理
  - [ ] `GMP`并发模型

- ### 规范工具和测试工具

  - [ ] 代码规范检测工具`golint`

- ### gRPC原理

  - [ ] gRPC原理和用法
    - [带入gRPC：基于 CA 的 TLS 证书认证](https://segmentfault.com/a/1190000016601810)
  
- ### 编程语言

  - [什么是拷贝与浅拷贝](https://mp.weixin.qq.com/s?__biz=MzAxMTA4Njc0OQ==&mid=2651439391&idx=5&sn=3a06a7c9877c774f8012485243f117f3&chksm=80bb1fedb7cc96fb16af6d6a74d2ebe7ae6f593a5041b23dd808de680702c1fd052cf14cd5f6&scene=126&sessionid=1588555766&key=3bc555d722b85ff328f7d59980f1d9a20e242d4e242d5aa6ef4e125c8ca4501a2ee5ba51a230af0798ce485324b6e7da238de73bed6fc119278bfc2f4ec52ba849404ffa636a1258e06c4d223b1a888f&ascene=1&uin=OTg2NTk3NTA2&devicetype=Windows+10+x64&version=62090070&lang=zh_CN&exportkey=AzGL4h9Ie7JadnViuugdxpM%3D&pass_ticket=LqNtBMfJ2C4uaOLa5%2FIf7%2BeKoMS8teYE7SzPUQHtQ6Gs7ehxbm0hr5V%2FKVfH2y5j)  Go语言讲解深拷贝与浅拷贝
  
- ### 学习资料

  - [数据结构和算法（Golang实现）](https://goa.lenggirl.com/)
  - [Go 语言设计与实现](https://draveness.me/golang/)
  - [Golang官网](https://go.dev/)

## 工具

- ### Git

  - [ ] 什么是git，基本用法
  - [ ] [这才是真正的Git——Git内部原理揭秘！](https://mp.weixin.qq.com/s/UQKrAR3zsdTRz8nFiLk2uQ)
  - [ ] [我用四个命令，总结了 Git 的所有套路](https://mp.weixin.qq.com/s/VdeQpFCL3GGsfOKrIRW6Hw)
  - [ ] [图解Git](https://marklodato.github.io/visual-git-guide/index-zh-cn.html)
  
- ### Docker

  - [Docker 核心技术与实现原理](https://mp.weixin.qq.com/s?__biz=MzAxMTA4Njc0OQ==&mid=2651438399&idx=2&sn=f5e8ab227a4e3a1994de04a9c7f0ad8e&chksm=80bb63cdb7cceadbba03342812ac0a6d3904654e9864a01c9ed347d93a901423c4a9de8084a7&scene=21#wechat_redirect)
  - [既然有了 Docker，为什么还要 Kubernetes？](https://mp.weixin.qq.com/s?__biz=MzAxMTA4Njc0OQ==&mid=2651438165&idx=4&sn=3ce0810889c0a72f5528bf3d861c7012&chksm=80bb62a7b7ccebb1785248013c6806c14c8f921a70c6d50bfea991f53cd9584c561583a466a5&scene=21#wechat_redirect)

## 你的简历

- [超级简历](https://www.wondercv.com/)

## 优质好文

这是笔者在编程学习过程中，看到的一些优质毒鸡汤，可以帮助自己思考以后的编程生涯发展规划等。

- [自学编程的八大误区！克服它！](https://mp.weixin.qq.com/s/NwSzbizFR7beha1DlmZgfA)
- [职场经验！两年滴滴和头条的后端开发经验！字字都是肺腑之言！](https://mp.weixin.qq.com/s/z0Npn4xFOyh-8hr_qGKLuw)
- [如何高效的学习技术](https://www.cnblogs.com/xiaoyangjia/p/11535486.html)

- [大学四年告诉帅地，计算机系的同学应该要有更高的雄心壮志](https://mp.weixin.qq.com/s/aRWdF7t8UV4dGT76oiKDhg)

