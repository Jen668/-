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



### 集合类型语法

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



### 字典类型简写语法

Swift 字典类型的完整语法为`Dictionary<Key, Value>`，也可以直接简写为`[Key: Value]`，`Key`是字典 key 的类型，`Value`是 key 对应的值的类型。



### 创建空字典

使用初始化语法创建一个空字典：

```swift
var namesOfIntegers: [Int: String] = [:]
// namesOfIntegers is an empty [Int: String] dictionary
```

或者：

```swift
namesOfIntegers[16] = "sixteen"
// namesOfIntegers now contains 1 key-value pair
namesOfIntegers = [:]
// namesOfIntegers is once again an empty dictionary of type [Int: String]
```



### 使用字典字面量创建字典

```swift
// [key 1: value 1, key 2: value 2, key 3: value 3]

var airports: [String: String] = ["YYZ": "Toronto Pearson", "DUB": "Dublin"]
```

如果字典中的所有 key 的类型是一致的，并且所有 value 的类型也是一致的，则不用显式声明`airports`变量为字典类型，Swift 会自动推断为字典类型：

```swift
var airports = ["YYZ": "Toronto Pearson", "DUB": "Dublin"]
```



### 访问和修改字典

访问`count`属性来查找字典中键值对的数量：

```swift
print("The airports dictionary contains \(airports.count) items.")
// Prints "The airports dictionary contains 2 items."
```

访问`isEmpty`属性来判断该字典是否是一个空字典：

```swift
if airports.isEmpty {
    print("The airports dictionary is empty.")
} else {
    print("The airports dictionary isn't empty.")
}
// Prints "The airports dictionary isn't empty."
```

可以使用下标语法来向字典中添加新的键值对：

```swift
airports["LHR"] = "London"
// the airports dictionary now contains 3 items
```

或者使用下标语法来更改与指定 key 关联的值：

```swift
airports["LHR"] = "London Heathrow"
// the value for "LHR" has been changed to "London Heathrow"
```

也可以使用`updateValue(_:forKey:)`方法来向字典中添加新的键值对或者更改与指定 key 关联的值，与下标语法不同，`updateValue(_:forKey:)`方法还会返回与指定 key 关联的旧值，这个值是一个可选的字典值类型，如果在更新之前，字典中存在指定 key 的旧值，则此可选值包含指定 key 的旧值；如果不存在旧值，则为`nil`：

```swift
if let oldValue = airports.updateValue("Dublin Airport", forKey: "DUB") {
    print("The old value for DUB was \(oldValue).")
}
// Prints "The old value for DUB was Dublin."
```

 还可以使用下标语法从字典中检索与指定 key 关联的值，返回值是一个可选的字典值类型：

```swift
if let airportName = airports["DUB"] {
    print("The name of the airport is \(airportName).")
} else {
    print("That airport isn't in the airports dictionary.")
}
// Prints "The name of the airport is Dublin Airport."
```

可以使用下标语法将与指定 key 关联的值设为`nil`来从字典中删除键值对：

```swift
airports["APL"] = "Apple International"
// "Apple International" isn't the real airport for APL, so delete it
airports["APL"] = nil
// APL has now been removed from the dictionary
```

或者，使用`removeValue(forKey:)`方法从字典中删除键值对，此方法会返回删除的值（如果存在），如果不存在值，则会返回`nil`：

```swift
if let removedValue = airports.removeValue(forKey: "DUB") {
    print("The removed airport's name is \(removedValue).")
} else {
    print("The airports dictionary doesn't contain a value for DUB.")
}
// Prints "The removed airport's name is Dublin Airport."
```



### 字典迭代

可以使用`for-in`循环来遍历字典中的键值对，每次循环会将字典中的一个键值对作为一个`(key, value)`元组返回，我们可以讲元组的成员分解为单独的临时常量或者变量：

```swift
for (airportCode, airportName) in airports {
    print("\(airportCode): \(airportName)")
}
// LHR: London Heathrow
// YYZ: Toronto Pearson
```

还可以通过访问字典的`keys`属性来遍历字典中的所有 key，通过访问字典的`values`属性来遍历字典中的所有值：

```swift
for airportCode in airports.keys {
    print("Airport code: \(airportCode)")
}
// Airport code: LHR
// Airport code: YYZ

for airportName in airports.values {
    print("Airport name: \(airportName)")
}
// Airport name: London Heathrow
// Airport name: Toronto Pearson
```



# 控制流



## for-in 循环

遍历数组：

```swift
let names = ["Anna", "Alex", "Brian", "Jack"]
for name in names {
    print("Hello, \(name)!")
}
// Hello, Anna!
// Hello, Alex!
// Hello, Brian!
// Hello, Jack!
```

遍历字典：

```swift
let numberOfLegs = ["spider": 8, "ant": 6, "cat": 4]
for (animalName, legCount) in numberOfLegs {
    print("\(animalName)s have \(legCount) legs")
}
// cats have 4 legs
// ants have 6 legs
// spiders have 8 legs
```

遍历数字区间，会返回区间内的每个数字：

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

在遍历**字符串、数组、字典、集合或者数字区间**时，如果返回值不是必需的，则可以使用`_`来代替循环变量，这会导致单个值被忽略，并且在循环的每次迭代期间不提供对当前值的访问：

```swift
let minutes = 60
for tickMark in 0..<minutes {
    // render the tick mark each minute (60 times)
}
```

某些场景下，我们可能需要跨步执行某些操作，这时可以使用`for-in`循环配合`stride(from:to:by:)`方法（开区间）或者`stride(from:through:by:)`方法（闭区间）来分段区间：

```swift
let minuteInterval = 5
for tickMark in stride(from: 0, to: minutes, by: minuteInterval) {
    // render the tick mark every 5 minutes (0, 5, 10, 15 ... 45, 50, 55)
}


let hours = 12
let hourInterval = 3
for tickMark in stride(from: 3, through: hours, by: hourInterval) {
    // render the tick mark every 3 hours (3, 6, 9, 12)
}
```



## while 循环

```swift
var square = 0
var diceRoll = 0
while square < finalSquare {
    // roll the dice
    diceRoll += 1
    if diceRoll == 7 { diceRoll = 1 }
    // move by the rolled amount
    square += diceRoll
    if square < board.count {
        // if we're still on the board, move up or down for a snake or a ladder
        square += board[square]
    }
}
print("Game over!")
```



## repeat-while 循环

与`while`循环不同，`repeat-while `循环会先执行一次循环，然后再判断循环条件。

```swift
repeat {
    // move up or down for a snake or ladder
    square += board[square]
    // roll the dice
    diceRoll += 1
    if diceRoll == 7 { diceRoll = 1 }
    // move by the rolled amount
    square += diceRoll
} while square < finalSquare
print("Game over!")
```



## 条件语句

### if 语句

```swift
temperatureInFahrenheit = 90
if temperatureInFahrenheit <= 32 {
    print("It's very cold. Consider wearing a scarf.")
} else if temperatureInFahrenheit >= 86 {
    print("It's really warm. Don't forget to wear sunscreen.")
} else {
    print("It's not that cold. Wear a t-shirt.")
}
// Prints "It's really warm. Don't forget to wear sunscreen."
```



### switch-case 语句

```swift
let someCharacter: Character = "z"
switch someCharacter {
case "a":
    print("The first letter of the alphabet")
case "z":
    print("The last letter of the alphabet")
default:
    print("Some other character")
}
// Prints "The last letter of the alphabet"
```

#### 区间匹配

```swift
let approximateCount = 62
let countedThings = "moons orbiting Saturn"
let naturalCount: String
switch approximateCount {
case 0:
    naturalCount = "no"
case 1..<5:
    naturalCount = "a few"
case 5..<12:
    naturalCount = "several"
case 12..<100:
    naturalCount = "dozens of"
case 100..<1000:
    naturalCount = "hundreds of"
default:
    naturalCount = "many"
}
print("There are \(naturalCount) \(countedThings).")
// Prints "There are dozens of moons orbiting Saturn."
```

#### 使用元组作为条件值

```swift
let somePoint = (1, 1)
switch somePoint {
case (0, 0):
    print("\(somePoint) is at the origin")
case (_, 0):
    print("\(somePoint) is on the x-axis")
case (0, _):
    print("\(somePoint) is on the y-axis")
case (-2...2, -2...2):
    print("\(somePoint) is inside the box")
default:
    print("\(somePoint) is outside of the box")
}
// Prints "(1, 1) is inside the box"
```

![coordinateGraphSimple_2x.png](https://docs.swift.org/swift-book/_images/coordinateGraphSimple_2x.png)

#### 值绑定

```swift
let anotherPoint = (2, 0)
switch anotherPoint {
case (let x, 0):
    print("on the x-axis with an x value of \(x)")
case (0, let y):
    print("on the y-axis with a y value of \(y)")
case let (x, y):
    print("somewhere else at (\(x), \(y))")
}
// Prints "on the x-axis with an x value of 2"
```

#### where

`switch-case`语句 还可以使用 `where`子句来检查附加条件：

```swift
let yetAnotherPoint = (1, -1)
switch yetAnotherPoint {
case let (x, y) where x == y:
    print("(\(x), \(y)) is on the line x == y")
case let (x, y) where x == -y:
    print("(\(x), \(y)) is on the line x == -y")
case let (x, y):
    print("(\(x), \(y)) is just some arbitrary point")
}
// Prints "(1, -1) is on the line x == -y"
```

#### 复合 case

```swift
let someCharacter: Character = "e"
switch someCharacter {
case "a", "e", "i", "o", "u":
    print("\(someCharacter) is a vowel")
case "b", "c", "d", "f", "g", "h", "j", "k", "l", "m",
     "n", "p", "q", "r", "s", "t", "v", "w", "x", "y", "z":
    print("\(someCharacter) is a consonant")
default:
    print("\(someCharacter) isn't a vowel or a consonant")
}
// Prints "e is a vowel"


let stillAnotherPoint = (9, 0)
switch stillAnotherPoint {
case (let distance, 0), (0, let distance):
    print("On an axis, \(distance) from the origin")
default:
    print("Not on an axis")
}
// Prints "On an axis, 9 from the origin"
```



## 控制转移语句

### continue

在循环语句中使用`continue`语句时，会立即跳出本次循环，并**继续执行**后续循环：

```swift
let puzzleInput = "great minds think alike"
var puzzleOutput = ""
let charactersToRemove: [Character] = ["a", "e", "i", "o", "u", " "]
for character in puzzleInput {
    if charactersToRemove.contains(character) {
        continue
    }
    puzzleOutput.append(character)
}
print(puzzleOutput)
// Prints "grtmndsthnklk"
```

### break

在循环语句中使用`break`语句时，会立即跳出本次循环，并且**不再执行**后续循环。



在`switch-case`语句中使用`break`语句时，会立即结束执行`switch-case`语句：

```swift
let numberSymbol: Character = "三"  // Chinese symbol for the number 3
var possibleIntegerValue: Int?
switch numberSymbol {
case "1", "١", "一", "๑":
    possibleIntegerValue = 1
case "2", "٢", "二", "๒":
    possibleIntegerValue = 2
case "3", "٣", "三", "๓":
    possibleIntegerValue = 3
case "4", "٤", "四", "๔":
    possibleIntegerValue = 4
default:
    break
}
if let integerValue = possibleIntegerValue {
    print("The integer value of \(numberSymbol) is \(integerValue).")
} else {
    print("An integer value couldn't be found for \(numberSymbol).")
}
// Prints "The integer value of 三 is 3."
```



### fallthrough

`swift-case`语句的某个`case`语句执行完毕后，就不会再执行下一个`case`或者`default`语句了。如果想要某个`case`语句执行完毕后继续执行下一个`case`或者`default`语句中的代码，则可以在该`case`语句中使用`Fallthrough`语句，**该语句会使代码执行直接移动到下一个`case`语句中的代码，而不会去判断下一个`case`或者`default`语句的条件是否为真**：

```swift
let integerToDescribe = 5
var description = "The number \(integerToDescribe) is"
switch integerToDescribe {
case 2, 3, 5, 7, 11, 13, 17, 19:
    description += " a prime number, and also"
    fallthrough
default:
    description += " an integer."
}
print(description)
// Prints "The number 5 is a prime number, and also an integer."
```



### 标签

在某个循环内部嵌套使用`switch-case`语句或者其他循环时，为了明确`continue`或者`break`语句的作用对象，可以使用标签来标记循环（如果没有使用标签标记循环，则默认作用对象为`continue`或者`break`语句所在的这层循环）：

```swift
loopA: for i in 2...6 {
            
	print("loop A --- \(i)")
            
	loopB: for j in 1...7 {
    
    print("loop B --- \(j)")
    
		if j == 2 {
                    
			break loopA
		}
	}
}
```



### guard

`guard`语句与`if`语句类似，但`guard`语句要求条件必须为真，以便执行`guard`语句之后的代码。与`if`语句不同的是，`guard`语句总是包含一个`else`子句。如果`guard`语句的条件为假，则会执行`else`子句中的代码。

```swift
func greet(person: [String: String]) {
    guard let name = person["name"] else {
        return
    }

    print("Hello \(name)!")

    guard let location = person["location"] else {
        print("I hope the weather is nice near you.")
        return
    }

    print("I hope the weather is nice in \(location).")
}

greet(person: ["name": "John"])
// Prints "Hello John!"
// Prints "I hope the weather is nice near you."
greet(person: ["name": "Jane", "location": "Cupertino"])
// Prints "Hello Jane!"
// Prints "I hope the weather is nice in Cupertino."
```

与使用`if`语句进行相同的检查相比，使用`guard`语句可以提高代码的可读性。



## 检查 API 可用性

```swift
if #available(iOS 10, macOS 10.12, *) {
    // Use iOS 10 APIs on iOS, and use macOS 10.12 APIs on macOS
} else {
    // Fall back to earlier iOS and macOS APIs
}
```





# 函数



## 定义和调用函数

定义函数时，需要使用`func`关键字作为前缀，后面是函数名，函数名后面是`()`，`()`号内包含函数的参数，`()`号是`->`，`->`后面是返回值类型。在以下代码中，`greet`是函数名，`person`是参数名称，`:`后面是参数类型：

```swift
func greet(person: String) -> String {
    let greeting = "Hello, " + person + "!"
    return greeting
}
```

调用函数：

```swift
greet(person: "Anna")
```

在以上代码中，`greet`是函数名称，`person`是参数标签（未显式指定参数的标签时，默认使用参数的名称作为起标签）。



### 没有参数的函数

```swift
func sayHelloWorld() -> String {
    return "hello, world"
}
print(sayHelloWorld())
// Prints "hello, world"
```



### 具有多个参数的函数

```swift
func greet(person: String, alreadyGreeted: Bool) -> String {
    if alreadyGreeted {
        return greetAgain(person: person)
    } else {
        return greet(person: person)
    }
}
print(greet(person: "Tim", alreadyGreeted: true))
// Prints "Hello again, Tim!"
```



### 没有返回值的函数

```swift
func greet(person: String) {
    print("Hello, \(person)!")
}
greet(person: "Dave")
// Prints "Hello, Dave!"
```



### 具有多个返回值的函数

可以使用元组作为函数的返回值类型，以便将多个返回值作为一个复合值返回。

```swift
func minMax(array: [Int]) -> (min: Int, max: Int) {
    var currentMin = array[0]
    var currentMax = array[0]
    for value in array[1..<array.count] {
        if value < currentMin {
            currentMin = value
        } else if value > currentMax {
            currentMax = value
        }
    }
    return (currentMin, currentMax)
}

```

### 返回值为可选类型的函数

```swift
func minMax(array: [Int]) -> (min: Int, max: Int)? {
    if array.isEmpty { return nil }
    var currentMin = array[0]
    var currentMax = array[0]
    for value in array[1..<array.count] {
        if value < currentMin {
            currentMin = value
        } else if value > currentMax {
            currentMax = value
        }
    }
    return (currentMin, currentMax)
}
```



## 函数参数标签和参数名称

每个函数参数都有**参数标签**和**参数名称**，调用函数时使用**参数标签**，每个参数都写在函数调用中，前面有**参数标签**。**参数名称**用于函数的实现。**默认情况下，参数使用其参数名称作为参数标签。**



### 指定参数标签

```swift
func greet(person: String, from hometown: String) -> String {
    return "Hello \(person)!  Glad you could visit from \(hometown)."
}
print(greet(person: "Bill", from: "Cupertino"))
// Prints "Hello Bill!  Glad you could visit from Cupertino."
```



### 省略参数标签

如果不想要参数的参数标签，则可以在参数名称之前使用`_`来代替参数标签：

```swift
func someFunction(_ firstParameterName: Int, secondParameterName: Int) {
    // In the function body, firstParameterName and secondParameterName
    // refer to the argument values for the first and second parameters.
}
someFunction(1, secondParameterName: 2)
```



### 默认参数值

可以通过在参数类型后为参数分配值来为函数中的任何参数定义*默认值*。如果定义了默认值，则可以在调用函数时省略该参数。

```swift
func someFunction(parameterWithoutDefault: Int, parameterWithDefault: Int = 12) {
    // If you omit the second argument when calling this function, then
    // the value of parameterWithDefault is 12 inside the function body.
}
someFunction(parameterWithoutDefault: 3, parameterWithDefault: 6) // parameterWithDefault is 6
someFunction(parameterWithoutDefault: 4) // parameterWithDefault is 12
```



### 可变参数

可以使用可变参数来指定调用函数时可以传递不同数量的输入值，通过在参数的类型后加上`...`来编写可变参数：

```swift
func arithmeticMean(_ numbers: Double...) -> Double {
    var total: Double = 0
    for number in numbers {
        total += number
    }
    return total / Double(numbers.count)
}
arithmeticMean(1, 2, 3, 4, 5)
// returns 3.0, which is the arithmetic mean of these five numbers
arithmeticMean(3, 8.25, 18.75)
// returns 10.0, which is the arithmetic mean of these three numbers
```

**在可变参数之后的第一个其他参数必须具有参数标签。**



### 输入输出参数

函数的参数默认为常量，在函数主体内更改函数参数的值会导致编译时错误。如果想要在函数主体内修改参数的值，并且希望这些更改在函数调用结束后持续存在，则可以将参数定义为**输入输出参数**。通过在参数类型之前加上`inout`关键字来编写一个输入输出参数：

```swift
func swapTwoInts(_ a: inout Int, _ b: inout Int) {
    let temporaryA = a
    a = b
    b = temporaryA
}

var someInt = 3
var anotherInt = 107
swapTwoInts(&someInt, &anotherInt)
print("someInt is now \(someInt), and anotherInt is now \(anotherInt)")
// Prints "someInt is now 107, and anotherInt is now 3"
```

**注意：输入输出参数不能设置默认值。**



## 函数类型

每个函数都有特定的函数类型，由函数的参数类型和返回值类型组成。

```swift
func addTwoInts(_ a: Int, _ b: Int) -> Int {
    return a + b
}
func multiplyTwoInts(_ a: Int, _ b: Int) -> Int {
    return a * b
}
```

以上代码中两个函数的类型都是`(Int, Int) -> Int`。



### 使用函数类型

可以将常量或者变量定义为函数类型：

```swift
var mathFunction: (Int, Int) -> Int = addTwoInts
```

然后就可以调用名为`mathFunction`的函数了：

```swift
print("Result: \(mathFunction(2, 3))")
// Prints "Result: 5"

mathFunction = multiplyTwoInts
print("Result: \(mathFunction(2, 3))")
// Prints "Result: 6"
```

与任何其他类型一样，将函数分配给常量或者变量时，swift 会自动推断函数类型：

```swift
let anotherMathFunction = addTwoInts
// anotherMathFunction is inferred to be of type (Int, Int) -> Int
```



### 函数类型作为函数的参数类型

```swift
func printMathResult(_ mathFunction: (Int, Int) -> Int, _ a: Int, _ b: Int) {
    print("Result: \(mathFunction(a, b))")
}
printMathResult(addTwoInts, 3, 5)
// Prints "Result: 8"
```



### 函数类型作为函数的返回值类型

```swift
func stepForward(_ input: Int) -> Int {
    return input + 1
}
func stepBackward(_ input: Int) -> Int {
    return input - 1
}

func chooseStepFunction(backward: Bool) -> (Int) -> Int {
    return backward ? stepBackward : stepForward
}

var currentValue = 3
let moveNearerToZero = chooseStepFunction(backward: currentValue > 0)
// moveNearerToZero now refers to the stepBackward() function

print("Counting to zero:")
// Counting to zero:
while currentValue != 0 {
    print("\(currentValue)... ")
    currentValue = moveNearerToZero(currentValue)
}
print("zero!")
// 3...
// 2...
// 1...
// zero!
```



## 嵌套函数

除了可以定义全局函数之外，Swift 还支持在函数的主体内定义其他函数，称为嵌套函数。

```swift
func chooseStepFunction(backward: Bool) -> (Int) -> Int {
    func stepForward(input: Int) -> Int { return input + 1 }
    func stepBackward(input: Int) -> Int { return input - 1 }
    return backward ? stepBackward : stepForward
}
var currentValue = -4
let moveNearerToZero = chooseStepFunction(backward: currentValue > 0)
// moveNearerToZero now refers to the nested stepForward() function
while currentValue != 0 {
    print("\(currentValue)... ")
    currentValue = moveNearerToZero(currentValue)
}
print("zero!")
// -4...
// -3...
// -2...
// -1...
// zero!
```



# 闭包

闭包（closure）是自包含的函数块，可以在代码中传递和使用。Swift 中的闭包类似于 C 和 Objective-C 中的 block。



**全局函数和嵌套函数是实际上是闭包的特例。**闭包有以下三种形式：

- 全局函数是具有名称且不捕获任何值的闭包。
- 嵌套函数是具有名称的闭包，可以从其封闭函数中捕获值。
- 闭包表达式是用轻量级语法编写的未命名闭包，可以从周围的上下文中捕获值。



## 闭包表达式

调用`Array`对象的`sorted(by:)`函数时，需要向该函数传递一个闭包，这个闭包具有两个与数组存储类型一致的参数，并返回一个`Bool`值，这个`Bool`值用来说明在排序时给定的第一个参数值是排在给定的第二个参数值之前（`true`）还是之后（`false`）。由于全局函数是闭包的一种特殊形式，所以可以像下面这样使用`sorted(by:)`函数：

```swift
let names = ["Chris", "Alex", "Ewa", "Barry", "Daniella"]

func backward(_ s1: String, _ s2: String) -> Bool {
    return s1 > s2
}

var reversedNames = names.sorted(by: backward)
// reversedNames is equal to ["Ewa", "Daniella", "Chris", "Barry", "Alex"]
```

但是上面这种方式比较冗长，为了让代码更加简洁，我们可以使用闭包表达式语法内联编写排序闭包。



闭包表达式语法有以下一般形式：

​	{ (`parameters`) **->** `return type` **in**
​    	`statements`
​	}



上面例子中的排序闭包可以写成这样：

```swift
reversedNames = names.sorted(by: { (s1: String, s2: String) -> Bool in
    return s1 > s2
})
```



### 从上下文推断类型

当将闭包作为一个内联闭包表达式传递给函数或者方法时，Swift 总是可以根据上下文自动推断出闭包的参数类型和返回值类型。因此，上面例子中的排序闭包还可以编写为：

```swift
reversedNames = names.sorted(by: { s1, s2 in return s1 > s2 } )
```



### 单一表达式闭包的隐式返回值

我们可以通过省略**单一表达式**闭包的`return`关键字来隐式返回该闭包主体内的单一表达式的返回值，上面例子中排序闭包的单一表达式`s1>s2`会返回一个`Bool`值，因此还可以编写成以下这样：

```swift
reversedNames = names.sorted(by: { s1, s2 in s1 > s2 } )
```



### 简写参数名称

Swift 会自动为**内联闭包**提供简写的参数名称，我们可以通过名称`$0`、`$1`、`$2`...来引用内联闭包`第一个`、`第二个`、`第三个`...参数的值。如果我们在内联闭包表达式的主体内使用了这些简写参数名称，则我们可以省略内联闭包表达式中的参数列表，`in`关键字也可以省略：

```swift
reversedNames = names.sorted(by: { $0 > $1 } )
```



### 运算符方法

以上例子中的内联闭包表达式还有一种更简单的编写方式--[自动闭包](#自动闭包)：

```swift
reversedNames = names.sorted(by: >)
```



## 尾随闭包

当需要将闭包表达式传递给函数作为函数的最终参数，并且闭包表达式很长，那么将其编写为**尾随闭包**是非常有用地。

```swift
func someFunctionThatTakesAClosure(closure: () -> Void) {
    // function body goes here
}

// 使用闭包调用函数

someFunctionThatTakesAClosure(closure: {
    // closure's body goes here
})

// 使用尾随闭包调用函数

someFunctionThatTakesAClosure() {
    // trailing closure's body goes here
}
```



前面例子中的排序函数也可以使用尾随闭包去调用：

```swift
reversedNames = names.sorted() {(s1: String, s2: String) -> Bool in
    return s1 > s2
}
```

如果闭包是函数或方法的唯一参数，并且使用尾随闭包去调用函数或方法，则在调用函数或者方法时可以省略函数名称后面的一对括号`()`：

```swift
// 闭包的参数类型和返回值类型被省略了
reversedNames = names.sorted { $0 > $1 }
```



Swift 的`Array`类型有一个`map(_:)`方法，该方法接受一个闭包表达式作为其唯一参数，该方法会为数组对象中的每个元素调用一次传递进来的闭包来返回该元素的映射值。在以下代码中，由于闭包表达式较长，所以使用尾随闭包来调用`map(_:)`方法：

```swift
let digitNames = [
    0: "Zero", 1: "One", 2: "Two",   3: "Three", 4: "Four",
    5: "Five", 6: "Six", 7: "Seven", 8: "Eight", 9: "Nine"
]
let numbers = [16, 58, 510]

let strings = numbers.map { (number) -> String in
    var number = number
    var output = ""
    repeat {
        output = digitNames[number % 10]! + output
        number /= 10
    } while number > 0
    return output
}
// strings is inferred to be of type [String]
// its value is ["OneSix", "FiveEight", "FiveOneZero"]
```



如果一个函数需要多个闭包参数，则省略第一个尾随闭包的参数标签，并标记其余的尾随闭包。例如，下面的函数为照片库加载图片：

```swift
func loadPicture(from server: Server, completion: (Picture) -> Void, onFailure: () -> Void) {
    if let picture = download("photo.jpg", from: server) {
        completion(picture)
    } else {
        onFailure()
    }
}
// 调用loadPicture函数
loadPicture(from: someServer) { picture in
    someView.currentPicture = picture
} onFailure: {
    print("Couldn't download the next picture.")
}
```



## 捕获值

闭包可以从周围上下文中捕获常量和变量，在闭包表达式主体内可以引用和修改这些常量和变量的值，即使定义常量和变量的原始作用域已不存在。



在 Swift 中，可以捕获值的闭包的最简单形式是嵌套函数，嵌套函数可以捕获其外部函数的任何参数，也可以捕获外部函数中定义的任何常量和变量。

```swift
func makeIncrementer(forIncrement amount: Int) -> () -> Int {
    var runningTotal = 0
    func incrementer() -> Int {
        runningTotal += amount
        return runningTotal
    }
    return incrementer
}

let incrementByTen = makeIncrementer(forIncrement: 10)

/*
	此时 makeIncrementer 函数的栈帧已被释放，而 runningTotal 变量已被 incrementByTen 闭包引用
*/

incrementByTen()
// returns a value of 10
incrementByTen()
// returns a value of 20
incrementByTen()
// returns a value of 30

let incrementBySeven = makeIncrementer(forIncrement: 7)
incrementBySeven()
// returns a value of 7
```



闭包会从周围上下文中捕获对常量和变量的引用，从而确保在定义常量和变量的作用域失效后调用闭包时，常量和变量还未被销毁。



## 闭包是引用类型

函数和闭包属于引用类型。将函数或闭包分配给常量或变量时，实际上是将常量和变量的指针指向了闭包的内存地址。以下代码中的`alsoIncrementByTen`常量和上面的`incrementByTen`常量引用的是同一个闭包：

```swift
let alsoIncrementByTen = incrementByTen
alsoIncrementByTen()
// returns a value of 50

incrementByTen()
// returns a value of 60
```



## 逃逸闭包

一个闭包被作为参数传递给某个函数，并在该函数返回之后才被执行，Swift 将这种场景称为闭包从函数中逃逸。在声明一个将闭包作为其参数之一的函数时，可以在参数的类型前加上`@escaping`来表示允许闭包从函数中逃逸。



逃逸闭包多被用来当作函数回调，例如：许多执行异步操作的函数会将闭包参数作为其完成处理程序，函数在开始执行异步操作后返回，但直到异步操作执行完毕后才调用闭包。



以下代码中，`completionHandlers`变量是一个存放`() -> Void`类型闭包的数组，`someFunctionWithEscapingClosure`函数会将传递进来的闭包添加到`completionHandlers`数组中。如果没有允许传递进来的闭包可以从函数中逃逸的话，编译以下代码时会报错。

```swift
var completionHandlers: [() -> Void] = []
func someFunctionWithEscapingClosure(completionHandler: @escaping () -> Void) {
    completionHandlers.append(completionHandler)
}
```



**引用`self`的逃逸闭包，如果`self`是一个类的实例，则可能会导致循环引用。有关循环引用的更多信息，请参看后面的[自动引用计数](#自动引用计数)章节。**



**非逃逸闭包可以隐式地引用`self`，而逃逸闭包必须显式地引用`self`。**以下代码中，传递给`someFunctionWithEscapingClosure`函数的闭包**显式**地引用了`self`，而传递给`someFunctionWithNonescapingClosure`函数的闭包**隐式**地引用了`self`。

```swift
func someFunctionWithNonescapingClosure(closure: () -> Void) {
    closure()
}

class SomeClass {
    // 属性 x
    var x = 10
  
    func doSomething() {
        someFunctionWithEscapingClosure { self.x = 100 }
        someFunctionWithNonescapingClosure { x = 200 }
    }
}

let instance = SomeClass()
instance.doSomething()
print(instance.x)
// Prints "200"

completionHandlers.first?()
print(instance.x)
// Prints "100"
```



如果`self`是一个结构体或枚举的实例，则闭包始终可以**隐式**地引用`self`。但是，当`self`是结构体或者枚举的实例时，逃逸闭包无法捕获对`self`的可变引用。如[结构体和枚举是值类型](#结构体和枚举是值类型)章节中所述，结构体和枚举不允许共享可变性。

```swift
struct SomeStruct {
    var x = 10
    mutating func doSomething() {
        someFunctionWithNonescapingClosure { x = 200 }  // Ok
        someFunctionWithEscapingClosure { x = 100 }     // Error, 不允许共享可变性
    }
}
```



## 自动闭包

定义一个具有闭包类型的参数的函数时，如果在闭包类型前加上`@autoclosure`属性来标记参数可以自动转换为闭包，那么我们在使用这个函数时，可以直接将一段代码作为闭包参数传递给这个函数，编译器在编译时会自动为这段代码创建一个闭包。

```swift
var customersInLine = ["Chris", "Alex", "Ewa", "Barry", "Daniella"]

func serve(customer customerProvider: @autoclosure () -> String) {
    print("Now serving \(customerProvider())!")
}
serve(customer: customersInLine.remove(at: 0))

/*
	可以逃逸的自动闭包
*/
// customersInLine is ["Barry", "Daniella"]
var customerProviders: [() -> String] = []
func collectCustomerProviders(_ customerProvider: @autoclosure @escaping () -> String) {
    customerProviders.append(customerProvider)
}
collectCustomerProviders(customersInLine.remove(at: 0))
collectCustomerProviders(customersInLine.remove(at: 0))

print("Collected \(customerProviders.count) closures.")
// Prints "Collected 2 closures."
for customerProvider in customerProviders {
    print("Now serving \(customerProvider())!")
}
// Prints "Now serving Barry!"
// Prints "Now serving Daniella!"
```



# 枚举



## 枚举语法

使用`enum`关键字来定义一个枚举，并使用`case`关键字来引入一个新的枚举案例：

```swift
enum CompassPoint {
    case north
    case south
    case east
    case west
}
```

多个枚举案例可以出现在同一行上，用逗号隔开：

```swift
enum Planet {
    case mercury, venus, earth, mars, jupiter, saturn, uranus, neptune
}
```



定义一个枚举就是定义了一个新的类型，与 Swift 中的其他类型一样，枚举的名字以大写字母开头。



使用枚举：

```swift
var directionToHead = CompassPoint.west

// directionToHead的类型已经已知，所以可以省略掉枚举的类型
directionToHead = .east
```



## 将枚举值与 switch-case 语句匹配

```swift
directionToHead = .south
switch directionToHead {
case .north:
    print("Lots of planets have a north")
case .south:
    print("Watch out for penguins")
case .east:
    print("Where the sun rises")
case .west:
    print("Where the skies are blue")
}
// Prints "Watch out for penguins"
```



## 迭代枚举案例

当枚举遵循`CaseIterable`协议时，可以使用枚举的`allCases`属性来迭代枚举案例。

```swift
enum Beverage: CaseIterable {
    case coffee, tea, juice
}
let numberOfChoices = Beverage.allCases.count
print("\(numberOfChoices) beverages available")
// Prints "3 beverages available"

for beverage in Beverage.allCases {
    print(beverage)
}
// coffee
// tea
// juice
```



## 关联值

枚举的案例还可以关联一个其他类型的值，这种枚举被称为 discriminated union 或 tagged union。



例如，假设库存跟踪系统需要通过两种不同类型的条形码来跟踪产品，一部分产品使用了 UPC 格式的 1D 条形码（每个竖线条代表`0`到`9`之间的某个数字）来标记，还有一部分产品使用了二维码格式的 2D 条形码（使用若干个与二进制相对应的几何形体来表示任何 ISO 8859-1 字符）来标记。库存跟踪系统将 UPC 条形码存储为包含4个`Int`类型的元组，将二维码条形码存储为任意长度的字符串。

![UPC格式条形码](https://docs.swift.org/swift-book/_images/barcode_UPC_2x.png)

![二维码格式条形码](https://docs.swift.org/swift-book/_images/barcode_QR_2x.png)

在 Swift 中，我们可以为上面的例子定义一个产品条形码的枚举：

```swift
enum Barcode {
    case upc(Int, Int, Int, Int)
    case qrCode(String)
}
```

我们可以为某个产品创建一个新的条形码，并设置不同格式的条形码：

```swift
var productBarcode = Barcode.upc(8, 85909, 51226, 3)

productBarcode = .qrCode("ABCDEFGHIJKLMNOP")
```

使用`switch-case`语句检查条形码类型并提取关联值：

```swift
switch productBarcode {
case .upc(let numberSystem, let manufacturer, let product, let check):
    print("UPC: \(numberSystem), \(manufacturer), \(product), \(check).")
case .qrCode(let productCode):
    print("QR code: \(productCode).")
}
// Prints "QR code: ABCDEFGHIJKLMNOP."

/*
	如果所有关联值都统一被提取为常量或者变量，则可以直接在案例前加上`let`或者`var`关键字，而不用逐个显式声明
*/
switch productBarcode {
case let .upc(numberSystem, manufacturer, product, check):
    print("UPC : \(numberSystem), \(manufacturer), \(product), \(check).")
case let .qrCode(productCode):
    print("QR code: \(productCode).")
}
// Prints "QR code: ABCDEFGHIJKLMNOP."
```



## 原始值

枚举的案例还可以手动设置默认值（称为原始值），这些值都是**同一**类型的。



以下是一个将案例的原始值设置为原始 ASCII 值的枚举：

```swift
enum ASCIIControlCharacter: Character {
    case tab = "\t"
    case lineFeed = "\n"
    case carriageReturn = "\r"
}
```

原始值可以是字符串、字符或者任何整数或浮点数类型，每个原始值在其枚举声明中必须是唯一的。



### 隐式分配原始值

