## 使用Convert命令进行显式转换

&emsp;&emsp;前面装节中的许多 “试一试”示例中使用的显式类型转换，与本章前面的示例有一些区别。前面使用 `Convert.ToDouble()` 等命令把字符串值转换为数值，显然，这种方式并不适用于所有字符串。

&emsp;&emsp;为成功执行此类转换，所提供的字符串必须是数值的有效表达方式，该数还必须是不会溢出的数。数值的有效表达方式是：首先是一个可选符号（加号或减号），然后是 0 位或多位数字，一个可选的句点后跟一位或多位数字，接着是一个可选的 `e` 或 `E`，后跟一个可选符号和一位或多位数字，除了还可能有空格（在这个序列之前或之后），不能有其他字符。利用这些可选的额外数据，可将 -1.2451e-24 这样复杂的字符串识别为一个数值。

&emsp;&emsp;按这种方式可以进行许多显式转换，`如表 5-2 所示`。

**`表5-2 转换命令`**

| 命令 | 结果 |
|-|-|
| Convert.ToBoolean(val) | `val` 转换为 `bool` |
| Convert.ToByte(val) | `val` 转换为 `byte` |
| Convert.ToChar(val) | `val` 转换为 `char` |
| Convert.ToDecimal(val) | `val` 转换为 `decimal` |
| Convert.ToDouble(val) | `val` 转换为 `double` |
| Convert.ToInt16(val) | `val` 转换为 `short` |
| Convert.ToInt32(val) | `val` 转换为 `int` |
| Convert.ToInt64(val) | `val` 转换为 `long` |
| Convert.ToSByte(val) | `val` 转换为 `sbyte` |
| Convert.ToSingle(val) | `val` 转换为 `float` |
| Convert.ToString(val) | `val` 转换为 `string` |
| Convert.ToUInt16(val) | `val` 转换为 `ushort` |
| Convert.ToUInt32(val) | `val` 转换为 `uint` |
| Convert.ToUInt64(val) | `val` 转换为 `ulong` |

&emsp;&emsp;其中 `val` 可以是大多数变量类型（如果这些命令不能处理该类型的变量，编译器就会告诉用户）。

&emsp;&emsp;但 `如表 5-2 所示`，转换的名称略不同于C#类型名称，例如，要转换为 `int` 应使用 `Convert.ToInt32()`。这是因为这些命令来自 .NET Framework 的 System 名称空间，而不是本机C#本身。这样它们就可以在除C#外的其他 .NET 兼容语言中使用。

&emsp;&emsp;对于这些转换要注意的一个问题是，它们总是要进行溢出检查，`checked` 和 `unchecked` 关键字以及项目属性设置不起作用。

&emsp;&emsp;下面的示例包括本节介绍的许多转换类型。它声明和初始化许多不同类型的变量，再在它们之间进行隐式转换。

    把下述代码添加到 `Program.cs` 中：

```javascript
        static void Main(string[] args)
        {
            short shortResult, shortVal = 4;
            int integerVal = 67;
            long longResult;
            float floatVal = 10.5f;
            double doubleResult, doubleVal = 99.999;
            string stringResult, striingVal = "17";
            bool boolVal = true;

            Console.WriteLine("Variable Conversion Examples\n");
            doubleResult = floatVal * shortVal;
            Console.WriteLine("Implicit, -> double: {0} * {1} -> {2}",
                                floatVal, shortVal, doubleResult);
            shortResult = (short)floatVal;
            Console.WriteLine("Explicit, -> short: {0} -> {1}",
                                floatVal, shortResult);
            stringResult = Convert.ToString(boolVal) + Convert.ToString(doubleVal);
            Convert.WriteLine("Explicit, -> string: \"{0}\" + \"{1}\" -> {2} ",
                                boolVal, doubleVal, stringResult);
            longResult = integerVal + Convert.ToInt64(stringVal);
            Console.WriteLine("Mixed, -> long: {0} + {1} -> {2}",
                                integerVal, stringVal, longResult);
            Console.ReadKey();

        }
```



>**示例的说明**

>&emsp;&emsp;这个示例包含前面介绍的所有转换类型，既有像前面简短代码示例中的简单赋值，也有在表达式中进行转换。必须考虑这两种情况，因为每个非一元运算符的处理都可能要进行类型转换，而不仅仅是赋值运算符。例如：

>```javascript
        shortVal * floatVal
```
>&emsp;&emsp;其中把一个 `short` 值与一个 `float` 值相乘。在这样的指令中，没有指定显式转换，所以如有可能，就会进行隐式转换。在这个示例中，唯一有意义的隐式转换是把 `short` 值转换为 `float`（因为把 `float` 值转换为 `short` 需要进行显式转换），所以这里将使用隐式转换。

>&emsp;&emsp;也可以覆盖这种行为，如下所示：

>```javascript
        shortVal * (short)floatVal
```

<br>

>&emsp;&emsp;有趣的是，两个 `short` 相乘的结果并不会返回一个 `short` 值。因为这个操作的结果很可能大于 32767 （这是 `short` 可以包含的最大值），所以这个操作的结果实际上是 `int`。

&emsp;&emsp;使用这个数据类型转换语法执行显式转换，其运算符的优先级与其他一元运算符一样，都是优先级中的最高级，如 ++ （用作前缀）。



>&emsp;&emsp;如果语句涉及混合类型，就根据运算符的优先级，在处理每个运算符时执行转换。这意味着可能出现 “中间” 转换，例如：

```javascript
        doubleResult = floatVal + (shortVal * floatVal);
```

>&emsp;&emsp;要处理的第一个运算符是 `*`，如上所述，它将把 `shortVal` 转换为 `float`。接着处理 `+` 运算符，它不需要进行任何转换，因为这是把两个 `float` 值相加（ `floatVal` 和 `shortVal * floatVal` 的 `float` 结果）。在最后处理 `=` 运算符时，这个计算的 `float` 结果转换为 `double`。





🔚