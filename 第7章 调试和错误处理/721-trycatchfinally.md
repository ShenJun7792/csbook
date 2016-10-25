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














🔚