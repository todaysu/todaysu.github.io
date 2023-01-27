---
layout: post
title:  "kubernets go 学习 01"
date:   2022-11-15
categories: kubernets
---

# 1. 微服务开发建议

统一思想-12 factors

​	**I. 基准代码：**一份基准代码，多份部署

​	**II. 依赖：**显式声明依赖关系

​	**III. 配置：**在环境中存储配置

​	**IV. 后端服务：**把后端服务当作附加资源

​	**V. 构建，发布，运行：**严格分离构建和运行

​	**VI. 进程：**以一个或多个无状态进程运行应用

​	**VII. 端口绑定：**通过端口绑定提供服务

​	**VIII. 并发：**通过进程模型进行扩展

​	**IX. 易处理：**快速启动和优雅终止可最大化健壮性

​	**X. 开发环境与线上环境等价：**尽可能的保持开发，预发布，线上环境相同

​	**XI. 日志：**把日志当作事件流

​	**XII. 管理进程：**后台管理任务当作一次性进程运行

# 2. 为什么需要另外一种语言？

## 2.1 其他编程语言的弊端。 

​	• 硬件发展速度远远超过软件。 

​	• C 语言等原生语言缺乏好的依赖管理 (依赖头文件）。

​	• Java 和 C++ 等语言过于笨重。

​	• 系统语言对垃圾回收和并行计算等基础功能缺乏支持。

​	• 对多核计算机缺乏支持。

## 2.2 Go 语言是一个可以编译高效，支持高并发的，面向垃圾回收的全新语言。

​	• 秒级完成大型程序的单节点编译。

​	• 依赖管理清晰。

​	• 不支持继承，程序员无需花费精力定义不同类型之间的关系。

​	• 支持垃圾回收，支持并发执行，支持多线程通讯。

​	• 对多核计算机支持友好。

## 2.3 **Go 语言不支持的特性**

​	• 不支持函数重载和操作符重载

​	• 为了避免在 C/C++ 开发中的一些 Bug 和混乱，不支持隐式转换

​	• 支持接口抽象，不支持继承

​	• 不支持动态加载代码

​	• 不支持动态链接库

​	• 通过 recover 和 panic 来替代异常机制

​	• 不支持断言

​	• 不支持静态变量

# 2.4 **一些基本命令**

**bug**   start a bug report

**build** compile packages and dependencies

• Go 语言不支持动态链接，因此编译时会将所有依赖编译进同一个二进制文件。

• 指定输出目录。 

• go build –o bin/mybinary . 

• 常用环境变量设置编译操作系统和 CPU 架构。 

​			• GOOS=linux GOARCH=amd64 go build

• 全支持列表。 

​			• $GOROOT/src/go/build/syslist.go

```go
cat main.go
package main

import (
        "fmt"
)

func main() {
        myArray := [5]string{"I", "am", "stupid", "and", "weak"}
        myArray[2] = "smart"
        myArray[4] = "strong"
        for _, char := range myArray {
                fmt.Println(char)

        }

}
go build main.go #编译
root#./main
I
am
smart
and
strong
```

**clean**  remove object files and cached files

**doc**  show documentation for package or symbol

**env**  print Go environment information

**fix**  update packages to use new APIs

**fmt** gofmt (reformat) package sources，格式化代码

```go
cat main.go
package main

import (
        "fmt"
)

func main() {
  myArray := [5]string{"I", "am", "stupid", "and", "weak"}
   myArray[2] = "smart"
        myArray[4] = "strong"
        for _, char := range myArray {
                fmt.Println(char)

        }

}

go fmt main.go
cat main.go
package main

import (
        "fmt"
)

func main() {
        myArray := [5]string{"I", "am", "stupid", "and", "weak"}
        myArray[2] = "smart"
        myArray[4] = "strong"
        for _, char := range myArray {
                fmt.Println(char)

        }

}
```

**generate** generate Go files by processing source

**get**  add dependencies to current module and install them

**install**  compile and install packages and dependencies

**list** list packages or modules

**mod**  module maintenance go 的依赖管理工具

**run** compile and run Go program

**test**  test packages

Go 语言原生自带测试

```
import "testing"

func TestIncrease(t *testing.T) {

t.Log("Start testing")

increase(1, 2) 

}
```

go test ./… -v 运行测试

go test命令扫描所有*_test.go为结尾的文件，惯例是将测试代码与正式代码放在同目录，

如 foo.go 的测试代码一般写在 foo_test.go

**tool** run specified go tool

**version** print Go version

**vet** report likely mistakes in packages,代码静态检查，发现可能的 bug 或者可疑的构造

## 2.5 go语法

控制结构

```go
#If
• 基本形式
if condition1 {
// do something 
} else if condition2 {
// do something else 
} else {
// catch-all or default
} • if 的简短语句
• 同 for 一样， if 语句可以在条件表达式前执行一个简单的语句。
if v := x - 100; v < 0{
return v }

#switch
switch var1 {
	case val1: //空分支
	case val2:
		fallthrough //执行case3中的f()
	case val3:
		f()
	default: //默认分支
		...
}

#For
Go 只有一种循环结构：for 循环。
# 计入计数器的循环
for 初始化语句; 条件语句; 修饰语句 {}
for i := 0; i < 10; i++ {
sum += i }
# 初始化语句和后置语句是可选的，此场景与 while 等价（Go 语言不支持 while）
for ; sum < 1000; {
sum += sum
} 
# 无限循环
for {
	if condition1 {
	break
} }

#for-range
遍历数组，切片，字符串，Map 等
for index, char := range myString {
...
}
for key, value := range MyMap {
...
}
for index, value := range MyArray {
...
}
需要注意：如果 for range 遍历指针数组，则 value 取出的指针地址为原指针地址的拷贝
```

Example

```go
cat main
package main ##

import (
        "flag"
        "fmt"
        "os"
)

func main() {
        //当运行时加上--name的参数，就会由flag捕捉到。如果没有就就以world为默认值,第三个参数就是提示
        name := flag.String("name", "world", "specify the name you want to say hi") 
        flag.Parse()
        fmt.Println("os args is:", os.Args)
        fmt.Println("input parameter is:", *name)
        fullString := fmt.Sprintf("Hello %s from Go\n", *name)
        fmt.Println(fullString)
}
```

运行：

```
./main
os args is: [./main]
input parameter is: world
Hello world from Go

--name jack
os args is: [./main --name jack]
input parameter is: jack
Hello jack from Go
```

## 2.6 **变量与常量**

常量：const identifier type,不能后期修改的

变量：var identifier type

​			• var 语句用于声明一个变量列表，跟函数的参数列表一样，类型在最后。

```go
var c, python, java bool
```

​	• **变量的初始化**

​			• 变量声明可以包含初始值，每个变量对应一个。

​			• 如果初始化值已存在，则可以省略类型；变量会从初始值中获得类型。

```go
var i, j int = 1, 2
```

• **短变量声明**

​			• 在函数中，简洁赋值语句 := 可在类型明确的地方代替 var 声明。

​			• 函数外的每个语句都必须以关键字开始（var, func 等等），因此 := 结构不能在函数外使用。

```go
c, python, java := true, false, "no!"
```

## 2.7 **类型转换与推导**

• **类型转换**

显示转换

​	• 表达式 T(v) 将值 v 转换为类型 T。 

​		一些关于数值的转换：

```go
var i int = 42 
var f float64 = float64(i) 
var u uint = uint(f)
```

​		或者，更加简单的形式：

```go
i := 42 
f := float64(i) 
u := uint(f)
```

• **类型推导**

​	•在声明一个变量而不指定其类型时（即使用不带类型的 := 语法或 var = 表达式语法），变量的类型由右值推导得出。

```go
var i int 
j := i  //j 也是一个 int
```

## 2.8**数组**

• 相同类型且长度固定连续内存片段

• 以编号访问每个元素

• 定义方法

```
var identifier [len]type
```

• 示例

```
myArray := [3]int{1,2,3}
```

## 2.9 **切片(slice)**

• 切片是对数组一个连续片段的引用

• 数组定义中不指定长度即为切片

• var identifier []type

• 切片在未初始化之前默认为nil， 长度为0 

• 常用方法

```go
func main() {
	myArray := [5]int{1, 2, 3, 4, 5}
	mySlice := myArray[1:3]
	fmt.Printf("mySlice %+v\n", mySlice)
	fullSlice := myArray[:]
	remove3rdItem := deleteItem(fullSlice, 2)
	fmt.Printf("remove3rdItem %+v\n", remove3rdItem)
}
//切片的值没有办法直接删除，只能通过拼接的方式来删除
func deleteItem(slice []int, index int) []int {
	return append(slice[:index], slice[index+1:]...)
}
```

切片是连续内存并且可以动态扩展，由此引发的问题？

```go
a := []int{}
b := []int{1,2,3}
c := a
a = append(b, 1) //假如当前内存地址块b放不到一个数字1，那append后地址的内存地址就行有变，导致a不等于b了

//修改切片的值？
mySlice := []int{10, 20, 30, 40, 50}
for _, value := range mySlice {
	value *= 2 
}
fmt.Printf("mySlice %+v\n", mySlice)
for index, _ := range mySlice {
	mySlice[index] *= 2 
}
fmt.Printf("mySlice %+v\n", mySlice)
```

## 2.10 **Map**

一种key和value的组合

```
声明方法
• var map1 map[keytype]valuetype
• 示例
myMap := make(map[string]string, 10)
myMap["a"] = "b"
myFuncMap := map[string]func() int{ "funcA": func() int { return 1 },}
fmt.Println(myFuncMap) f := myFuncMap["funcA"]
fmt.Println(f())
```

访问map

```go
value, exists := myMap["a"]
if exists {
	//如果值存在才打印，避免空值。
	println(value)
}
//遍历 Map
for k, v := range myMap {
	println(k, v)
}
```

## 2.11 **结构体和指针**

通过 type … struct 关键字自定义结构体,结构体中的字段除了有名字和类型外，还可以有一个可选的标签（tag） 

```go
//使用场景：Kubernetes APIServer对所有资源的定义都用 Json tag 和protoBuff tag,可以通过tag去反射到具体的属性值
NodeName string  `json:"nodeName,omitempty" protobuf:"bytes,10,opt,name=node Name"`
```

• Go 语言支持指针，但不支持指针运算

​	• 指针变量的值为内存地址

​	• 未赋值的指针为 nil

```go
type MyType struct {
	Name string //定义属性
}
func printMyType(t *MyType){
	println(t.Name) }
	func main(){
	t := MyType{Name: "test"}
	printMyType(&t)
}
```

# 2.12 类型重命名

```go
// Service Type string describes ingress methods for a service
type ServiceType string
const (
// ServiceTypeClusterIP means a service will only be accessible inside the
// cluster, via the ClusterIP.
ServiceTypeClusterIP ServiceType = "ClusterIP"
// ServiceTypeNodePort means a service will be exposed on one port of
// every node, in addition to 'ClusterIP' type.
ServiceTypeNodePort ServiceType = "NodePort"
// ServiceTypeLoadBalancer means a service will be exposed via an
// external load balancer (if the cloud provider supports it), in addition
// to 'NodePort' type.
ServiceTypeLoadBalancer ServiceType = "LoadBalancer"
// ServiceTypeExternalName means a service consists of only a reference to
// an external name that kubedns or equivalent will return as a CNAME
// record, with no exposing or proxying of any pods involved.
ServiceTypeExternalName ServiceType = "ExternalName" )
```

