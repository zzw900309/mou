# The Swift Programming Language 中文版（2）

全书gitbook地址：[全书地址](http://numbbbbb.gitbooks.io/-the-swift-programming-language-/content/)

GitHub开源项目地址：[项目地址](https://github.com/numbbbbb/the-swift-programming-language-in-chinese)

## 2. Swift教程

本章介绍 Swift 的各种特性和方法，是核心部分

---

### 2.1 基础部分

---

本节内容包括：

- 常量和变量
- 注释
- 分号
- 整数
- 浮点数
- 类型安全和类型推断
- 数值型字面量
- 数值型类型转换
- 类型别名
- 布尔值
- 元组
- 可选
- 断言

#### 常量和变量

---

常量和变量把 一个名字 和 一个指定类型的值 关联起来

常量的值一旦设定就不能改变，变量的值可以随意更改

##### 声明常量和变量

用 let 声明常量，用 var 声明变量

```
let maximumNumberOfLoginAttempts = 10
var currentLoginAttempt = 0
```

可以在一行中声明多个常量或变量，用逗号隔开

```
var x = 0.0, y = 0.0, z = 0.0
```

##### 类型标注

声明常量和变量的时候可以加上类型标注，说明要存储的值的类型

一般很少需要写类型标注，常量和变量赋初始值的时候Swift会推断出类型

```
var welcomeMessage: String
```

##### 常量和变量的命名

可以使用任何字符，包括 Unicode 字符

- 不能包含数学符号，箭头，保留的（或非法的）Unicode码位
- 不能以数字开头，但是其他地方可以包含数字
- 不能用Swift保留关键字作为常量名或变量名；如果一定要用，需要用反引号( ` )将关键字包围起来使用，不推荐

常量和变量声明为确定的类型后，不能使用相同的名字再次声明，也不能改变其存储的值得类型

可以更改变量值为其他同类型的值，常量的值一旦确定就不能更改

```
var friendlyWelcome = "Hello!"
friendlyWelcome = "Bonjour!"
```

##### 输出常量和变量

可以用 println 来输出常量和变量的值

- println 会将内容输出到 console
- print 和 println 的区别是前者输出后不换行
- 和Cocoa李的 NSLog 类似，println可以输出包括变量和常量的值在内的复杂信息

```
println(friendlyWelcome)
println("This is a String")
```

Swift用 字符串插值 的方式把常量名或变量名当做占位符加入到长字符串中。将常量名或变量名放入圆括号中，并在前面加上反斜杠来转义

```
println("The current value of friendlyWelcome is \(friendlyWelcome)")
```

