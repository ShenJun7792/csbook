##try...catch...finally

&emsp;&emsp;C#语言包含结构化异常处理（Structured Exception Handling, SEH）的语法。用 3 个关键字可以标记出能处理异常的代码和指令，如果发生异常，就使用这些指令处理异常。用于这个目的的 3 个关键字是 `try`、`catch`和 `finally`。它们都有一个关联的代码块，必须在连续的代码行中使用。其基本结构如下：

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