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

#### 注释

---

单行注释以双正斜杠作为起始标记

```
// 这是一个注释
```

多行注释用单个正斜杠加一个星号开始，用一个星号加一个正斜杠作为结束

```
/* 这是一个
多行注释 */
```

Swift的多行注释可以嵌套在其他多行注释之中：

```
/* 这是第一个多行注释的开头
/* 这是第二个
嵌套的多行注释 */
这是第一个多行注释的结尾 */
```

#### 分号

---

Swift不强制需要在每行结尾加上分号，但是在一行内写多条独立语句时必须用分号隔开

```
let cat = "CAT"; println(cat)
```

#### 整数

---

整数是没有小数部分的数字，整数可以是有符号（正，负，零）或者无符号（正，零）

Swift 有6，16，32，64位的有符号和无符号整数类型

##### 整数范围

通过访问不同类型的 min 和 max 来获取最大和最小值

```
let minValue = UInt8.min  // 0
let maxValue = UInt8.max  // 255
```

##### Int

Int的长度与当前平台的原生长度相同

- 在32位平台，Int 与 Int32 长度相同
- 在64位平台，Int 与 Int64 长度相同

##### UInt

UInt的长度也与当前平台的原生字长相同，一般情况下尽量使用 Int

#### 浮点数

---

浮点数是有小数部分的数字，Swift提供两种浮点数类型

- Double 表示64位浮点数
- Float 表示32位浮点数

#### 类型安全和类型判断

---

Swift是一个 类型安全 的语言（type safe）

在声明常量或者变量的时候赋一个字面量即可触发类型判断

- 当推断浮点数类型时，Swift总会选择Double
- 如果同时出现了整数和浮点数，会被推断为Double类型

```
let meaningOfLife = 42 // meaningOfLife 会推测为 Int 类型
let pi = 3.14159  // pi 被推测为 Double 类型
let anotherPi = 3 + 0.14159  // anotherPi 被推测为 Double 类型
```

#### 数值型字面量

---

整数字面量可以写作：

- 十进制数，没有前缀
- 二进制数，前缀是 0b
- 八进制数，前缀是 0o
- 十六进制数，前缀是 0x

```
// 下面数字都表示十进制里面的 17
let decimalInteger = 17
let binartInteger = 0b10001
let octalInteger = 0o21
let hexadecimalInteger = 0x11
```

浮点字面量可以是十进制（无前缀）或十六进制（前缀是0x），小数点两边必须有至少一个十进制数字（或十六进制数）

浮点字面量有可选的指数（exponent），十进制浮点数中通过大写或小写的e指定，十六进制浮点数中通过大写或小写的p来指定

- 1.25e2 = 1.25*10^2 = 125
- 1.25e-2 = 1.25*10^-2 = 0.0125
- 0xFp2 = 15*2^2 = 60
- 0xFp-2 = 15*2^-2 = 3.75

```
// 下面数字都表示十进制的 12.1875
let decimalDouble = 12.1875
let exponentDouble = 1.21875e1
let hexadecimalDouble = 0xC.3p0
```

整数和浮点数可以添加额外的0和下划线，不影响字面量

```
let paddeddouble = 00123.456
let oneMillion = 1_000_000
let justOverOneMillion = 1_000_000.000_000_1
```

#### 数值型类型转换

---

##### 整数转换

数字超出了常量或变量可以存储的范围时候会报错

```
// 以下两种情况都会报错
let cannotBeNegative: UInt8 = -1
let tooBig: Int8 = Int8.max + 1
```

将一种数字类型转换成另一种，要用当前值初始化一个期望类型的新数字

```
let twoThousand: UInt16 = 2_000
let one: UInt8 = 1
let twoThousandAndOne = twoThousand + UInt16(one)
```

someType(ofInitialValue) 是调用 Swift 构造器并传入一个初始值的默认方法

- 传入的值不能是任意类型，只能传入内部有对应构造器的值
- 可以扩展现有的类型来让它接收其他类型的值

##### 整数和浮点数转换

整数和浮点数的转换必须显式指定类型

```
let three = 3
let pointOneFourFiveNine = 0.14159
let pi = Double(three) + pointOneFourOneFiveNine  // 加号两边的类型必须相同才可以相加
```

浮点数到整数反向转换时，浮点值会被截断

```
let integerPi = Int(pi)  // 3
```

#### 类型别名

---

类型别名指给现有的类型定义另一个名字，使用 typealias 关键字来定义类型别名

```
typealias AudioSample = UInt16
var maxAmplitudeFound = AudioSample.min  // 0
```

#### 布尔值

---

Swift有一个基本的布尔类型，Bool，有两个布尔常量，true 和 false

```
let orangesAreOrange = true
let turnipsAreDelicious = true
```

编写条件语句的时候，布尔值非常有用

```
if turnipsAreDelicious {
  println("Mmm, tasty turnips!")
} else {
  println("Eww, turnips are horrible.")
}
```

如果在需要Bool类型的地方使用了非布尔值，会报错

```
let i = 1
if i {
  // 这个部分不会通过编译，会报错
}
if i == 1 {
  // 这个部分会编译成功
}
```

#### 元组

---

元组把多个值组合成一个复合值

- 元组内的值可以是任意类型，不需要是相同的类型
- 作为函数返回值时，元组非常有用
- 但元组不适合创建复杂的数据结构，如果数据结构不是临时使用，应该用类或者结构体

```
// 一个描述404返回的元组
let http404Error = (404, "Not Found")
```

可以将元组的内容分解成单独的常量和变量

```
let (statusCode, statusMessage) = http404Error
println("The status code is \(statusCode)")  // 404
println("The status message is \(statusMessage)")  // Not Found
```

分解元组时候，可以用下划线代替需要忽略的部分

```
let (justTheStatusCode, _) = http404Error
println("The status code is \(justTheStatusCode)")
```

还可以通过下标来访问元组中的单个元素，下标从零开始

```
println("The status code is \(http404Error.0)")
println("The status message is \(http404Error.1)")
```

在定义元组的时候可以给单个元素命名，获取时候就可以通过名字来获取

```
let http200Status = (statusCode: 200, description: "OK")
println("The status code is \(http200Status.statusCode)")  // 200
println("The status message is \(http200Status.description)")  // OK
```

#### 可选类型

---

使用 可选类型 来处理值可能缺失的情况，可选类型表示：

- 有值，等于 X
- 没有值

```
/* 
  toInt 方法返回的值类型是一个可选类型
  可选的Int类型写作 Int?，问号表示是可选类型
  Int? 可以包含一个Int的值或者什么都没有
*/
let possibleNumber = "123"
let convertedNumber = possibleNumber.toInt()
```

##### if语句及强制解析

可选值的强制解析：当确定一个可选类型包含值之后，可以在它的名字后面加上一个感叹号来获取值

```
if convertedNumber != nil {
  println("\(possibleNumber) has an integer value of \(convertedNumber!)")
} else {
  println("\(possibleNumber) cound not be converted to an integer")
}
```

##### 可选绑定

使用可选绑定来判断可选类型是否包含值，如果包含就把值赋给一个临时常量或变量。经常用在if和while语句中

```
if let constantName = someOptional {
  statements
}
```

重写上面的例子

```
if let actualNumber = possibleNumber.toInt() {
  println("\(possibleNumber) has an integer value of \(actualNumber)")
} else {
  println("\(possibleNumber) cound not be converted to an integer")
}
```

##### nil

可以给一个可选变量赋值为 nil 表示它没有值

- 只能用于可选变量，不能用于非可选的变量和常量
- 声明一个可选变量或可选常量但是没有赋值，它的值自动会被设置成 nil

```
var serverResponseCode: Int? = 404
serverResponseCode = nil
var surveyAnswer: String?  // surveyAnswer 的值自动设置为 nil
```

##### 隐式解析可选类型

在程序框架中，可选类型第一次被赋值后，可以确定总会有值，这种类型的可选状态被定义为 隐式解析可选类型

声明的方式是把想要用作可选的类型的后面的问号改成感叹号

- 一个隐式解析可选类型是一个普通的可选类型，但是可以被当做非可选类型来使用
- 一个变量之后可能变成 nil 的话不要使用隐式解析可选类型

```
let assumedString: String! = "An implicitly unwrapped optional string."
ptintln(assumedString)  // 不需要感叹号
```

可以把隐式解析可选类型当做普通可选类型来判断是否包含值，也可以在可选绑定中使用

```
if assumedString {
  println(assumedString)
}
if let definiteString = assumedString {
  println(definiteString)
}
```

#### 断言

---

当值缺失或不满足条件使代码无法继续执行时，可以在代码中触发一个断言来结束代码运行并通过调试来找到值缺失的原因

##### 使用断言进行调试

断言会在运行时判断一个逻辑条件是否为 true

- 如果判断为 true，代码会继续运行
- 如果条件判断为 false，代码运行停止，应用中止

用全局 assert函数 写断言，当表达式是false时候，断言的信息会被显示

```
let age = -3
assert(age >= 0, "A person's age cannot be less than zero")
```

断言信息可以被省略

```
assert(age >= 0)
```

##### 何时使用断言

- 整数类型的下标索引被传入一个自定义下标脚本实现，但是下标索引值可能太小或者太大
- 需要给函数传入一个值，但是非法的值可能导致函数不能正常执行
- 一个可选值现在是nil，但是后面的代码运行需要一个非nil值

### 2.2 基本运算符

---

本节包含内容：

- 术语
- 赋值运算符
- 算术运算符
- 组合赋值运算符
- 比较运算符
- 三目运算符
- 空合运算符
- 区间运算符
- 逻辑运算符

#### 术语

---

运算符有一元，二元和三元运算符

- 一元运算符：对单一操作对象操作，分前置运算符（如 !b）和后置运算符(如 i++)
- 二元运算符：操作两个对象，是中置的（如 a+b）
- 三元运算符：只有一个，三目运算符 （a?b:c）

#### 赋值运算符

---

赋值运算，用b的值初始化更新a的值

```
let b = 10
var a = 5
a = b  // a = 10
```

赋值右边是多元组，它的元素可以马上被分解多个常量或变量

```
let (x,y) = (1,2)  // x=1, y=2
```

Swift的赋值操作不返回任何值：

```
if x=y {
  // 语句错误
}
```

#### 算术运算符

---

Swift中所有的数值类型都支持基本的四则运算

```
1 + 2
5 - 3
2 * 3
10 / 2
```

Swift默认情况下不允许数值运算中出现溢出的情况，但可以使用溢出运算符实现溢出运算（ a &+ b ）

加法运算符可以用作 string 的拼接

```
"hello, " + "world"  // 等于 "hello, world"
```

两个character值或一个string和一个character值，相加会产生一个新的string值

```
let dog: Charactor = "d"
let cow: Charactor = "c"
let dogCow = dog + cow
```

##### 求余运算符

求余运算（ a%b ）计算b的多少倍可以容入a，返回余数

```
9 % 4 // 等于 1
```

求余运算使用了以下等式

```
a = (b * 倍数) + 余数
// 所以负数的操作如下
-9 % 4 // 结果是 -1
```

对负数b求余时，b的符号会被忽略，所以 `a % b` 和 ` a % -b `结果是一样的

##### 浮点数求余计算

Swift可以对浮点数进行求余计算

```
8 % 2.5 // 等于 0.5
```

##### 自增和自减运算

Swift提供了对变量自身加1或减1的自增（++）和自减（--）缩略算符

```
var i = 0
++i  // 现在 i = 1
```

++ 和 -- 既可以做前置运算，也可以做后置运算

- 当 ++ 前置的时候，先自增再返回
- 当 ++ 后置的时候，先返回再自增

```
var a = 0
let b = ++a // a=1, b=1
let c = a++  //a=2, c=1
```

一般情况下尽量使用前置运算，即先自增/自减，再返回

##### 一元符号运算符

数值的正负可以用前缀 - （一元符号）来切换

```
let three = 3
let minusThree = -three  // minusThree = -3
let plusThree = -minusThree  // plusThree = 3
```

一元负号写在操作数之前，中间没有空格

##### 一元正号运算符

一元正号运算符不做任何改变的返回操作数的值

```
let minusSix = -6
let alsoMinusSix = +minusSix  // alsoMinusSix = -6
```

#### 复合赋值

---

```
var a = 1
a += 2  // a=3
```

`a += 2` 是 `a = a + 2` 的缩写

符合运算符没有返回值，所以 `let b = a += 2` 这种写法是错误的

#### 比较运算符

---

所有C语言的比较运算符都可以在Swift中使用：

- 等于 （ a == b ）
- 不等于 （ a != b）
- 大于 （ a > b ）
- 小于 （ a < b ）
- 大于等于 （ a >= b ）
- 小于等于 （ a <= b ）

Swift提供恒等（===）和不恒等（!==）比较符来判断两个对象是否引用同一个对象实例

每个比较运算符都返回布尔值

```
1 == 1  // true
2 != 1  // true
2 > 1  // true
1 < 2  // true
1 >= 1  // true
2 <= 1  // false
```

比较运算符一般用于条件语句

```
let name = "world"
if name == "world" {
  println("hello, world")
} else {
  println("sorry")
}
```

#### 三目运算符

---

三目运算符的原型是 `问题 ? 答案1 : 答案2`，如果问题成立，返回答案1的结果，如果不成立，返回答案2的结果，它是以下代码的缩写

```
if question: {
  answer1
} else {
  answer2
}
```

三目运算符高效的表达二选一的选择，但会使代码难懂，要避免在组合语句中使用

```
// 计算表格行高，如果有表头，则高度要比内容多50个像素，没有的话，只多20个
let contentHeight = 40
let hasHeader = true
let rowHeight = contentHeight + (hasHeader ? 50 : 20)
// rowHeight=90
// 如果不使用三目运算符，代买如下
let contentHeight = 40
let hasHeader = true
var rowHeight = contentHeight
if hasHeader {
  rowHeight = rowHeight + 50
} else {
  rowHeight = rowHeight + 20
}
```

#### 空合运算符

---

空合运算符（ a ?? b ）对可选类型a进行判断，如果a包含一个值就强制解封，如果不包含（a = nil）就返回一个默认值b

- 表达式a必须是 Optional 类型
- 默认值b的类型必须要和a的存储值的类型保持一致

空合运算符是以下代码的简短表达：

```
a != nil ? a! : b
```

如果a为非空值，那么b不会被估值，这就是所谓的短路求值

下面的例子实现了在默认颜色和可选自定义颜色之间的选择

```
let defaultColorName = "red"
var userDefinedColorName:String?  // 默认值是nil
var colorNameToUse = userDefinedColorName ?? defaultColorName  // 现在 colorNameToUse 的值是 red
userDefinedColorName = "green"
var colorNameToUse = userDefinedColorName ?? defaultColorName  // 现在 colorNameToUse 的值是 green

```

