# 谈谈panic和recover

函数调用`panic` 时会立刻停止执行函数的其他代码

### 什么时候应该使用 panic？

在 Go 语言中，程序中一般是使用错误来处理异常情况。对于程序中出现的大部分异常情况，错误就已经够用了。

但在有些情况，当程序发生异常时，无法继续运行。在这种情况下，我们会使用 `panic` 来终止程序。当函数发生 panic 时，它会终止运行，在执行完所有的defer函数后，程序控制返回到该函数的调用方。

需要注意的是，你应该尽可能地使用错误，而不是使用 panic 和 recover。只有当程序不能继续运行的时候，才应该使用 panic 和 recover 机制。

panic 有两个合理的用例：

1. **发生了一个不能恢复的错误，此时程序不能继续运行。 一个例子就是 web 服务器无法绑定所要求的端口。在这种情况下，就应该使用 panic，因为如果不能绑定端口，啥也做不了。**
2. **发生了一个编程上的错误。 假如我们有一个接收指针参数的方法，而其他人使用 `nil` 作为参数调用了它。在这种情况下，我们可以使用 panic，因为这是一个编程错误：用 `nil` 参数调用了一个只能接收合法指针的方法。**

### 用法

首先，panic 是用来表示非常严重的不可恢复的错误的。在Go语言中这是一个内置函数，如果在程序中遇到异常，或者调用panic函数，程序会立即退出（除非recover）。如下代码：

我们来看一个panic的例子：

```go
package main

import "fmt"

func main() {
	a := 10
	b := 0
	c := a / b
	fmt.Println("a/b is ", c)
}
输出：
panic: runtime error: integer divide by zero

goroutine 1 [running]:
main.main()
	F:/我的文档/我的文档/面试准备/goroutines/panic/main.go:8 +0x11
```

那么，当发生panic时，我们如何优雅的退出程序呢？也就是说，不让程序立刻停止、退出。

defer能保证在函数结束最后执行该方法（有问题的或者引发panic的函数),但是有个条件：必须在错误出错之前进行拦截，在错误出现后进行错误捕获，如果在定义的方法中defer定义的方法如果在panic后面，defer定义的方法就无法执行到。

```go
package main

import "fmt"

func compute(a, b int) int {
	return a / b
}

func main() {
	defer func() {
		if err := recover(); err != nil {
			fmt.Println(err)
		}
	}()
	c := compute(10, 0)
	fmt.Println("a/b is ", c)
	fmt.Println("hello world")
}
输出：
runtime error: integer divide by zero

Process finished with exit code 0
```

稍微改造一下，我们发现：

```go
package main

import "fmt"

func compute(a, b int) int {
	defer func() {
		if err := recover(); err != nil {
			fmt.Println(err)
		}
	}()
	return a / b
}

func main() {
	c := compute(10, 0)
	fmt.Println("a/b is ", c)
	fmt.Println("hello world")
}
输出：
runtime error: integer divide by zero
a/b is  0
hello world

Process finished with exit code 0
```

总结：

遇到异常时，一般会调用panic，同时，造成程序的中止、崩溃；

使用recover，一般都是和defer连着使用的，他会捕获一个异常，中止 `panic` 造成的程序崩溃。

### 什么是defer

defer：在函数A内用defer关键字调用的函数B会在在函数A return后执行。

#### 总结

1. defer语句非常重要，非常常用，必须掌握
2. 在统一处理多个`return`和`panic/recover`场景下使用defer，还有就是，连接了资源（数据库链接、文件句柄、TCP网络流）后，需要释放的场景下。
3. 谨记“Go语言的函数参数传递的都是值（除了map、slice、chan）”这一重要原则，正确的评估defer指定函数的参数值
4. defer不影响返回值，除非是map、slice和chan，或者返回值定义了变量名
5. 执行顺序：先进后出





### 参考

- [深入理解 Go panic and recover](https://segmentfault.com/a/1190000019251478)

- [Golang研学：如何掌握并用好defer（延迟执行）](https://segmentfault.com/a/1190000019063371)