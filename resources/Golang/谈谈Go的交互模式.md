# Golang的交互模式----读取用户的输入

读写数据除了 `fmt` 和 `os` 包，我们还需要用到 `bufio` 包来处理缓冲的输入和输出。

### 读取控制台的用户输入

我们如何读取用户的键盘（控制台）输入呢？从键盘和标准输入 `os.Stdin` 读取输入，最简单的办法是使用 `fmt `包提供的 Scan开头的函数。具体代码如下：

```go
package main

import "fmt"

func main() {
	nums:=0
	for {
		//读取一个字符，和类型相匹配
		n, _ := fmt.Scan(&nums)
		if n == 0 {
			break
		}
		//利用输入的nums，接着获取接下来的输入，形成数组
		A := make([]int, nums)
		for i := 0; i < nums; i++ {
			f, _ := fmt.Scan(&A[i])
			if f == 0 {
				break
			}
		}
		fmt.Println(A)
	}
}
//代码输出：
3
1 2 3
[1 2 3]

Process finished with exit code 0
```

### 读取输入--进阶

`bufio.NewReader() `构造函数的签名为：` func NewReader(rd io.Reader) *Reader`。

该函数的实参可以是满足 `io.Reader` 接口的任意对象，函数返回一个新的带缓冲的` io.Reader` 对象，它将从指定读取器（例如 `os.Stdin` ）读取内容。

返回的读取器对象提供一个方法 `ReadString(delim byte) `，该方法从输入中读取内容，直到碰到 `delim`指定的字符，然后将读取到的内容连同 `delim` 字符一起放到缓冲区。

`ReadString` 返回读取到的字符串，如果碰到错误则返回 nil 。如果它一直读到文件结束，则返回读取到的字符串和` io.EOF` 。如果读取过程中没有碰到 `delim` 字符，将返回错误 err != nil 。

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	//读取数据
	inputReader := bufio.NewReader(os.Stdin)
	fmt.Println("请在这输入：")
    //接收输入的字符串，遇到换行符，结束读取
	input, err := inputReader.ReadString('\n')
	if err != nil {
		fmt.Println("读取异常")
		os.Exit(1)
	}
	str := string(input)
	fmt.Printf("输入的值是：%s", str)
    //strings.Field(str string)：返回str空格分隔的所有子串的slice
	fmt.Println("输入的字符串子集是：", strings.Fields(str))
}
//代码输出：
请在这输入：
1 22   3333     444444
输入的值是：1 22   3333     444444
输入的字符串子集是： [1 22 3333 444444]
```

这里补充一个知识点：

### go语言中strings包常用方法

```go
strings.HasPrefix(s string, prefix string) bool：判断字符串s是否以prefix开头
strings.HasSuffix(s string, suffix string) bool：判断字符串s是否以suffix结尾。
//判断str在s中首次出现的位置，可以在字符串相关的算法中使用
strings.Index(s string, str string) int：判断str在s中首次出现的位置，如果没有出现，则返回-1
strings.LastIndex(s string, str string) int：判断str在s中最后出现的位置，如果没有出现，则返回-1

strings.Replace(str string, old string, new string, n int)：字符串替换

strings.Count(str string, substr string)int：字符串计数

strings.Repeat(str string, count int)string：重复count次str
//大小写
strings.ToLower(str string)string：转为小写
strings.ToUpper(str string)string：转为大写

strings.TrimSpace(str string)：去掉字符串首尾空白字符
strings.Trim(str string, cut string)：去掉字符串首尾cut字符
strings.TrimLeft(str string, cut string)：去掉字符串首cut字符
strings.TrimRight(str string, cut string)：去掉字符串首cut字符
//这两个个挺实用的，取代空格
strings.Field(str string)：返回str空格分隔的所有子串的slice
strings.Split(str string, split string)：返回str split分隔的所有子串的slice
//拼接字符串数组
strings.Join(s1 []string, sep string)：用sep把s1中的所有元素链接起来
```

字符串转换：

```go
//字符串转数字int型
n, _ := strconv.Atoi("123")
//int型转字符串
s := strconv.Itoa(123)
```

