# golang的并发编程（一）

本系列，是学习golang的并发编程的笔记篇，主要是代码实践和基础。

我们先从常见的基础面试题出发：

> 请使用go的协程，按顺序打印1~10

代码：

```go
package main

import (
	"fmt"
)

func main() {
	c := make(chan int, 1)
	go func() {
		for i:=0;i<10;i++{
			fmt.Println("..........",i)
		}
		c <- 1
	}()
	<-c
}
```

这里有个小技巧，就是使用`<-c`。

作为初学者，我们一般会使用`time.Sleep(1* time.Second)`，作为结束语，等待协程结束后退出。但是，我们使用通道`chan`，由于它接收数据一直会处于等待状态，所以可以很自然的等待协程结束。

---

程序原来编码：

```go
package main

import (
	"sync"
)

const N = 10

func main() {
	m := make(map[int]int)

	syncwg := &sync.WaitGroup{}
	syncmu := &sync.Mutex{}
	syncwg.Add(N)
	for i := 0; i < N; i++ {
		go func() {
			defer syncwg.Done()
			syncmu.Lock()
			m[i] = i
			syncmu.Unlock()
		}()
	}
	syncwg.Wait()
	println(len(m))
}
```

对for循环改造后：

```go
	for i := 0; i < N; i++ {
		go func(j int) {
			syncmu.Lock()
			m[j] = j
			syncmu.Unlock()
			defer syncwg.Done()
		}(i)
	}
```







### 参考文献

- [1.6万字长文：Go 协程的实现原理](https://mp.weixin.qq.com/s/nyTF3IgPf1qkBWCJZQuTuA)