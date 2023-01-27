---
layout: post
title:  "kubernets go 学习 02"
date:   2022-11-15
categories: kubernets
---

# 1. **Main 函数**

• 每个 Go 语言程序都应该有个 main package，入口函数。

• Main package 里的 main 函数是 Go 语言程序入口

```
package main
func main() {
	args := os.Args
	if len(args) != 0 {
	println("Do not accept any argument")
	os.Exit(1) }
	println("Hello world") 
}
```

Go 语言如何传入参数呢？

• 方法1： 

```
fmt.Println("os args is:", os.Args) 
```

• 方法2： 

```
name := flag.String("name", "world", "specify the name you want to say hi")
flag.Parse()
```

# 2.**Init 函数**

• Init 函数：会在包初始化时运行，会执行在main函数前面

• 谨慎使用 init 函数

• 当多个依赖项目引用统一项目，且被引用项目的初始化在 init 中完成，并且不可重复运行时，会导

致启动错误.

![image-20221117111445924](/Users/suyingjie/Documents/blog/todaysu.github.io/assets/img/2022-11-17/1.png)

例如：

定义一个main，首先会导入a包

```go
package main

import (
	"fmt"

	_ "github.com/cncamp/golang/examples/module1/init/a"
	_ "github.com/cncamp/golang/examples/module1/init/b" #此处位置的b不会再打印，因为init方法只执行一次
)

func init() {
	fmt.Println("main init")
}
func main() {

}
```

a又需要导入b

```
package a

import (
	"fmt"

	_ "github.com/cncamp/golang/examples/module1/init/b"
)

func init() {
	fmt.Println("init from a")
}
```

b

```
package b

import (
	"fmt"
)

func init() {
	fmt.Println("init from b")
}
```

通过上面的代码分析，会先打印b，再打印a,然后再执行main。并且init方法只执行一次

```go
//输出
init from b
init from a
main init
```

# 3.**返回值**

• 多值返回

​	• 函数可以返回任意数量的返回值，可以有多返回值

• 命名返回值

​	• Go 的返回值可被命名，它们会被视作定义在函数顶部的变量。

​	• 返回值的名称应当具有一定的意义，它可以作为文档使用。

​	• 没有参数的 return 语句返回已命名的返回值。也就是直接返回。

• 调用者忽略部分返回值

​	result, _ = strconv.Atoi(origStr)

# 4.**传递变长参数**

Go 语言中的可变长参数允许调用方传递任意多个相同类型的参数

• 函数定义

```
func append(slice []Type, elems ...Type) []Type //可以允许N个函数
```

• 调用方法

```
myArray := []string{}

myArray = append(myArray, "a","b","c")
```

# 5.**回调函数(Callback)**

函数作为参数传入其它函数，并在其他函数内部调用执行

• strings.IndexFunc(line, unicode.IsSpace) 

• Kubernetes controller的leaderelection

```
示例：
func main() {
	DoOperation(1, increase)
	DoOperation(1, decrease)
}
func increase(a, b int) {
	println(“increase result is:”, a+b) }
	func DoOperation(y int, f func(int, int)) {
	f(y, 1) 
}
func decrease(a, b int) {
	println("decrease result is:", a-b)
}
```

# 6.**闭包**

• 匿名函数

​	• 不能独立存在

​	• 可以赋值给其他变量

​		x:= func(){}

• 可以直接调用

​		func(x,y int){println(x+y)}(1,2)

• 可作为函数返回值

​		func Add() (func(b int) int)

# 7.**方法**

• 方法：作用在接收者上的函数

• func (recv receiver_type) methodName(parameter_list) (return_value_list) 

• 使用场景

• 很多场景下，函数需要的上下文可以保存在receiver属性中，通过定义 receiver 的方法，该方法可

以直接访问 receiver 属性，减少参数传递需求

```go
// StartTLS starts TLS on a server from NewUnstartedServer.
func (s *Server) StartTLS() {
	if s.URL != “” {
	panic(“Server already started”) 
}

	if s.client == nil {
	s.client = &http.Client{Transport: &http.Transport{}
	}
}
```

# 8.**传值还是传指针**

• Go 语言只有一种规则-传值

• 函数内修改参数的值不会影响函数外原始变量的值

• 可以传递指针参数将变量地址传递给调用函数，Go 语言会

复制该指针作为函数内的地址，但指向同一地址

• 思考：当我们写代码的时候，函数的参数传递应该用 struct

还是 pointer？

```go
package main

import (
	"fmt"
)

func main() {
	str := "a string value" //定义一个变量
	pointer := &str //取变量指针,就是内存地址
	anotherString := *&str //取变量内存地址上所对应的值
	fmt.Println(str)
	fmt.Println(pointer)
	fmt.Println(anotherString)
	str = "changed string"
	fmt.Println(str)
	fmt.Println(pointer)
	fmt.Println(anotherString)
	para := ParameterStruct{Name: "aaa"}
	fmt.Println(para)
	changeParameter(&para, "bbb")
	fmt.Println(para)
	cannotChangeParameter(para, "ccc")
	fmt.Println(para)
}

type ParameterStruct struct {
	Name string
}

func changeParameter(para *ParameterStruct, value string) {
	para.Name = value
}

func cannotChangeParameter(para ParameterStruct, value string) {
	para.Name = value
}

```

# 9.**接口**

• 接口定义一组方法集合

```
type IF interface {

	Method1(param_list) return_type

} 
```

• 适用场景：Kubernetes 中有大量的接口抽象和多种实现

• Struct 无需显示声明实现 interface，只需直接实现方法

• Struct 除实现 interface 定义的接口外，还可以有额外的方法

• 一个类型可实现多个接口（Go 语言的多重继承）

• Go 语言中接口不接受属性定义

• 接口可以嵌套其他接口
