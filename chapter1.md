# 一 基础部分

### 常量和变量

用`let来声明常量，用var来声明变量`

`let maximumNumberOfLoginAttempts = 10                                
 var currentLoginAttempt = 0`

### 类型标注_（type annotation）_

```
var welcomeMessage: String 声明中的冒号代表着“是...类型”
```

可以在一行中定义多个同样类型的变量，用逗号分割，并在最后一个变量名之后添加类型标注：var red, green, blue: Double

### 常量和变量的命名

常量与变量名不能包含数学符号，箭头，保留的（或者非法的）Unicode 码位，连线与制表符。也不能以数字开头，但是可以在常量与变量名的其他地方包含数字。

### 输出常量和变量

`print(friendlyWelcome)                          
// 输出 "Bonjour!"Swift 用字符串插值（string interpolation）的方式把常量名或者变量名当做占位符加入到长字符串中：print("The current value of friendlyWelcome is \(friendlyWelcome)")                          
// 输出 "The current value of friendlyWelcome is Bonjour!`

## 注释 {#ee656aa13bfbf6dfd83440765959d43f}

```
// 这是一个注释
/* 这是一个,
多行注释 */
嵌套的多行注释：
* 这是第一个多行注释的开头
/* 这是第二个被嵌套的多行注释 */
这是第一个多行注释的结尾 */
```

## 分号 {#cb368833d4910b55cc4cdc5539b69b97}

Swift 并不强制要求你在每条语句的结尾处使用分号（`;），当然，你也可以按照你自己的习惯添加分号。`

## 整数 {#b5f1a7cd15761173a095c35c5a06f177}

Swift 提供了8，16，32和64位的有符号和无符号整数类型。这些整数类型和 C 语言的命名方式很像，比如8位无符号整数类型是`UInt8，32位有符号整数类型是Int32。就像 Swift 的其他类型一样，整数类型采用大写命名法。`

### 整数范围

你可以访问不同整数类型的`min和max属性来获取对应类型的最小值和最大值：`

```
let minValue = UInt8.min  // minValue 为 0，是 UInt8 类型
let maxValue = UInt8.max  // maxValue 为 255，是 UInt8 类型
```

### Int

在32位平台上，Int和Int32长度相同。（-2,147,483,648~2,147,483,647）

在64位平台上，Int和Int64长度相同。

除非你需要特定长度的整数，一般来说使用`Int就够了。`

### UInt

尽量不要使用UInt，除非你真的需要存储一个和当前平台原生字长相同的无符号整数。除了这种情况，最好使用Int,即使你要存储的值已知是非负的。

### 浮点数

Double表示64位浮点数。当你需要存储很大或者很高精度的浮点数时请使用此类型。

Float表示32位浮点数。精度要求不高的话可以使用此类型。

### 类型安全和类型推断

由于 Swift 是类型安全的，所以它会在编译你的代码时进行_类型检查（type checks）_，并把不匹配的类型标记为错误。这可以让你在开发的时候尽早发现并修复错误。

当你在声明常量或者变量的时候赋给它们一个字面量（literal value 或 literal）即可触发类型推断。（字面量就是会直接出现在你代码中的值，比如`42和3.14159。）`

例如，如果你给一个新常量赋值`42并且没有标明类型，Swift 可以推断出常量类型是Int，因为你给它赋的初始值看起来像一个整数：`

```
let meaningOfLife = 42
// meaningOfLife 会被推测为 Int 类型
```

同理，如果你没有给浮点字面量标明类型，Swift 会推断你想要的是`Double：`

```
let pi = 3.14159
// pi 会被推测为 Double 类型
```

当推断浮点数的类型时，Swift 总是会选择`Double而不是Float。`

如果表达式中同时出现了整数和浮点数，会被推断为`Double类型：`

```
let anotherPi = 3 + 0.14159
// anotherPi 会被推测为 Double 类型
```

原始值`3没有显式声明类型，而表达式中出现了一个浮点字面量，所以表达式会被推断为Double类型。`

### 数值型字面量

```
let decimalInteger = 17
let binaryInteger = 0b10001       // 二进制的17
let octalInteger = 0o21           // 八进制的17
let hexadecimalInteger = 0x11     // 十六进制的17

数值类字面量可以包括额外的格式来增强可读性。整数和浮点数都可以添加额外的零并且包含下划线，并不会影响字面量：

let paddedDouble = 000123.456
let oneMillion = 1_000_000
let justOverOneMillion = 1_000_000.000_000_1
```

### 整数转换

`SomeType(ofInitialValue)`

是调用 Swift 构造器并传入一个初始值的默认方法。

```
let twoThousand: UInt16 = 2_000
let one: UInt8 = 1
let twoThousandAndOne = twoThousand + UInt16(one)
```

### 整数和浮点数转换

整数和浮点数的转换必须显式指定类型：

```
let three = 3
let pointOneFourOneFiveNine = 0.14159
let pi = Double(three) + pointOneFourOneFiveNine
// pi 等于 3.14159，所以被推测为 Double 类型
```

### 类型别名

_类型别名（type aliases）_就是给现有类型定义另一个名字。你可以使用`typealias关键字来定义类型别名。`

```
typealias AudioSample = UInt16
```

### 布尔值

Swift 有两个布尔常量，`true和false。`

### 元组

_元组（tuples）_把多个值组合成一个复合值。元组内的值可以是任意类型，并不要求是相同类型。

```
let http404Error = (404, "Not Found")
// http404Error 的类型是 (Int, String)，值是 (404, "Not Found")
```

你可以将一个元组的内容分解（decompose）成单独的常量和变量，然后你就可以正常使用它们了：

```
let (statusCode, statusMessage) = http404Error
print("The status code is \(statusCode)")
// 输出 "The status code is 404"
print("The status message is \(statusMessage)")
// 输出 "The status message is Not Found"
```

如果你只需要一部分元组值，分解的时候可以把要忽略的部分用下划线（`_）标记：`

```
let (justTheStatusCode, _) = http404Error
print("The status code is \(justTheStatusCode)")
// 输出 "The status code is 404"
```

此外，你还可以通过下标来访问元组中的单个元素，下标从零开始：

```
print("The status code is \(http404Error.0)")
// 输出 "The status code is 404"
print("The status message is \(http404Error.1)")
// 输出 "The status message is Not Found"
```

你可以在定义元组的时候给单个元素命名：

```
let http200Status = (statusCode: 200, description: "OK")
```

给元组中的元素命名后，你可以通过名字来获取这些元素的值：

```
print("The status code is \(http200Status.statusCode)")
// 输出 "The status code is 200"
print("The status message is \(http200Status.description)")
// 输出 "The status message is OK"
```

### 可选类型

使用_可选类型（optionals）_来处理值可能缺失的情况。可选类型表示：

* 有值，等于 x

或者

* 没有值

### nil

你可以给可选变量赋值为`nil来表示它没有值：`

```
var serverResponseCode: Int? = 404
// serverResponseCode 包含一个可选的 Int 值 404
serverResponseCode = nil
// serverResponseCode 现在不包含值
```

如果你声明一个可选常量或者变量但是没有赋值，它们会自动被设置为`nil：`

```
var surveyAnswer: String?
// surveyAnswer 被自动设置为 nil
```

### if 语句以及强制解析

你可以使用`if语句和nil比较来判断一个可选值是否包含值。你可以使用“相等”(==)或“不等”(!=)来执行比较。`

如果可选类型有值，它将不等于`nil：`

```
if convertedNumber != nil {
    print("convertedNumber contains some integer value.")
}
// 输出 "convertedNumber contains some integer value."
```

当你确定可选类型确实包含值之后，你可以在可选的名字后面加一个感叹号（`!）来获取值。这个惊叹号表示“我知道这个可选有值，请使用它。”这被称为可选值的`_`强制解析（forced unwrapping）`_`：`

```
if convertedNumber != nil {
    print("convertedNumber has an integer value of \(convertedNumber!).")
}
// 输出 "convertedNumber has an integer value of 123."
```

### 可选绑定

使用_可选绑定（optional binding）_来判断可选类型是否包含值，如果包含就把值赋给一个临时常量或者变量。

```
if let actualNumber = Int(possibleNumber) {
    print("\'\(possibleNumber)\' has an integer value of \(actualNumber)")
} else {
    print("\'\(possibleNumber)\' could not be converted to an integer")
}
// 输出 "'123' has an integer value of 123"
```

这段代码可以被理解为：

“如果Int\(possibleNumber\)返回的可选Int包含一个值，创建一个叫做actualNumber的新常量并将可选包含的值赋给它。”

可以包含多个可选绑定或多个布尔条件在一个if语句中，只要使用逗号分开就行。

### 隐式解析可选类型

有时候在程序架构中，第一次被赋值之后，可以确定一个可选类型\_总会\_有值。在这种情况下，每次都要判断和解析可选值是非常低效的，因为可以确定它总会有值。

这种类型的可选状态被定义为隐式解析可选类型（implicitly unwrapped optionals）。把想要用作可选的类型的后面的问号（`String?`）改成感叹号（`String!`）来声明一个隐式解析可选类型。

下面的例子展示了可选类型`String`和隐式解析可选类型`String`之间的区别：

```
let possibleString: String? = "An optional string."
let forcedString: String = possibleString! // 需要感叹号来获取值

let assumedString: String! = "An implicitly unwrapped optional string."
let implicitString: String = assumedString  // 不需要感叹号
```

> 注意：如果一个变量之后可能变成`nil`的话请不要使用隐式解析可选类型。如果你需要在变量的生命周期中判断是否是`nil`的话，请使用普通可选类型。

### 错误处理

当一个函数遇到错误条件，它能报错。调用函数的地方能抛出错误消息并合理处理。

```
func canThrowAnError() throws {
    // 这个函数有可能抛出错误
}
```

一个函数可以通过在声明中添加`throws`关键词来抛出错误消息。当你的函数能抛出错误消息时, 你应该在表达式中前置`try`关键词。

```
do {
    try canThrowAnError()
    // 没有错误消息抛出
} catch {
    // 有一个错误消息抛出
}
```

### 断言

### 使用断言进行调试

可以使用全局`assert(_:_:file:line:)`函数来写一个断言。向这个函数传入一个结果为`true`或者`false`的表达式以及一条信息，当表达式的结果为`false`的时候这条信息会被显示：

```
let age = -3
assert(age >= 0, "A person's age cannot be less than zero")
// 因为 age < 0，所以断言会触发
```



