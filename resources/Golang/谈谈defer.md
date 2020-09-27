# 谈谈defer



### 执行顺序

defer在同一个函数中可以使用多次。

多个defer指定的函数执行顺序是"先进后出"：

```go
package main

import "fmt"

func foo() {
	i := 0
	defer func() {
		i--
		fmt.Println("第一个defer", i)
	}()

	i++
	fmt.Println("+1后的i：", i)

	defer func() {
		i--
		fmt.Println("第二个defer", i)
	}()

	i = 8
	fmt.Println("再+1后的i：", i)
}

func main() {
	foo()
}
输出：
+1后的i： 1
再+1后的i： 8
第二个defer 7
第一个defer 6
```

### 值传递

**defer指定的函数的参数在 defer 时确定**，但，这只是一个总结，真正的原因是， **Go语言除了map、slice、chan都是值传递**。

```go
package main

import "fmt"

func foo() {
	i := 0
	defer func(k int) {
		fmt.Println("第一个defer", k)
	}(i)

	i++
	fmt.Println("+1后的i：", i)

	defer func(k int) {
		fmt.Println("第二个defer", k)
	}(i)

	i=8
	fmt.Println("再+1后的i：", i)
}

func main() {
	foo()
}
输出：
+1后的i： 1
再+1后的i： 8
第二个defer 1
第一个defer 0
```

也就是说，`defer`的值，在传入函数的时候，就已经确定了。但是，这个不适用于map、slice、chan。因为他们都是浅拷贝，他们在某个位置的改变，会导致其指针地址的改变。





### 参考

- [Golang研学：如何掌握并用好defer（延迟执行）](https://segmentfault.com/a/1190000019063371)

