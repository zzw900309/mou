# The Swift Programming Language 中文版（1）

全书gitbook地址：[全书地址](http://numbbbbb.gitbooks.io/-the-swift-programming-language-/content/)

GitHub开源项目地址：[项目地址](https://github.com/numbbbbb/the-swift-programming-language-in-chinese)

## 1. 欢迎使用 Swift

---

### 1.1 关于 Swift

Swift 基于 Cocoa 和 Cocoa Touch 框架

Swift 使用 Objective-C 的命名参数和动态对象模型，可以对接现有的 Cocoa 框架，兼容 Objective-C 代码

Swift 支持代码预览

---

### 1.2 Swift 初见

本节内容包括：

- 简单值（Simple Values）
- 控制流（Control Flow）
- 函数和闭包（Functions and Closures）
- 对象和类（Objects and Classes）
- 枚举和扩展体（Enumerations and Structures）
- 协议和扩展（Protocols and Extensions）
- 泛型（Generics）

打印“Hello World”：`println("Hello World")`

Swift中，全局作用域中的代码会自动当做程序的入口点，不需要main函数

每个语句的结尾不需要分号

**Xcode中，可以通过打开 Playground 功能来实时预览代码**

#### 简单值

---

使用let声明常量，var声明变量

常量和变量的类型可以根据赋值自动推断，也可以在变量后面声明类型

```
var myVariable = 42
myVariable = 50
let my Constant = 42
let explicitDouble: Double = 70
```

值永远不会被转化成其他类型，如果需要转换，必须用显示转换

```
let label = "The Width is"
let width = 94
let widthLabel = label + String(label)
```

用`\( )`可以快速把数值转换成字符串，支持计算

```
let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let fruitSummary = "I have \(apples + oranges) pieces of fruit."
```

使用`[ ]`来创建数组或字典，使用下标或者键（key）来访问

```
var shoppingList = ["catfish", "water", "tulips", "blue paint"]
shoppingList[1] = "bottle of water"  //修改数组的值

var occupations = [
  "Malcolm": "Captain",
  "Kaylee": "Mechanic",
]
occupations["Jayne"] = "Public Relations"  //字典中添加键值对
```

创建空的数组或键值对，当类型可以推断时，创建时可以省略

```
let emptyArray = [String]()
let emptyDictionary = [String: float]()

shoppingList = []
occupations = [ : ]
```

#### 控制流

---

if 和 switch 进行条件操作，for-in，for，while 和 do-while 来进行循环

包裹条件和循环变量的括号可以省略

```
let individualScores = [75, 43, 103 ,87, 12]
var teamScore = 0
for score in individualScores {
  if score > 50 {
    teamScore += 3
  } else {
    teamScore += 1
  }
}
teamScore
```

if 语句中，条件必须是一个布尔表达式

- 有的变量的值是可选的，没有值的时候是 nil
- 在类型后面加一个问号标记这个变量的值可选
- 变量的值是 nil，if 会返回判断为 false

```
var optionalString: String? = "Hello"
optionalString == nil

var optionalName: String? = "Jhon Appleseed"
var greeting = "Hello!"
if let name = optionalName {
  greeting = "Hello, \(name)"
}
```

switch 支持任意类型的数据和各种比较操作

- 每一个匹配最后不用加 break

```
let vegetable = "red pepper"
switch vegetable {
case "celery":
  let vegetableComment = "Add some raisins and make ants on a dog."
case "cucumber", "watercress":
  let vegetableComment = "That would make a good tea sandwish."
case let x where x.hasSuffix("pepper"):
  let vegetableComment = "Is it a spicy \(x)?"
default:
  let vegetableComment = "Everything tastes good in soup."
```

使用 for-in 遍历字典，需要两个变量表示键值对，注意字典是一个无序的集合

```
let interestingNumbers = [
  "Prime": [2,3,5,7,11,13],
  "Fibonacci": [1,1,2,3,5,8],
  "Square": [1,4,9,16,25],
]
var largest = 0
for (kind, numbers) in interestingNumbers {
  for number in numbers {
    if number > largest {
      largest = number
    }
  }
}
largest
```

while 循环代码直到不满足条件，循环条件可以在开头或者结尾

```
var n = 2
while n < 100 {
  n = n * 2
}n

var m = 2
do {
  m = m * 2
} while m < 100
m
```

for 循环中，循环可以用 ..< 表示范围，不包括上限，如果用 ... 表示范围，包括上限

```
var firstForLoop = 0
for i in 0..<4 {  // 等同于 for var i = 0; i < 4; ++i {
  firstForLoop += i
}
firstForLoop
```

#### 函数和闭包

---

使用 func 声明一个函数，使用名字和参数调用函数，用 -> 指定函数返回值

```
func greet(name: String, day: String) -> String {
  return "Hello \(name), today is \(day)."
}
greet("Bob", "Tuesday")
```

使用元组让函数返回多个值，元组的元素用名称或数字表示

```
func calculateStatistics(scores: [Int]) -> (min: Int, max: Int, sum: Int) {
  var min = scores[0]
  var max = scores[0]
  var sum = 0
  for score in scores {
    if score > max {
      max = score
    } else if score < min {
      min = score
    }
    sum += score
  }
  return (min, max, sum)
}
let statistics = calculateStatistics([5,3,100,3,9])
statistics.sum
statistics.2
```

函数可以有可变个数的参数，这些参数在函数内以数组形式表现

```
func sumOf(numbers: Int...) -> Int {
  var sum = 0
  for number in numbers {
    sum += number
  }
  return sum
}
sumOf(42,597,12)
```

函数可以嵌套，被嵌套的函数可以访问外侧函数的变量

```
func returnFifteen() -> Int {
  var y = 10
  func add() {
    y += 5
  }
  add()
  return y
}
returnFifteen()
```

函数是第一等类型，所以能将一个函数作为另一个函数的返回值

```
func makeIncrementer() -> (Int -> Int) {
  func addOne(number: Int) -> Int {
    return number + 1
  }
  return addOne
}
var increment = makeIncrementer()
increment(7)
```

函数可以当做参数传入另一个函数

```
func hasAnyMatches(list: [Int], condition: Int -> Bool) -> Bool {
  for item in list {
    if condition(item) {
      return true
    }
  }
  return false
}
func lessThanTen(number: Int) -> Bool {
  return number < 10
}
var numbers = [20,19,7,12]
hasAnyMatches(numbers, lessThanTen)
```

函数是一种特殊的闭包，可以使用 { } 来创建匿名闭包

- 使用 in 将参数，返回值类型声明和闭包函数体进行分离
- 闭包的类型已知时候，可以忽略参数，返回值类型和返回值
- 可以通过参数位置来引用参数，当闭包作为最后一个参数传给函数时候，可以直接跟在括号后面

```
numbers.map({
  (numbers: Int) -> Int in
  let result = * number
  return result
})

let mappedNumbers = number.map({ number in 3 * number })
mappedNumbers

let sortedNumbers = sorted(numbers) { $0 > $1 }
sortedNumbers
```

#### 对象和类

---

使用 class 和类名来创建一个类，类中属性的声明和常量，变量声明一样，方法和函数声明也一样

```
class Shape {
  var numberOfSides = 0
  func simpleDescription() -> String {
    return "A shape with \(numberOfSides) sides."
  }
}
```

创建类的实例时，在类名后加上括号，使用点语法访问实例的属性和方法

```
var shape = Shape()
shape.numberOfSides = 7
var shapeDescription = shape.simpleDescription()
```

类需要一个构造函数来初始化实例，使用 init 创建构造器

- self 用来区别实例变量
- 每一个属性都需要赋值，无论是通过声明还是通过构造器
- 在删除对象之前需要进行清理工作时，使用 deinit 创建一个析构函数

```
class NamedShape {
  var numberOfSides: Int = 0
  var name: String
  
  init(name: String) {
    self.name = name
  }
  
  func simpleDescription() -> String {
    return "A shape with \(numberOfSides) sides."
  }
}
```

子类的定义方法：在类名后面加上父类的名字，用冒号分割

- 子类重写父类方法时候，用 override 标记（标记的方法必须在父类中存在）
- 创建类时候不需要标准根类，所以可以忽略父类

```
class Square: NamedShape {
  var sideLength: Double
  
  init(sideLength: Double, name: String) {
    self.sideLength = sideLength
    super.init(name: name)
    numberOfSides = 4
  }
  
  func area() -> Double {
    return sideLength * sideLength
  }
  
  override func simpleDescription() -> String {
    return "A square with sides of length \(sideLength)."
  }
}
let test = Square(sideLength: 5.2, name: "my test square")
test.area()
test.simpleDescription()
```

类的属性可以有 getter 和 setter

- setter 中，新值的名称是 newValue，可以在 set 之后显式的设置一个名字
- 子类构造器执行的三个步骤
  - 设置子类声明的属性值 
  - 调用父类的构造器
  - 改变父类定义的属性值
  - 其它工作，如调用方法，getters和setters也可以在这个阶段完成

```
class EquilateralTriangle: NamedShape {
  var sideLength = 0.0
  
  init(sideLength: Double, name: String) {
    self.sideLength = sideLength
    super.init(name: name)
    numberOfSides = 3
  }
  
  var preimeter: Double {
  get {
    return 3.0 * sideLength
  }
  set {
    sideLength = newValue / 3.0
  }
  }
  
  override func simpleDescription() -> String {
    return "An equilateral triangle with sides of length \(sideLength)."
  }
}
var triangle = EquilateralTriangle(sideLength: 3.1, name: "a triangle")
triangle.perimeter
triangle.perimeter = 9.9
triangle.sideLength
```

使用 willSet 和 didSet 可以在不计算属性时，在设置一个新值之前或之后运行代码

```
// 下面的代码将三角形和正方形的边长设置成相同
class TriangleAndSquare {
  var triangle: EauilateralTriangle {
  willSet {
    square.sideLength = newValue.sideLength
  }
  }
  
  var square: Square {
  willSet {
    triangle.sideLength = newValue.sideLength
  }
  }
  
  init(size: Double, name: String) {
    square = Square(sideLength: size, name: name)
    triangle = EquilateralTriangle(sideLength: size, name: name)
  }
}
var triangleAndSquare = TriangleAndSquare(size: 10, name: "another test shape")
triangleAndSquare.square.sideLength
triangleAndSquare.triangle.sideLength
triangleAndSquare.square = Square(sideLength: 50, name: "larger square")
triangleAndSquare.triangle.sideLength
```

类中的方法的参数名需要在调用的时候显式说明（除了第一个）

- 默认方法的参数名和它在方法内部的名字一样，也可以自定义第二个，用在方法内部

```
class Counter {
  var count: Int = 0
  func incrementBy(amount: Int, numberOfTimes times: Int) {
    count += amount * times
  }
}
var counter = Counter()
counter.incrementBy(2, numberOfTimes: 7)
```

处理可选变量时候，可以在操作（方法，属性，脚本）之前加 ?

- ? 之前的值是 nil，后面的内容会忽略，整个表达式返回 nil
- ? 之前的值不是nil，后面的内容会执行，
- 这种情况下，整个表达式也是一个可选值

```
let optionalSquare: Square? = Square(sideLength: 2.5, name: "optional square")
let sideLength = optionalSquare?.sideLength
```

#### 枚举和结构体

---

使用 enum 创建一个枚举，枚举的每一个元素需要通过 case 来声明

- 枚举中可以包含方法
- 枚举的类型可以是 Int，浮点数或字符串
- Int 类型枚举只需要设置第一个原始值
- 枚举中的 switch 可以不加 default

```
enum Rank: Int {
  case Ace = 1
  case Two, Three, Four, Five, Six, Seven, Eight, Nine, Ten
  case Jack, Queen, King
  func simpleDescription() -> String {
    switch self {
    case .Ace:
      return "ace"
    case .Jack:
      return "jack"
    case .Queen:
      return "queen"
    case .King:
      return "king"
    default:
      return String(self.rawValue)
    }
  }
}
let ace = Rank.Ace
let aceRawValue = ace.rawValue
```

使用 rawValue 在原始值和枚举值之间进行转换

```
if let convertedRank = Rank(rawValue: 3) {
  let threeDescription = convertedRank.simpleDescription()
}
```

枚举成员的值是实际值，有两种方法引用枚举中的成员

- 下面给 hearts 赋值是，枚举成员 Suit.Hearts 需要用全名来引用，因为常量没有显式指定类型
- 在 switch 中，枚举成员可以缩写，因为 self 的值已经知道是一个 suit

```
enum Suit {
  case Spades, Hearts, Diamonds, Clubs
  func simpleDescription() -> {
    switch self {
    case .Spades:
      return "spades"
    case .Hearts:
      return "hearts"
    case .Diamonds:
      return "diamonds"
    case .Clubs:
      return "clubs"
    }
  }
}
let hearts = Suit.Hearts
let heartsDescription = hearts.simpleDescription()
```

使用 struct 创建一个结构体，结构体和类的区别：结构体传值，类是传引用

```
struct Card {
  var rank: Rank
  var suit: Suit
  func simpleDescription() -> String {
    return "The \(rank.simpleDescription()) of \(suit.simpleDescripton())"
  }
}
let threeOfSpades = Card(rank: .Three, suit: .Spades)
let threeOfSpadesDescription = threeOfSimpleDescription()
```

一个枚举成员的实例可以有实例值

- 相同的枚举成员可以有不同的值，创建实例的时候确定即可
- 原始值对于所有实例是相同的，实在定义枚举的时候设置的

```
// 从服务器取日出日落时间，考虑错误情况
enum ServerResponse {
  case Result(String,String)
  case Error(String)
}

let success = ServerResponse.Result("6:00 am", "8:09 pm")
let failure = ServerResponse.Error("Out of cheese.")

switch success {
  case let .Result(sunrise, sunset):
    let serverResponse = "Sunrise is at \(sunrise) and sunset is at \(sunset)."
  case let .Error(error):
    let serverResponse = "Failure... \(error)"
}
```

#### 协议和扩展

---

使用 protocol 来声明协议

- 类，枚举和结构体都可以实现协议
- 声明协议的时候 mutating 关键字用来标记一个会修改结构体的方法

```
protocol ExampleProtocol {
  var simpleDescription: String { get }
  mutating func adjust()
}

实现协议
class SimpleClass: ExampleProtocol {
  var simpleDescription: String = "A very simple class."
  var anotherProperty: Int = 69015
  func adjust() {
    simpleDescription += " Now 100% adjusted."
  }
} 
var a = SimpleClass()
a.adjust()
let aDescription = a.simpleDescription

struct SimpleStructure: ExampleProtocol {
  var simpleDescription: String = "A simple structure"
  mutating func adjust() {
    simpleDescription += " (adjusted)"
  }
}
var b = SimpleStructure()
b.adjust()
let bDescription = b.simpleDescription
```

使用 extension 为现有的类型添加功能（新的方法和参数），可以从外部框架引入一个类型，是这个类型遵循某个协议

```
extension Int: ExampleProtocol {
  var simpleDescription: String {
    return "The number \(self)"
  }
  mumating func adjust() {
    self += 42
  }
}
7.simpleDescription
```

可以像使用其他命名类型一样使用协议名，但是处理类型是协议的值时，协议外定义的方法不可用

```
// protocolValue 的类型是 simpleClass，但编译器把它当做 ExampleProtocol，所以不能调用在它之外实现的方法或属性
let protocolValue: ExampleProtocol = a
protocolValue.simpleDescription
protocolValue.anotherProperty  //报错，无法正常运行
```

#### 泛型

---

在尖括号里写一个名字来创建一个泛型函数或类型

```
func repeat<ItemType>(item: ItemType, times: Int) -> [ItemType] {
  var result = [ItemType]()
  for i in 0..<times {
    result.append(item)
  }
  return result
}
repeat("knock", 4)
```

也可以创建泛型类，枚举，结构体

```
enum OptionalValue<T> {
  case None
  case Some(T)
}
var possibleInteger: OptionalValue<Int> = .None
possibleInteger = .Some(100)
```

在类名后面使用 where 来指定对类型的需求

- where 可以省略，只在冒号后面写协议或者类名
- `<T: Equatable>` 和 `<T where T: Equatable>` 是等价的

```
func anyCommonElements <T, U where T: SequenceType, U: SequenceType, T.Generator.Element: Equatable, T.Generator.Element == U.Generator.Element> (lhs: T, rhs: U) -> Bool {
  for lhsItem in lhs {
    for rhsItem in rhs {
      if lhsItem == rhsItem {
        return true
      }
    }
  }
  return false
}
```

---

### 1.3 Swift版本历史记录

