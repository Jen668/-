# 基础

## 常量和变量

**常量**的值一旦设置就无法更改，而**变量**的值是可以被更改的。

### 声明常量和变量

使用`let`关键字声明**常量**，使用`var`关键字声明**变量**，示例代码如下：

```swift
// 声明一个常量
let sex = "man"

// 声明一个变量
var name = "alix"
```

也可以在一行上声明多个常量或者多个变量，以`,`分隔：

```swift
var x = 0.0, y = 0.0, z = 0.0
```



**如果代码中的存储值不会被更改，则始终将其声明为**常量**；否则，使用**变量**去存储需要更改的值。**

### 类型注释

声明常量或者变量时，可以提供类型注释，以明确常量或者变量可以存储的值类型，示例如下：

```swift
var welcomeMessage: String

welcomeMessage = "hello"

// 在一行上定义多个【相同类型】的变量
var red, green, blue: Double
```



> 在实践中定义一个常量或者变量时，很少需要提供类型注释。如果我们在定义常量或者变量时，为其提供初始值，Swift 会自动推动该常量或变量使用的类型。如果我们在定义常量或者变量时，没有为其提供初始值，那么就**需要提供**类型注释。否则，编译器会报错。



### 命名常量和变量

常量名和变量名几乎可以包含任何字符，包括 Unicode 字符：

```swift
let π = 3.14159
let 你好 = "你好世界"
let 🐶🐮 = "dogcow"
```



**常量名和变量名不能包含空格字符、数学符号、箭头、私人使用的 Unicode 标量值、行和框画字符，它们也不能以数字开头，但是数字可以被包含在名称的其他地方。**



一旦声明了特定类型的常量或者变量，就不能再次声明**同名**的常量或者变量，也不能更改常量或者变量的类型，也不能将常量更改为变量，也不能将变量更改为常量。



如果常量名或者变量名与保留的 Swift 关键字相同，可以使用`包围关键字。但是，除非我们别无选择，否则永远不要使用关键字作为常量或者变量的名称。

```swift
var `default` = "默认值"
`default` = "千金散尽还复来"
```



### 打印常量和变量

可以使用`print(_:separator:terminator:)`函数打印常量或者变量的当前值：

```swift
print(welcomeMessage)
```

值之间的分隔符（separator）默认为**空格字符**，终止符（terminator）默认为**换行符**。



## 注释

单行注释以两个正斜杠开头：

```swift
// this is a comment.
```

多行注释以正斜杠加星号开头，以星号加正斜杠结尾：

```swift
/* This is also a comment
but is written over multiple lines. */
```

嵌套多行注释：

```swift
/* This is the start of the first multiline comment.
/* This is the second, nested multiline comment. */ 
This is the end of the first multiline comment. */
```



## 分号

与其他语言不同，Swift 语言不要求我们在代码中的每个语句结束后写`;`。但是，如果我们想在一行上写多个单独的语句，则需要写`;`。

```swift
let cat = "🐱"; print(cat)
```



## 整数

Swift 以 **8位**（`Int8`或`UInt8`）、**16位**（`Int16`或`UInt16`）、**32位**（`Int32`或`UInt32`）、**64位**（`Int64`或`UInt64`） 形式提供有符号（正、零或负）和无符号（正或零）整数。

### 整数边界

可以通过访问整数类型的`min`和`max`属性来获取该整数类型的边界：

```swift
let minUInt32Value = UInt32.min
let maxUInt32Value = UInt32.max
```

### Int 和 UInt

`Int`和`UInt`是动态定义的类型。在 32位 架构下，`Int`等同于`Int32`，`UInt`等同于`UInt32`；在 64位 架构下，`Int`等同于`Int64`，`UInt`等同于`UInt64`。



**Swift 默认整数类型为`Int`类型，除非我们需要处理特定大小的整数，否则请始终使用`Int`类型来定义整数。即使已知要存储的值为非负值，也应该使用`Int`，而不是`UInt`，除非指定需要使用`UInt`。定义整数时，统一使用`Int`有助于代码互操作性，避免了在不同数字类型之间转换的必要性，并能匹配整数类型推断。**



## 浮点数

Swift 提供了两种**有符号**浮点数类型：

- `Double`表示 64位 浮点数。
- `Float`表示 32位 浮点数。



**Swift 默认的浮点数类型为`Double`。`Double`的精度至少为小数点后 15 位，而`Float`的精度可以到小数点后 6 位。**

```swift
let sp: Float = 1.6666666666666666
        
print("\(sp)") // 输出结果为 1.6666666
```



## 类型安全和类型推断

Swift 语言是类型安全的，其会在编译代码时执行类型检查，并将任何不匹配的类型标记为错误。



当使用不同类型的值时，类型检查可以帮助我们避免错误。然而，这并不意味着我们必须指定我们声明的每个常量或变量的类型。如果我们没有指定常量或变量的类型，编译器在编译代码时，会根据我们提供的初始值自动推断常量或变量的类型。



```swift
// meaningOfLife 常量会被自动推断 Int 类型
let meaningOfLife = 42

// pi 常量会被自动推断为 Double 类型
let pi = 3.14159

// anotherPi 常量会自动推断为 Double 类型
let anotherPi = 3 + 0.14159
```



## 数字字面量



整数[字面量](https://baike.baidu.com/item/字面量/8500322?fr=aladdin)可以写成：

- 十进制数，没有前缀
- 二进制数，前缀为0b
- 八进制数，前缀为0o
- 十六进制数，前缀为0x

以下这些整数字面量的十进制值均为`17`：

```swift
let decimalInteger = 17
let binaryInteger = 0b10001
let octalInteger = 0o21
let hexadecimalInteger = 0x11
```

### 

浮点数字面量可以是十进制（没有前缀）或者十六进制（前缀为0x）。十进制浮点数可以有一个**可选的指数**，由大写或小写 **e** 表示。十六进制浮点数**必须有一个指数**，由大小或小写 **p** 表示。

以下所有浮点数字面量的十进制值为`12.1875`：

```swift
let decimalDouble = 12.1875
// 乘以10
let exponentDouble1 = 1.21875e1
// 乘以-10
let exponentDouble2 = 121.875e-1
let hexadecimalDouble = 0xC.3p0
```



数字字面量还可以包含额外的格式，使其更容易阅读。整数和浮点数都可以使用**额外的零**填充，并可以包含**下划线**来提升可读性，这样做并不会改变字面量的值。

```swift
let paddedDouble = 000123.456
let oneMillion = 1_000_000
let justOverOneMillion = 1_000_000.000_000_1
```



## 数字类型转换

对于代码中的所有通用整数常量和变量，都应使用 Swift 默认的整数类型`Int`，即使它们的值已知为负数。使用默认的整数类型意味着整数常量和整数变量在代码中可以立即互操作，并能匹配整数字面量的推断类型。



只有当当前任务指定需要其他整数类型时，例如：整数是来自外部来源的显式大小数据，整数是用于性能、内存使用或其他必要的优化的。在这些情况下，使用显式大小的类型有助于捕获任何意外值溢出，并隐式记录使用数据的性质。



### 整数转换

每个数字类型可以存储的数字范围是不同的。`Int8`类型可以存储的数字在`-128`到`127`之间，而`UInt8`类型可以存储的数字在`0`到`255`之间。**在编译代码时，如果存储值超出了数字类型可以存储的数字范围，编译器会报错。**



**将一种数字类型的值赋值给另一种数字类型的常量或变量时，必须先使用现有值初始化一个所需数字类型的新值，然后再将这个新值赋值给这个常量或变量。否则，编译器会报错。**



`SomeType(value)`方法（ SomeType 是类名称，value 是现有值）是调用 Swift 类型的初始化程序并传递初始值的默认方法。

```swift
let twoThousand: UInt16 = 2_000
let one: UInt8 = 1
let twoThousandAndOne = twoThousand + UInt16(one)
```



### 整数和浮点数转换

整数类型和浮点数类型之间的转换**必须明确**：

```swift
let three = 3
let pointOneFourOneFiveNine = 0.14159
let pi = Double(three) + pointOneFourOneFiveNine
```



将浮点数转换为整数时，浮点数的值会被截断，也就是说`4.75`变成了`4`，`-3.9`变成了`-3`。



组合数字类型常量和数字类型变量的规则与组合数字字面量的规则是不一样的。字面量值`3`可以直接与字面量值`0.14159`相加，因为字面量值的类型是在编译时推断出来的。

```swift
// 可以直接组合数字字面量
let a = 3 + 0.14159

// 但是不能直接组合数字类型常量和数字类型变量,必须先进行转换
let a = 3
let b = Double(a) + 0.14159
```



## 类型别名

类型别名是为现有类型定义的备用名称，我们可以使用`typealias`关键字定义类型别名。



当我们想通过上下文更合适的名称来引用现有类型时，例如在处理来自外部源的特定大小的数据时，类型别名非常有用。



```swift
typealias AudioSample = UInt16

var maxAmplitudeFound = AudioSample.min
```

对`AudioSample.min`的调用实际上调用的是`UInt16.min`。



## Boolean

Swift 提供了一个基础的布尔类型`Boolean`，`Boolean`常量或变量的值只能为`true`或者`false`。

```swift
let orangesAreOrange = true
let turnipsAreDelicious = false

if (orangesAreOrange)
{
	print("YES!")
}
```

## 元组

元组是由多个值组成的一个复合值，元组中的每个值可以是任何类型。以下代码中的`(404, "Not Found")`元组由一个`Int`类型的值和一个`String`类型的值组成：

```swift
let http404Error = (404, "Not Found")
```

我们可以将元组中的值分解为单独的常量或者变量，然后像往常一样访问它们：

```swift
let (statusCode, statusMessage) = http404Error
print("The status code is \(statusCode)")
// Prints "The status code is 404"
print("The status message is \(statusMessage)")
// Prints "The status message is Not Found"
```

如果我们只需要元组中的部分值，则在分解元组时使用下划线`_`来忽略元组中其他不需要的值：

```swift
let (justTheStatusCode, _) = http404Error
print("The status code is \(justTheStatusCode)")
// Prints "The status code is 404"
```

或者，使用从`0`开始的索引去访问元组中的单个元素值：

```swift
print("The status code is \(http404Error.0)")
// Prints "The status code is 404"
print("The status message is \(http404Error.1)")
// Prints "The status message is Not Found"
```

在定义一个元组时，还可以为元组中的元组命名：

```swift
let http200Status = (statusCode: 200, description: "OK")
```

如果有为元组中的元素命名，则可以使用元素名称来访问元组中的元素值：

```swift
print("The status code is \(http200Status.statusCode)")
// Prints "The status code is 200"
print("The status message is \(http200Status.description)")
// Prints "The status message is OK"
```



当函数有多个返回值时，使用元组作为函数的返回值是非常有用的。



元组对于简单的相关值的组合是非常有用的，但其不适合创建复杂的数据结构。如果数据结构比较复杂，应该为其构建类或者结构体，参看[结构体和类]()。



## 可选

**可选表示变量或常量的值有两种可能性：要么有一个值，要么为空。**



由于 Swift 是类型安全的，定义一个变量或常量后，在编译代码时会确定变量或常量的类型。之后，如果将类型不匹配的值赋值给这个变量或常量，编译器会报错。为了解决变量或常量的值可能不存在（为空）的情况，Swift 提供了可选类型。类型后面加上`?`，表示这是个可选类型，例如，`Int?`表示可选的`Int`类型。



> 注意：可选的`Int`类型表示它的值可能为一个`Int`值，或者可能为空（不存在任何值）。但是，它的值不可能是任何其他类型的值。



### nil

将特殊值`nil`分配给一个可选变量，可以将这个可选变量设置为无值状态：

```swift
var serverResponseCode: Int? = 404
// serverResponseCode contains an actual Int value of 404
serverResponseCode = nil
// serverResponseCode now contains no value
```

如果我们定义了一个可选变量，并且没有为其提供初始值，那么这个可选变量会被自动设置为`nil`：

```swift
var surveyAnswer: String?
// surveyAnswer is automatically set to nil
```



**Swift 中的`nil`与 Objective-C 中的`nil`是有区别的。Objective-C 中的`nil`是一个指向空值对象的指针，而 Swift 中的`nil`不是一个指针，而是一个缺少某种类型的值。可以将任何类型的可选值设置为`nil`，而不仅仅是对象类型。**



### if 语句和强制展开可选值

可以通过使用`==`或`!=`操作符将可选变量或常量的值与`nil`进行比较，并使用`if`语句来判断出可选值是否包含值。

```swift
if convertedNumber != nil {
    print("convertedNumber contains some integer value.")
}
// Prints "convertedNumber contains some integer value."
```

一旦确定可选值确实存在一个值，我们就可以通过在可选值名称后面加上感叹号`!`来访问这个值，这被称为强制展开可选值。

```swift
if convertedNumber != nil {
    print("convertedNumber has an integer value of \(convertedNumber!).")
}
// Prints "convertedNumber has an integer value of 123."
```



> 如果可选值不包含非`nil`值，使用`!`强制展开可选值时，会触发运行时错误。



### 可选绑定

可以使用可选绑定来确定可选值是否存在非空值，如果存在，则会将这个值用作临时常量或变量。可选绑定可以与`if`和`while`语句一起使用，以便检查可选变量或常量的值，并将该值提取到其他常量或变量中。

```swift
if let actualNumber = Int(possibleNumber) {
    print("The string \"\(possibleNumber)\" has an integer value of \(actualNumber)")
} else {
    print("The string \"\(possibleNumber)\" couldn't be converted to an integer")
}
// Prints "The string "123" has an integer value of 123"
```



可以根据需要在单个`if`语句中包含尽可能多的可选绑定和布尔条件，并用逗号分割。如果某个可选绑定中的值为`nil`或者布尔条件为`false`，则整个`if`语句的条件视为`false`。以下`if`语句是等效的：

```swift
if let firstNumber = Int("4"), let secondNumber = Int("42"), firstNumber < secondNumber && secondNumber < 100 {
    print("\(firstNumber) < \(secondNumber) < 100")
}
// Prints "4 < 42 < 100"

if let firstNumber = Int("4") {
    if let secondNumber = Int("42") {
        if firstNumber < secondNumber && secondNumber < 100 {
            print("\(firstNumber) < \(secondNumber) < 100")
        }
    }
}
// Prints "4 < 42 < 100"
```



> 在`if`语句中使用可选绑定创建的常量或变量只能在`if`语句的主体内可用。



### 隐式展开可选值

有时，从程序的结构可以明显看出首次给可选变量设置值之后，可选变量将始终具有该值。在这种情况下，消除每次访问可选值时检查可选值是否存在值和强制展开可选值的需要非常有用。



在声明常量或变量时，在类型之后添加感叹号（`String!`）而不是问号（`String?`）可以将可选值定义为隐式展开的可选值：

```swift
let possibleString: String? = "An optional string."
let forcedString: String = possibleString! // requires an exclamation point

let assumedString: String! = "An implicitly unwrapped optional string."
let implicitString: String = assumedString // no need for an exclamation point
```



当可选值在首次定义并且确认存在值后，隐式展开可选值非常有用。Swift 中的隐式展开可选值的主要用途是在类初始化期间，可以参看 [unowned 引用和隐式展开的可选属性]()。



如果一个隐式展开的可选值为`nil`，当我们尝试访问可选值时，会触发运行时错误。



我们可以像检查普通可选值一样检查隐式展开的可选值是否为`nil`：

```swift
if assumedString != nil {
    print(assumedString!)
}
// Prints "An implicitly unwrapped optional string."
```



还可以在可选绑定中使用隐式展开的可选值：

```swift
if let definiteString = assumedString {
    print(definiteString)
}
// Prints "An implicitly unwrapped optional string."
```



> 如果变量稍后可能被设置为`nil`，请不要使用隐式展开的可选类型。如果需要在变量的生命周期内检查`nil`值，请始终使用普通的的可选类型。



## 错误处理

可以使用错误处理来响应程序在执行过程中可能遇到的错误条件。



可选类型可以使用值的存在或不存在来传达函数的成功或失败。与可选类型相反，错误处理允许我们确定失败的根本原因，并在必要时将错误传达给程序的另一部分。



当函数遇到错误条件时，它会抛出错误。然后该函数的调用者可以捕获错误并做出适当响应。

```swift
func canThrowAnError() throws {
    // this function may or may not throw an error
}
```



一个函数通过在声明中使用`throws`关键字来表明它可以引发错误。调用可能引发错误的函数时，请将`try`关键字放在调用表达式的前面。

```swift
do {
    try canThrowAnError()
    // no error was thrown
} catch {
    // an error was thrown
}
```



以下是如何使用错误处理来响应不同错误条件的示例：

```swift
func makeASandwich() throws {
    // ...
}

do {
    try makeASandwich()
    eatASandwich()
} catch SandwichError.outOfCleanDishes {
    washDishes()
} catch SandwichError.missingIngredients(let ingredients) {
    buyGroceries(ingredients)
}
```

如果调用`makeASandwich()`函数没有引发错误，则会执行`eatASandwich()`函数；否则，将会执行`catch`语句。



## 断言和先决条件

断言和先决条件是在运行时进行的检查。可以使用它们来确保在满足基本条件之后，才执行任何其他代码。如果断言或先决条件中的布尔条件被判定为`true`，则会继续执行后续的其他代码；如果布尔条件被判定为`false`，则代码执行结束并且会终止运行应用程序。



断言和先决条件可以表达我们在编码时所做的假设和期望。断言帮助我们在开发过程中发现错误和错误的假设，先决条件可以帮助我们发现在生产环境下的问题。



除了在运行时验证我们的期望外，断言和先决条件也可以成为代码中有用的文档形式。与之前在[错误处理]()章节中讨论的错误条件不同，断言和先决条件并不是用于可恢复或预期的错误的。因为失败的断言或先决条件表明程序处于无效状态，这时是无法捕获失败的断言的。



使用断言和先决条件并不能替代以不太可能出现无效条件的方式设计代码。然而，使用它们来强制执行有效的数据和状态，可以让应用程序处于无效状态时更可预测地终止。一旦检测到无效状态，立即停止执行后续代码也有助于限制该无效状态造成的损害。



断言和先觉条件之间的区别在于：断言仅在**调试环境**中检查，而先决条件在**调试和生产环境**中都会检查。在生产环境中，不会判定断言中的条件。这意味着我们可以在开发过程中使用任意多的断言，而不会影响生产环境下的程序性能。



### 使用断言调试

通过调用由 Swift 标准库提供的`assert(_:_:file:line:)`函数来写一个断言，我们需要向该函数传递一个用于计算结果为`true`或`false`的表达式，和一个当表达式结果为`false`时显示的 message。例如：

```swift
let age = -3
assert(age >= 0, "A person's age can't be less than zero.")
// This assertion fails because -3 isn't >= 0.
```

如果我们的代码已经检查了条件，则可以使用`assertionFailure(_:file:line:)`函数来表明断言失败：

```swift
if age > 10 {
    print("You can ride the roller-coaster or the ferris wheel.")
} else if age >= 0 {
    print("You can ride the ferris wheel.")
} else {
    assertionFailure("A person's age can't be less than zero.")
}
```



### 执行先决条件

只要条件有可能为`false`，但条件又必须为真，以便代码继续执行时，请使用先决条件。例如，使用先决条件检查数组下标是否越界，或检查函数是否已传递有效值。



通过调用`precondition(_:_:file:line:)`函数来写一个先决条件，我们需要向该函数传递一个用于计算结果为`true`或`false`的表达式，和一个当表达式结果为`false`时显示的 message。例如：

```swift
// In the implementation of a subscript...
precondition(index > 0, "Index must be greater than zero.")
```

如果我们的代码已经检查了条件，则可以使用`preconditionFailure(_:file:line:)`函数来表明发生了发生了故障。



> 如果我们以未检查（-0unchecked）模式编译，则先决条件不会被检查。编译器会假定先决条件始终为`true`，并会相应地优化我们的代码。然而，无论优化设置如何，`fatalError(_:file:line:)`函数始终会暂停执行。



> 在原型开发和早期开发过程中，可以使用`fatalError(_:file:line:)`函数来为尚未实现的功能创建存根。通过编写`fatalError("Unimplemented")`代码来作为存根实现。由于致命错误永远不会被优化，这与断言或先决条件不同，因此可以确保在遇到存根实现时总是停止执行程序。



# 基本运算符



## 赋值运算符

使用`=`运算符将值赋值给常量或变量：

```swift
let b = 10
var a = 5
a = b
// a is now equal to 10

let (x, y) = (1, 2)
// x is equal to 1, and y is equal to 2
```



## 算术运算符

Swift 支持所有数字类型的四个标准算术运算符：

- 加：`+`

- 减：`-`

- 乘：`*`

- 除：`/`

```swift
1 + 2       // equals 3
5 - 3       // equals 2
2 * 3       // equals 6
10.0 / 2.5  // equals 4.0
```



与 C 和 Objective-C 中的算术运算符不同，Swift 算术运算符默认情况下不允许值溢出。可以使用 Swift 的溢出运算符（例如`&+`）来对溢出行为进行处理。



`+`运算符还支持字符串拼接：

```swift
"hello, " + "world"  // equals "hello, world"
```



### 取余运算符

使用`%`运算符来计算数字 a 除以数字 b 的余数：

```swift
9 % 4    // equals 1
-9 % 4   // equals -1
```



### 一元负数运算符

可以使用`-`来改变数字的正负：

```swift
let three = 3
let minusThree = -three       // minusThree equals -3
let plusThree = -minusThree   // plusThree equals 3, or "minus minus three"
```





### 一元正数运算符

一元正数运算符什么事情也不会做，只是返回它操作的值：

```swift
let minusSix = -6
let alsoMinusSix = +minusSix  // alsoMinusSix equals -6
```



## 复合赋值运算符

与 C 一样，Swift 也提供了将`=`运算符与另一个算术运算符相结合的复合赋值运算符。

```swift
var a = 1
a += 2
// a is now equal to 3
```

表达式`a += 2`是`a = a + 2`的简写。



## 比较运算符

Swift 支持以下比较运算符：

- 等于：`==`

- 不等于：`!=`

- 大于：`>`
- 小于：`<`
- 大于等于：`>=`
- 小于等于：`<=`

```swift
1 == 1   // true because 1 is equal to 1
2 != 1   // true because 2 isn't equal to 1
2 > 1    // true because 2 is greater than 1
1 < 2    // true because 1 is less than 2
1 >= 1   // true because 1 is greater than or equal to 1
2 <= 1   // false because 2 isn't less than or equal to 1
```



如果两个元组类型相同，值数量相同，那么就可以对它们进行比较。如果两个元组中的所有元素都相同，则这两个元组是相等的；否则，不相等。例如：

```swift
(1, "zebra") < (2, "apple")   // true because 1 is less than 2; "zebra" and "apple" aren't compared
(3, "apple") < (3, "bird")    // true because 3 is equal to 3, and "apple" is less than "bird"
(4, "dog") == (4, "dog")      // true because 4 is equal to 4, and "dog" is equal to "dog"
```



另外，`>`、`<`、`>=`和`<=`运算符是不能应用于布尔值的。否则，会报错：

```swift
("blue", -1) < ("purple", 1)        // OK, evaluates to true
("blue", false) < ("purple", true)  // Error because < can't compare Boolean values
```



> Swift 标准库提供的比较运算符只能比较包含不超过七个元素的元组。要比较包含超过七个或更多元素的元组，我们必须自己实现比较运算符。



## 条件运算符

与 C 和 Objective-C 一样，Swift 也提供有条件运算符，例如：`a > b ? value1 : value2`，如果`a > b`的运算结果为`true`，就会返回`value1`；否则，会返回`value2`。它等同于以下代码：

```swift
if a > b {
    value1
} else {
    value2
}
```



## Nil-Coalescing 运算符

使用 nil-coalescing 运算符`??`的表达式`a ?? b`，其含义是：如果可选值`a`包含一个值，则会展开可选值`a`的值并返回该值；如果可选值`a`为`nil`，则会返回默认值`b` 。**这里，`b`的类型必须与`a`的类型相匹配。**`a ?? b`等同于以下代码：

```swift
a != nil ? a! : b
```



## 区间运算符



### 闭区间运算符

闭区间运算符`a...b`定义了从`a`到`b`的范围，包括值`a`和`b`，`a`不得大于`b`。使用示例代码如下：

```swift
for index in 1...5 {
    print("\(index) times 5 is \(index * 5)")
}
// 1 times 5 is 5
// 2 times 5 is 10
// 3 times 5 is 15
// 4 times 5 is 20
// 5 times 5 is 25
```



### 半开区间运算符

半开区间运算符`a..<b`定义了从`a`到`b`的范围，但不包括`b`。使用示例代码如下：

```swift
let names = ["Anna", "Alex", "Brian", "Jack"]
let count = names.count
for i in 0..<count {
    print("Person \(i + 1) is called \(names[i])")
}
// Person 1 is called Anna
// Person 2 is called Alex
// Person 3 is called Brian
// Person 4 is called Jack
```



### 单侧区间（不是运算符！！！）

闭区间运算符还有一个替代形式 ——用于尽可能向一个方向继续的区间，例如：区间包括数组从索引`2`到数组末尾的所有元素。在这种情况下，可以省略闭区间运算符一侧的值，这种区间被称为单侧区间，因为只在运算符一侧有值。例如：

```swift
for name in names[2...] {
    print(name)
}
// Brian
// Jack

for name in names[...2] {
    print(name)
}
// Anna
// Alex
// Brian

for name in names[..<2] {
    print(name)
}
// Anna
// Alex
```



单侧区间还可以用于其他上下文，而不仅仅是数组下标。**但是，我们不能在只有一侧有值的单侧区间内迭代，因为不清楚迭代应该从哪里开始。**上面的代码可以迭代是因为数组的下标是从`0`开始的。我们可以检查单侧区间是否包含某个特定值，例如：

```swift
let range = ...5
range.contains(7)   // false
range.contains(4)   // true
range.contains(-1)  // true
```



## 逻辑运算符

逻辑运算符修改或组合`Boolean`逻辑值`true`和`false`。Swift 支持 C 语言中的三种标准逻辑运算符：

- 逻辑非：`!a`
- 逻辑与：`a && b`
- 逻辑或：`a || b`



# 字符串和字符

Swift 使用`String`类型表字符串，使用`Character`类型来表示单个字符。



## 字符串字面量

字符串字面量是被双引号`"`包围的字符序列：

```swift
let someString:String = "Some string literal value"
```



### 多行字符串字面量

如果需要一个跨越多行的字符串，请使用多行字符串字面量。多行字符串字面量是由三个双引号`"`包围的字符序列，并且包围字符序列的前后三个双引号都要**单独占用一行**（被包围的字符序列并不会以换行符开头和结束）：

```swift
let quotation = """
The White Rabbit put on his spectacles.  "Where shall I begin,
please your Majesty?" he asked.

"Begin at the beginning," the King said gravely, "and go on
till you come to the end; then stop."
"""
```

当多行字符串文本中保行换行符时，该换行符也会出现在字符串的值中。**如果我们想使用换行符来使我们的源代码更容易阅读，但又不希望换行符成为字符串值的一部分，可以在这些行的末尾加上一个反斜杠`\`：**

```swift
let softWrappedQuotation = """
The White Rabbit put on his spectacles.  "Where shall I begin, \
please your Majesty?" he asked.

"Begin at the beginning," the King said gravely, "and go on \
till you come to the end; then stop."
"""
```

要想多行字符串以换行开头或结束，请使用空白行作为第一行或最后一行（也可以使用换行符`\n`）：

```swift
let lineBreaks = """

This string starts with a line break.
It also ends with a line break.

"""
```

**注意，多行字符串中每一行的缩进必须大于或等于结尾三个双引号的缩进。如果某一行的缩进超出了结尾三个双引号的缩进，那么额外多出来的缩进会被算作空格字符作为多行字符串的值。**

![多行字符串缩进.png](https://docs.swift.org/swift-book/_images/multilineStringWhitespace_2x.png)



### 字符串字面量中的特殊字符

字符串字面量中可以包含以下特殊字符：

- 转义的特殊字符：空字符`\0`（不是空格字符），反斜杠`\\`，水平制表符`\t`，换行符`\n`，回车符`\r`，双引号`\"`，单引号`\'`。
- 任意 Unicode 标量值，写为`\u{n}`，其中`n`是 1-8 位数的十六进制数。（参看后面的 [Unicode]() 章节）

```swift
let wiseWords = "\"Imagination is more important than knowledge\" - Einstein"
// "Imagination is more important than knowledge" - Einstein
let dollarSign = "\u{24}"        // $,  Unicode scalar U+0024
let blackHeart = "\u{2665}"      // ♥,  Unicode scalar U+2665
let sparklingHeart = "\u{1F496}" // 💖, Unicode scalar U+1F496
```



在多行字符串字面量中，可以直接使用双引号`"`。如果要在多行字符串字面量中使用连续的三个双引号`"`，则需要像下面这样使用：

```swift
let threeDoubleQuotationMarks = """
Escaping the first quotation mark \"""
Escaping all three quotation marks \"\"\"
"""
```



### 扩展字符串定界符

如果我们需要在字符串包含特殊字符而无需调用其效果，则可以使用扩展定界符包围字符串字面量。例如，打印字符串`#"你好啊\n很高兴认识你"#`时，将会打印`\n`，而不是换行打印。



如果想要扩展定界符包围的字符串中的转义字符生效，可以在转义字符`\`后插入扩展定界符`#`。字符串每一侧被多少个扩展定界符`#`包围，就要在字符串中的转义字符`\`后插入多少个扩展定界符`#`。例如，打印`#你好啊\#n很高兴认识你`字符串时，换行符会生效。



也可以使用扩展定界符包围多行字符串字面量，例如多行字符串字面量中包含连续的三个双引号`"""`时：

```swift
let threeMoreDoubleQuotationMarks = #"""
Here are three more double quotes: """
"""#
```



## 初始化空字符串

创建空字符串的方式有两种，一种是直接将空字符串字面量赋值给变量，一种是使用初始化语法初始化一个新的`String`实例：

```swift
var emptyString = ""               // empty string literal
var anotherEmptyString = String()  // initializer syntax
// these two strings are both empty, and are equivalent to each other
```

可以通过`String`的`isEmpty`属性来确定其值是否为空字符串：

```swift
if emptyString.isEmpty {
    print("Nothing to see here")
}
// Prints "Nothing to see here"
```



## 字符串可变性

字符串**常量**是不可变的，字符串**变量**是可变的：

```swift
var variableString = "Horse"
variableString += " and carriage"
// variableString is now "Horse and carriage"

let constantString = "Highlander"
constantString += " and another Highlander"
// 编译报错!!!
```



## 字符串是值类型

Swift 的`String`类型是值类型。如果我们新建一个`String`值，在将这个`String`值传递给函数或方法时，或者将它赋值给常量或变量时，会根据这个`String`值深拷贝出一个新的`String`值，并将这个新的`String`值传递给函数或方法，或者赋值给常量或变量。



在后台，Swift 的编译器优化了字符串的用法，以便仅在绝对必要时才进行实际赋值。



## 与字符配合

可以通过使用`for-in`循环遍历字符串来访问字符串中的每个`Character`值：

```swift
for character in "Dog!🐶" {
    print(character)
}
// D
// o
// g
// !
// 🐶
```



可以使用`Character`值数组来构造`String`值：

```swift
let catCharacters: [Character] = ["C", "a", "t", "!", "🐱"]
let catString = String(catCharacters)
print(catString)
// Prints "Cat!🐱"
```



## 拼接字符串和字符

可以使用加法运算符`+`来拼接两个`String`值：

```swift
let string1 = "hello"
let string2 = " there"
var welcome = string1 + string2
// welcome now equals "hello there"
```

还可以使用复合赋值运算符`+=`将`String`值拼接到现有的`String`变量中：

```swift
var instruction = "look over"
instruction += string2
// instruction now equals "look over there"
```

还可以使用`String`类型的`append()`方法将`Character`值拼接到`String`变量中：

```swift
let exclamationMark: Character = "!"
welcome.append(exclamationMark)
// welcome now equals "hello there!"
```



## 字符串插值

字符串差值是一种通过组合常量、变量、文本和表达式来构建一个新的`String`值的方法。

```swift
let multiplier = 3
let message = "\(multiplier) times 2.5 is \(Double(multiplier) * 2.5)"
// message is "3 times 2.5 is 7.5"
```

也可以使用扩展定界符包围字符串来使字符串差值无效：

```swift
print(#"Write an interpolated string in Swift using \(multiplier)."#)
// Prints "Write an interpolated string in Swift using \(multiplier)."
```

要想被扩展定界符`#`包围的字符串中的字符串差值生效，需要在转义字符`\`后插入扩展定界符`#`：

```swift
print(#"6 times 7 is \#(6 * 7)."#)
// Prints "6 times 7 is 42."

let string = ###"""
      	 6 times 7 is \###(6 * 7).
      	 """###
print(string)
// Prints "6 times 7 is 42."
```



## Unicode

Unicode 是用于在不同书写系统中编码，表示和处理文本的国际标准。



### Unicode 标量值

在后台，Swift 的本地`String`类型是根据 Unicode 标量值构建的。Unicode 标量值是字符或修饰符的唯一21位数字，例如，`a`的 Unicode 标量值为`U+0061`，`🐥`的 Unicode 标量值为`U+1F425`。



注意，并非所有21位 Unicode 标量值都分配给了一个字符，其中某些标量值是被保留以供将来分配或者用于 UTF-16 编码的。



### 扩展字素簇

Swift 的每个`Character`类型的值都代表一个扩展字素簇。**扩展字素簇是一个或多个 Unicode 标量的序列**，这些标量组合时会产生一个人类可读的字符。



这里有一个例子，带有二声声调的字母`é`可以由单个 Unicode 标量值`U+00E9`表示，但也可以由字母`e`的标量值`U+0065`和二声声调`ˊ`的标量值`U+0301`组合起来表示：

```swift
let eAcute: Character = "\u{E9}"                         // é
let combinedEAcute: Character = "\u{65}\u{301}"          // e followed by ́
// eAcute is é, combinedEAcute is é

let precomposed: Character = "\u{D55C}"                  // 한
let decomposed: Character = "\u{1112}\u{1161}\u{11AB}"   // ᄒ, ᅡ, ᆫ
// precomposed is 한, decomposed is 한

let enclosedEAcute: Character = "\u{E9}\u{20DD}"
// enclosedEAcute is é⃝

let regionalIndicatorForUS: Character = "\u{1F1FA}\u{1F1F8}"
// regionalIndicatorForUS is 🇺🇸
```



## 字符个数

可以使用`String`的`count`属性来检索字符串中`Character`值的个数：

```swift
let unusualMenagerie = "Koala 🐨, Snail 🐌, Penguin 🐧, Dromedary 🐪"
print("unusualMenagerie has \(unusualMenagerie.count) characters")
// Prints "unusualMenagerie has 40 characters"
```

注意，Swift 对`Character`值使用扩展字素簇来表示字符串的拼接和修改，可能并不会改变字符串中字符个数，例如，`cafe`后面拼接二声声调`ˊ`的标量值`U+0301`，结果为`café`，还是只包含`4`个字符。

```swift
var word = "cafe"
print("the number of characters in \(word) is \(word.count)")
// Prints "the number of characters in cafe is 4"

word += "\u{301}"    // COMBINING ACUTE ACCENT, U+0301

print("the number of characters in \(word) is \(word.count)")
// Prints "the number of characters in café is 4"
```



> 扩展字素簇可以由多个 Unicode 标量值组成，这意味着不同的字符（以及相同字符的不同表现形式）可能需要占用不同大小的内存空间。如果不对字符串进行迭代来确定其扩展字素簇边界，就无法计算字符串中字符个数。注意，`count`属性必须遍历整个字符串的 Unicode 标量，以便确定该字符串中的字符个数。



> `String`的`count`属性返回的字符个数并不总是与包含相同字符的`NSString`的`length`属性返回的字符个数相同。`NSString`的长度取决于字符串的 UTF-16 表示形式中 16位 代码单元的数量，而不取决于字符串中的 Unicode 扩展字素簇的数量。



## 访问和修改字符串



### 字符串索引

如上所述，不同的字符可能需要占用不同大小的内存，如果想要确定某个字符在字符串中的位置，则必须从字符串的开头或结尾对字符串的每个`Unicode`标量进行迭代。**因此，Swift 字符串无法用整数值建立索引。**



`String`类型关联有一个`Index`类型，`Index`类型的值对应着某个字符在字符串中位置。



可以使用`String`的`startIndex`属性（`String`类型关联的`Index`类型）访问字符串中第一个字符的位置，`endIndex`属性是字符串中最后一个字符的位置。



可以使用`String`的`index(before:)`和`index(after:)`方法来访问给定索引的前一个和后一个索引。如果要访问距离给定索引更远的索引，可以使用`index(_:offsetBy:)`方法。



可以使用下标（不是整数）语法访问字符串中指定索引位置处的字符：

```swift
let greeting = "Guten Tag!"
greeting[greeting.startIndex]
// G
greeting[greeting.index(before: greeting.endIndex)]
// !
greeting[greeting.index(after: greeting.startIndex)]
// u
let index = greeting.index(greeting.startIndex, offsetBy: 7)
greeting[index]
// a
```

尝试访问字符串索引范围之外的索引，会触发运行时错误。



使用`indices`属性访问字符串的所有索引：

```swift
for index in greeting.indices {
    print("\(greeting[index]) ", terminator: "")
}
// Prints "G u t e n   T a g ! "
```



> 任何遵循`Collection`协议的类型都可以使用`startIndex`和`endIndex`属性以及`index(before:)`、`index(after:)`和`index(_:offsetBy:)`方法，包括`String`、`Array`、`Dictionary`和`Set`。



### 插入和删除

使用`insert(_:at:)`方法将单个字符插入到字符串的指定位置，使用`insert(contentsOf:at:)`方法将另一个字符串插入到字符串的指定位置。

```swift
var welcome = "hello"
welcome.insert("!", at: welcome.endIndex)
// welcome now equals "hello!"

welcome.insert(contentsOf: " there", at: welcome.index(before: welcome.endIndex))
// welcome now equals "hello there!"
```



使用`remove(at:)`方法删除字符串中指定位置处的字符，使用`removeSubrange(_:)`方法删除指定范围处的子字符串。

```swift
welcome.remove(at: welcome.index(before: welcome.endIndex))
// welcome now equals "hello there"

let range = welcome.index(welcome.endIndex, offsetBy: -6)..<welcome.endIndex
welcome.removeSubrange(range)
// welcome now equals "hello"
```



> 任何遵循`Collection`协议的类型都可以使用`insert(_:at:)`、`insert(contentsOf:at:)`、`remove(at:)`和`removeSubrange(_:)`方法，包括`String`、`Array`、`Dictionary`和`Set`。



### 子字符串

使用下标或者诸如`prefix(_:)`之类的方法从某个字符串中获取一个子字符串时，其结果是一个`Substring`类型的实例，而不是另一个`String`类型的实例。`String`类型提供的大多数方法，`Substring`类型也提供。**与`String`不同，在对`String`执行操作时，只能在短时间内使用其`Substring`。当准备将`Substring`存储更长的时间时，可以将`Substring`转换位`String`。

```swift
let greeting = "Hello, world!"
let index = greeting.firstIndex(of: ",") ?? greeting.endIndex
let beginning = greeting[..<index]
// beginning is "Hello"

// Convert the result to a String for long-term storage.
let newString = String(beginning)
```



与`String`实例一样，每个`Substring`实例也会占用一块内存，但`Substring`实例可以重用用于存储原始`String`的部分内存，或者重用用于存储另一个`Substring`的部分内存。由于`Substring`重复使用原始`String`的部分内存，所以只要使用原始`String`的任何`Substring`，原始`String`都必须保存在内存中。因此，`Substring`不适合长期存储。

![Substring.png](https://docs.swift.org/swift-book/_images/stringSubstring_2x.png)



## 比较字符串



### 字符串和字符相等

可以使用比较运算符`==`和`!=`来比较两个字符串或字符是否相等：

```swift
let quotation = "We're a lot alike, you and I."
let sameQuotation = "We're a lot alike, you and I."
if quotation == sameQuotation {
    print("These two strings are considered equal")
}
// Prints "These two strings are considered equal"
```



如果两个`String`值（或两个字符值）的扩展字素簇是规范相等的，则认为它们相等。如果扩展字素簇具有相同的语言含义和外观，即使它们是由不同的 Unicode 标量组成，它们在规范上也是相等的。例如，带有二声声调的字母`é`可以由单个 Unicode 标量值`U+00E9`表示，也可以由字母`e`的标量值`U+0065`和二声声调`ˊ`的标量值`U+0301`组合起来表示，这两种扩展字素簇都是表示字符`é`的有效方法，它们是相等的。

```swift
let latinCapitalLetterA: Character = "\u{41}"

let cyrillicCapitalLetterA: Character = "\u{0410}"

if latinCapitalLetterA != cyrillicCapitalLetterA {
    print("These two characters aren't equivalent.")
}
// Prints "These two characters aren't equivalent."
```



### 前缀和后缀相等

可以使用`String`的`hasPrefix(_:)`方法来判断字符串是否具有特定的前缀，可以使用`hasSuffix(_:)`方法来判断字符串是否具有特定的后缀。

```swift
let romeoAndJuliet = [
    "Act 1 Scene 1: Verona, A public place",
    "Act 1 Scene 2: Capulet's mansion",
    "Act 1 Scene 3: A room in Capulet's mansion",
    "Act 1 Scene 4: A street outside Capulet's mansion",
    "Act 1 Scene 5: The Great Hall in Capulet's mansion",
    "Act 2 Scene 1: Outside Capulet's mansion",
    "Act 2 Scene 2: Capulet's orchard",
    "Act 2 Scene 3: Outside Friar Lawrence's cell",
    "Act 2 Scene 4: A street in Verona",
    "Act 2 Scene 5: Capulet's mansion",
    "Act 2 Scene 6: Friar Lawrence's cell"
]

var act1SceneCount = 0
for scene in romeoAndJuliet {
    if scene.hasPrefix("Act 1 ") {
        act1SceneCount += 1
    }
}
print("There are \(act1SceneCount) scenes in Act 1")
// Prints "There are 5 scenes in Act 1"

var mansionCount = 0
var cellCount = 0
for scene in romeoAndJuliet {
    if scene.hasSuffix("Capulet's mansion") {
        mansionCount += 1
    } else if scene.hasSuffix("Friar Lawrence's cell") {
        cellCount += 1
    }
}
print("\(mansionCount) mansion scenes; \(cellCount) cell scenes")
// Prints "6 mansion scenes; 2 cell scenes"
```



## 字符串的 Unicode 表示形式

将 Unicode 字符串写入文本文件或者其他存储时，该字符串中的 Unicode 标量会以几种 Unicode 定义的编码形式之一进行编码。每个表单会将字符串编码为称为**代码单元**（code unit）的小块，UTF-8 编码形式将字符串编码为`8`位代码单元，UTF-16 编码形式将字符串编码为`16`位代码单元，UTF-32 编码形式将字符串编码为`32`位代码单元。



下面的每个示例显示以下字符串的不同表示形式：

```swift
let dogString = "Dog‼🐶"
```



### UTF-8 表示形式

可以通过迭代`dogString`的`utf8`属性来访问字符串的 UTF-8 表示形式，该属性的类型为`String.UTF8View`，它是一个无符号的`8`位（`UInt8`）十进制值的集合，每个值对应于字符串的 UTF-8 表示形式的每个字节：

![UTF-8.png](https://docs.swift.org/swift-book/_images/UTF8_2x.png)

```swift
for codeUnit in dogString.utf8 {
    print("\(codeUnit) ", terminator: "")
}
print("")
// Prints "68 111 103 226 128 188 240 159 144 182 "
```



### UTF-16 表示形式

可以通过迭代`dogString`的`utf16`属性来访问字符串的 UTF-16 表示形式，该属性的类型为`String.UTF16View`，它是一个无符号的`16`位（`UInt16`）十进制值的集合，每个值对应于字符串的 UTF-16 表示形式的`16`位代码单元：

![UTF-16.png](https://docs.swift.org/swift-book/_images/UTF16_2x.png)

```swift
for codeUnit in dogString.utf16 {
    print("\(codeUnit) ", terminator: "")
}
print("")
// Prints "68 111 103 8252 55357 56374 "
```



### Unicode 标量表示形式

可以通过迭代`dogString`的`unicodeScalars`属性来访问字符串的 Unicode 标量表示形式，该属性的类型为`UnicodeScalarView`，它是一个`UnicodeScalar`类型值的集合。



每个`UnicodeScalar`值有一个`value`属性，该属性返回 Unicode 标量的`21`位值，这个`21`值以一个`UInt32`值表示。因此，Unicode 标量表示形式是等效于 UTF-32 表示形式的。

![Unicode 标量表示形式.png](https://docs.swift.org/swift-book/_images/UnicodeScalar_2x.png)

```swift
for scalar in dogString.unicodeScalars {
    print("\(scalar.value) ", terminator: "")
}
print("")
// Prints "68 111 103 8252 128054 "
```



每个`UnicodeScalar`值也可以用于构造新的`String`值，例如使用字符串插值：

```swift
for scalar in dogString.unicodeScalars {
    print("\(scalar) ")
}
// D
// o
// g
// ‼
// 🐶
```





# 集合类型

Swift 提供了数组、字典和集合这三种集合类型，数组是值的有序集合，集合是唯一值的无序集合，字典是键值关联的无序集合。



Swift 中的数组、字典和集合，必须为它们指定可以存储的值类型和键类型，不能将不属于指定类型的值添加到这三种集合中。



## 集合类型的可变性

创建一个数组、字典或者集合，如果将其分配给**变量**，则创建的集合将是可变的；如果将其分配给**常量**，则该集合是不可变的。



## 数组

数组类型的声明语法如下：

```swift
// valueType 为要存储的值类型
Array<valueType>
```

或者：

```swift
// valueType 为要存储的值类型
[valueType]
```



> Swift 中的`Array`类型是可以桥接到 Foundation 中的`NSArray`类型的，相关信息可以查看 [Bridging Between Dictionary and NSDictionary](https://developer.apple.com/documentation/swift/dictionary#2846239)。



### 创建空数组

可以使用初始化程序语法创建特定类型的空数组：

```swift
var someInts = [Int]()
```

如果上下文信息已经提供了类型信息，还可以使用以下语法来创建一个空数组：

```swift
someInts.append(3) // 将 3 添加到 someInts 数组中

someInts = [] // 现在 someInts 是一个空数组了
```



### 创建具有默认值的数组

```swift
var threeDoubles = Array(repeating: 0.0, count: 3)
// threeDoubles is of type [Double], and equals [0.0, 0.0, 0.0]
```



### 通过将两个数组相加来创建新数组

```swift
var anotherThreeDoubles = Array(repeating: 2.5, count: 3)
// anotherThreeDoubles is of type [Double], and equals [2.5, 2.5, 2.5]

var sixDoubles = threeDoubles + anotherThreeDoubles
// sixDoubles is inferred as [Double], and equals [0.0, 0.0, 0.0, 2.5, 2.5, 2.5]
```



### 使用数组字面量创建数组

```swift
var shoppingList: [String] = ["Eggs", "Milk"]
```

或者：

```swift
var shoppingList = ["Eggs", "Milk"]
```



### 访问和修改数组

通过访问数组的`count`属性来获取数组中存储的元素个数：

```swift
print("The shopping list contains \(shoppingList.count) items.")
// Prints "The shopping list contains 2 items."
```

通过访问数组的`isEmpty`属性来判断数组是否为空：

```swift
if shoppingList.isEmpty {
    print("The shopping list is empty.")
} else {
    print("The shopping list isn't empty.")
}
// Prints "The shopping list isn't empty."
```

通过调用数组的`append(_:)`方法来向数组末尾添加新元素：

```swift
shoppingList.append("Flour")
// shoppingList now contains 3 items, and someone is making pancakes
```

可以使用复合赋值运算符`+=`来将一个数组中的所有元素添加另一个数组中去：

```swift
shoppingList += ["Baking Powder"]
// shoppingList now contains 4 items
shoppingList += ["Chocolate Spread", "Cheese", "Butter"]
// shoppingList now contains 7 items
```

使用下标语法来从数组中检索值：

```swift
var firstItem = shoppingList[0]
// firstItem is equal to "Eggs"
```

也可以使用下标语法来更改给定索引上的值，数组的索引从`0`开始：

```swift
shoppingList[0] = "Six eggs"
// the first item in the list is now equal to "Six eggs" rather than "Eggs"
```

还可以使用下标语法来更改某个索引范围内所有索引上的值，如果替换值数组中的元素个数**小于**索引范围内索引的个数，则会删除后续索引上的值；如果替换值数组中的元素个数**大于**索引范围内索引的个数，则会将多余的值添加到数组末尾：

```swift
shoppingList[4...6] = ["Bananas", "Apples"]
// shoppingList now contains 6 items
```

使用`insert(_:at:)`方法来在数组的指定索引处插入一个新元素：

```swift
shoppingList.insert("Maple Syrup", at: 0)
// shoppingList now contains 7 items
// "Maple Syrup" is now the first item in the list
```

使用`remove(at:)`方法来删除数组中指定索引处的元素：

```swift
let mapleSyrup = shoppingList.remove(at: 0)
// the item that was at index 0 has just been removed
// shoppingList now contains 6 items, and no Maple Syrup
// the mapleSyrup constant is now equal to the removed "Maple Syrup" string
```



> **使用下标访问或者修改数组时，索引值不能超过数组的索引边界，否则会触发运行时错误。**



如果想要删除数组中的最后一个元素，则可以使用`removeLast()`方法，而不是`remove（at:）`方法，这样可以避免查询数组的`count`值：

```swift
let apples = shoppingList.removeLast()
// the last item in the array has just been removed
// shoppingList now contains 5 items, and no apples
// the apples constant is now equal to the removed "Apples" string
```



### 数组迭代

可以使用`for-in`循环来遍历数组中的值：

```swift
for item in shoppingList {
    print(item)
}
// Six eggs
// Milk
// Flour
// Baking Powder
// Bananas
```

如果需要每个元素的索引及其值，请使用`enumerated()`方法迭代数组。对于数组中的每个元素，`enumerated()`方法都会返回一个由元素索引和元素值构成的元组：

```swift
for (index, value) in shoppingList.enumerated() {
    print("Item \(index + 1): \(value)")
}
// Item 1: Six eggs
// Item 2: Milk
// Item 3: Flour
// Item 4: Baking Powder
// Item 5: Bananas
```



## 集合

集合中无序存储着相同类型的不同值，当需要确保存储的值只出现一次时，可以使用集合。



> 有关将 Swift 的`Set`类型桥接到 Foundation 中的`NSSet`类型的信息，请参看 [Bridging Between Set and NSSet](https://developer.apple.com/documentation/swift/set#2845530)。



### 用于集合类型的哈希值

为了将某种类型的值存储到集合中，该类型必须是可散列的。也就是说，该类型需要提供一种方式来计算该类型值的哈希值，哈希值是一个`Int`类型的值。在比较两个值是否相等时，会比较两个值的哈希值是否相等。如果两个值是相等的，那么这两个值的哈希值就一定是相等的。



Swift 的所有基本类型（例如`String`、`Int`、`Double`和`Bool`）默认都是可散列的，可以用作设置值类型或字典键类型。



> 可以通过让自定义类型去遵循 Swift 标准库中的`Hashable`协议来使其支持用作设置值类型和字典键类型。有关实现必需的`hash(into:)`方法的更多信息，请参看  [Hashable](https://developer.apple.com/documentation/swift/hashable)。



### 集合类型的语法

Swift 中的集合类型被写作`Set<Element>`，`Element`是集合中存储的值的类型。



### 创建和初始化空集合

```swift
var letters = Set<Character>()
print("letters is of type Set<Character> with \(letters.count) items.")
// Prints "letters is of type Set<Character> with 0 items."
```

或者，如果上下文已经提供了类型信息，例如函数参数或者已经输入的变量或常量，您可以使用一个空数组字面量来创建一个空集：

```swift
letters.insert("a")
// letters now contains 1 value of type Character
letters = []
// letters is now an empty set, but is still of type Set<Character>
```



### 使用数组字面量来创建集合

```swift
var favoriteGenres: Set<String> = ["Rock", "Classical", "Hip hop"]
// favoriteGenres has been initialized with three initial items
```

**使用数组字面量来创建集合时，必须显式声明变量或常量的类型为`Set`类型。**也可以不显式指定存储值的类型：

```swift
var favoriteGenres: Set = ["Rock", "Classical", "Hip hop"]
```



### 访问和修改集合

使用`Set`的只读`count`属性来查找集合中存储的值个数：

```swift
print("I have \(favoriteGenres.count) favorite music genres.")
// Prints "I have 3 favorite music genres."
```

使用`Set`的`isEmpty`属性（`Boolean`类型）来判断集合是否为空：

```swift
if favoriteGenres.isEmpty {
    print("As far as music goes, I'm not picky.")
} else {
    print("I have particular music preferences.")
}
// Prints "I have particular music preferences."
```

使用`Set`的`insert(_:)`方法来向集合中添加新值：

```swift
favoriteGenres.insert("Jazz")
// favoriteGenres now contains 4 items
```

使用`remove(_:)`方法从集合中移除某个值，如果集合中存在该值，则该方法最终会返回一个已移除该值的集合；如果集合中不存在这个值，则会返回`nil`。或者，使用`removeAll()`方法来移除集合中的所有值。

```swift
if let removedGenre = favoriteGenres.remove("Rock") {
    print("\(removedGenre)? I'm over it.")
} else {
    print("I never much cared for that.")
}
// Prints "Rock? I'm over it."
```

使用`contains(_:)`方法来检查集合中是否存在某个特定值：

```swift
To check whether a set contains a particular item, use the contains(_:) method.

if favoriteGenres.contains("Funk") {
    print("I get up on the good foot.")
} else {
    print("It's too funky in here.")
}
// Prints "It's too funky in here."
```



### 集合迭代

可以使用`for-in`循环来迭代集合中的值：

```swift
for genre in favoriteGenres {
    print("\(genre)")
}
// Classical
// Jazz
// Hip hop
```

集合是无序的，如果想要按照特定顺序去遍历集合中的值，可以使用`Set`的`sorted()`方法，该方法会返回一个将集合中的值使用`<`运算符排序后的数组。

```swift
for genre in favoriteGenres.sorted() {
    print("\(genre)")
}
// Classical
// Hip hop
// Jazz
```



## 执行集合操作

### 基本集合操作

下图描述了集合 a 和集合 b，阴影区表示各种基本集合操作的结果：

![基本集合操作结果.png](https://docs.swift.org/swift-book/_images/setVennDiagram_2x.png)

- 使用`intersection(_:)`方法来创建一个包含两个集合共同含有的值的新集合。
- 使用`symmetricDifference(_:)`方法创建一个将两个集合组合一起后并去掉两个集合共同含有的值的新集合。
- 使用`union(_:)`方法创建一个将两个集合组合在一起后的新集合。
- 使用`subtracting(_:)`方法来创建一个去掉集合 a 中的集合 b 也包含的值的新集合。

```swift
let oddDigits: Set = [1, 3, 5, 7, 9]
let evenDigits: Set = [0, 2, 4, 6, 8]
let singleDigitPrimeNumbers: Set = [2, 3, 5, 7]

oddDigits.union(evenDigits).sorted()
// [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
oddDigits.intersection(evenDigits).sorted()
// []
oddDigits.subtracting(singleDigitPrimeNumbers).sorted()
// [1, 9]
oddDigits.symmetricDifference(singleDigitPrimeNumbers).sorted()
// [1, 2, 9]
```



### 集合关系和相等

下图描述了集合 a、集合 b 和集合 c，重叠区域代表集合之间共享的元素。集合 a是集合 b 的超集，因为 a 包含 b 中的所有元素。反过来说，集合 b 是集合 a 的子集。集合 b 和集合 c彼此不相交，因为它们没有共同的元素。

![集合关系和相等.png](https://docs.swift.org/swift-book/_images/setEulerDiagram_2x.png)

- 使用`==`运算符来确定两个集合是否包含所有相同的值。
- 使用`isSubset(of:)`方法确定一个集合的所有值是否包含在指定的集合中。
- 使用`isSuperset(of:)`方法确定一个集合是否包含指定集合中的所有值。
- 使用`isStrictSubset(of:)`或`isStrictSuperset(of:)`方法确定一个集合是子集还是超集，但不等于指定集合。
- 使用`isDisjoint(with:)`方法确定两个集合是否没有共同的值。

```swift
let houseAnimals: Set = ["🐶", "🐱"]
let farmAnimals: Set = ["🐮", "🐔", "🐑", "🐶", "🐱"]
let cityAnimals: Set = ["🐦", "🐭"]

houseAnimals.isSubset(of: farmAnimals)
// true
farmAnimals.isSuperset(of: houseAnimals)
// true
farmAnimals.isDisjoint(with: cityAnimals)
// true
```



## 字典

字典中存储着相同类型的键和相同类型的值，每个值都与一个唯一的键相关联，键充当字典中某个值的标识符。与数组不同，字典中存储的值是无序的。



> Swift 中的`Dictionary`类型是可以桥接到 Foundation 中的`NSDictionary`类的，相关信息可以查看 [Bridging Between Dictionary and NSDictionary](https://developer.apple.com/documentation/swift/dictionary#2846239)。



### 字典类型标准语法

