##try...catch...finally

&emsp;&emsp;C#语言包含**结构化异常处理**（Structured Exception Handling, **SEH**）的语法。用 3 个关键字可以标记出能处理异常的代码和指令，如果发生异常，就使用这些指令处理异常。用于这个目的的 3 个关键字是 `try`、`catch`和 `finally`。它们都有一个关联的代码块，必须在连续的代码行中使用。其基本结构如下：

```javascript
        try
        {
            ...
        }
        catch(<exceptionType> e)
        {
            ...
        }
        finally
        {
            ...
        }
```

&emsp;&emsp;也可以只有 `try` 块和 `finally` 块，而没有 `catch` 块，或者有一个 `try` 块和好几个 `catch` 块。如果有一个或多个 `catch` 块，`finally` 块就是可选的，否则就是必需的。这些代码块的用法如下：

&emsp;&emsp;● **try** -- 包含抛出异常的代码（在谈到异常时，C#语言用 “抛出”这个术语表示 “生成” 或 “导致”）。

&emsp;&emsp;● **catch** -- 包含抛出异常时要执行的代码。`catch` 块可以使用 `<exceptionType>`，设置为只响应特定的异常类型（如System.IndexOutOfRangeException），以便提供多个 `catch` 块。还可以完全省略这个参数，让一般的 `catch` 块响应所有异常。

&emsp;&emsp;● **finally** -- 包含始终会执行的代码，如果没有产生异常，则在 `try` 块之后执行，如果处理了异常，就在 `catch` 块后执行，或者在未处理的异常上移到调用堆栈之前执行。“上移到调用堆栈”表示，SEH允许嵌套 `try...catch...finally` 块，可以直接嵌套，也可以在 `try` 块包含的函数调用中嵌套。例如，如果在被调用的函数中没有 `catch` 块能处理某个异常，就由调用代码中的 `catch` 块处理。如果始终没有匹配的 `catch` 块，就终止应用程序。`finally` 块在此之前处理正是其存在的意义，否则也可以在 `try...catch...finally` 结构的外部放置代码。这个嵌套功能将在后面的 “异常处理的注意事项” 一节中进一步讨论，所以如果对这个功能感到困惑不解，请不必担心。

&emsp;&emsp;在 `try` 块的代码中出现异常后，发生的事件依次是：

&emsp;&emsp;● try 块在发生异常的地方中断程序的执行。

&emsp;&emsp;● 如果有 `catch` 块，就检查该块是否匹配已抛出的异常类型。如果没有 `catch` 块，就执行 `finally` 块（如果没有 `catch` 块，就一定要有 `finally` 块）。

&emsp;&emsp;● 如果有 `catch` 块，但它与已发生的异常类型不匹配，就检查是否有其他 `catch` 块。

&emsp;&emsp;● 如果有 `catch` 块匹配已发生的异常类型，就执行它包含的代码，再执行 `finally` 块（如果有）。

&emsp;&emsp;● 如果 `catch` 块都不匹配已发生的异常类型，就执行 `finally` 块（如果有）。

>&emsp;&emsp;下面用一个示例来说明异常的处理。这个示例以几种方式抛出和处理异常，以便读者了解其机制。

>&emsp;&emsp;修改代码，如下所示（这里显示的行号注释有助于将代码与后面讨论的内容联系起来，在本章的可下载代码中也包含这些行号，以方便参考）：

```javascript
        class Program
        {
            static string[] eTypes = { "none", "simple", "index", "nested index" };

            static void Main(string[] args)
            {
                foreach (string eType in eTypes)
                {
                    try
                    {
                        Console.WriteLine("Main() try block reached.");     // Line 19
                        Console.WriteLine("ThrowException(\"{0}\") called.", eType);
                        ThrowException(eType);
                        Console.WriteLine("Main() try block continues.");   // Line 22
                    }
                    catch (System.IndexOutOfRangeException e)               // Line 24
                    {
                        Console.WriteLine("Main() System.IndexOutOfRangeException 
                                           catch" + "block reached. Message:\n\"{0}\"", 
                                           e.Message);
                    }
                    catch                                                   // Line 30
                    {
                        Console.WriteLine("Main() general catch block reached.");
                    }
                    finally
                    {
                        Console.WriteLine("Main() finally block reached.");
                    }
                    Console.WriteLine();
                }
                Console.ReadKey();
            }

            static void ThrowException(string exceptionType)
            {
                Console.WriteLine("ThrowException(\"{0}\") reached.", exceptionType);

                switch (exceptionType)
                {
                    case "none":
                        Console.WriteLine("Not throwing an exception.");
                        break;                                              // Line 50
                    case "simple":
                        Console.WriteLine("Throwing System.Exception.");
                        throw new System.Exception();                       // Line 53
                    case "index":
                        Console.WriteLine("Throwing System.IndexOutOfRangeException.");
                        eTypes[4] = "error";                                // Line 56
                        break;
                    case "nested index":
                        try                                                 // Line 59
                        {
                            Console.WriteLine("ThrowException(\"nested index\")" + 
                                                "try block reached.");
                            Console.WriteLine("ThrowException(\"index\") called.");
                            ThrowException("index");                        // Line 64
                        }
                        catch                                               // Line 66
                        {
                            Console.WriteLine("ThrowException(\"nested index\") general"
                                              + "catch block reached.");
                        }
                        finally
                        {
                            Console.WriteLine("ThrowException(\"nested index\") finally"
                                              + "block reached." );
                        }
                        break;
                }
            }
        }
```


>&emsp;&emsp;**示例的说明**

>&emsp;&emsp;这个应用程序在 `Main()` 中有一个 `try` 块，它调用函数 `ThrowException()`。这个函数会根据调用时使用的参数抛出异常：

>&emsp;&emsp;● ThrowException("none") -- 不抛出异常。

>&emsp;&emsp;● ThrowException("simple") -- 生成一般异常。

>&emsp;&emsp;● ThrowException("index") -- 生成 `System.IndexOutOfRangeException` 异常。

>&emsp;&emsp;● ThrowException("nested index") -- 包含它自己的 `try` 块，其中的代码调用 `ThrowException("index")`，生成一个 `System.IndexOutOfRangeException` 异常

>&emsp;&emsp;其中的每个 `string` 参数都存储在全局数组 `eTypes` 中，在 `Main()` 函数中迭代，用每个可能的参数调用 `ThrowException()`。在迭代过程中，会把各种信息写到控制台上，说明发生了什么情况。这段代码可以使用本章节前面介绍的代码单步执行技巧。在执行代码的过程中，一次执行一行代码可以确切地了解代码的执行进度。

>在代码的第 19 行添加一个新断点（用默认的属性），该行代码如下：

>```javascript Console.WriteLine("Main() try block reached.");```

>&emsp;&emsp;**这里使用了行号来表示代码。如果关闭了行号，可以选择 `工具(T)` | `选项（O）`，在 `文本编辑器` | `C#` | `常规` 选项区域中打开它们。**

>&emsp;&emsp;在调试模式下运行应用程序。程序立即进入中断模式，此时光标停在第 19 行上。如果选择变量监视窗口中的 `局部变量` 选项卡，就会看到 `eType` 当前是 `none`。使用 `逐语句` 按钮处理第 19 和 20 行，看看第一行文本是否已经写到控制台。接着使用 `逐语句` 按钮单步执行第 21 行的 `ThrowException()` 函数。

>&emsp;&emsp;执行到 `ThrowException()` 函数后，`局部变量` 窗口会发生变化。`eType` 和 `args` 超出了作用域（因为它们是 `Main()` 的局部变量），我们看到的是 `exceptionType` 的值，执行代码，把字符串 `Not throw an exception` 写到屏幕上。在执行第 50 行上的 `break` 语句时，将退出函数，继续处理 `Main()` 中的第 22 行代码。因为没有抛出异常，所以继续执行 `try` 块。

>&emsp;&emsp;接着处理 `finally` 块。再单击 `逐语句` 几次，执行完 `finally` 块和 `foreach` 的第一次循环。下次执行到第 21 行时，使用另一个参数 `simple` 调用 `ThrowException()`。

>&emsp;&emsp;继续使用 `逐语句` 单步执行 `ThrowException()`，最终会执行第 53 行：

>```javascript throw new System.Exception();```

>&emsp;&emsp;这里使用C# `throw` 关键字生成一个异常，需要为这个关键字提供新初始化的异常作为其参数，抛出一个异常，这里使用名称空间 `System` 中的另一个异常 `System.Exception`。

>&emsp;&emsp;**这个 `case` 块不需要 `break` 语句，使用 `throw` 就可以结束该块的执行。**

>&emsp;&emsp;在使用 `逐语句` 执行这个语句时，将从第 30 行开始执行一般的 `catch` 块。因为与第 24 行开始的 `catch` 块都不匹配，所以执行这个一般的 `catch` 块。单步执行这段代码，然后执行 `finally` 块，最后返回到另一个循环周期，该循环在第 21 行用一个新参数调用 `ThrowException()`，这次的参数是 `index`。

>&emsp;&emsp;这次 `ThrowException()` 在第 56 行生成一个异常：

>```javascript eType[4] = "error";```

>&emsp;&emsp;`eTypes` 是一个全局数组，所以可以在这里访问它。但是这里视图访问数组中的第 5 个元素（其索引从 0 开始计数），这会生成一个 `System.IndexOutOfRangeException` 异常。

>&emsp;&emsp;这次 `Main()` 中有一个匹配的 `catch` 块，单步执行该 `catch` 块，从第 24 行开始。这个块中调用的 `Console.WriteLine()` 使用 `e.Message`，输出存储在异常中的消息（可以通过 `catch` 块的参数访问异常）。之后再次单步执行 `finally` 块（而不是第二个 `catch` 块，因为异常已经处理完毕）。返回循环，再次调用第 21 行的 ThrowException（）。

>&emsp;&emsp;在执行到 `ThrowException()` 中的 `switch` 结构时，进入一个新的 `try` 块，从第 59 行开始。在执行到第 64 行时，将遇到 `ThrowException()` 的一个嵌套调用，这次使用 `index` 参数。可以使用 `逐过程` 按钮跳过其中的代码行，因为前面已经单步执行过了。与前面一样，这个调用生成一个 `System.IndexOutOfRangeException` 异常。但这个异常在 `ThrowException()` 中的嵌套 `try...catch...finally` 结构中处理。这个结构没有明确匹配这种异常 `catch` 块，所以执行一般的 `catch` 块（从第 66 行开始）。

>&emsp;&emsp;与前面的异常处理一样，现在单步执行这个 `catch` 块，以及关联的 `finally` 块，最后返回到函数调用的末尾处。但是它们有一个重要的区别：抛出异常是由 `ThrowException（）` 中的代码处理的。这就是说，异常并没有留给 `Main()` 处理，所以直接进入 `finally` 块，之后应用程序中断执行。










🔚