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

            Console.WriteLine();
        }
```











🔚