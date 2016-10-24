##Main()函数

&emsp;&emsp;前面介绍了创建和使用函数时涉及的大多数简单技术，下面详细讨论 `Main()` 函数。

&emsp;&emsp;`Main()` 是 C#应用程序的入口点，执行这个函数就是执行应用程序。也就是说，在执行过程开始时，会执行 `Main()` 函数，在 `Main()` 函数执行完毕时，执行过程就结束了。

&emsp;&emsp;这个函数可以返回 `void` 或 `int`，有一个可选参数 `string[] args`。`Main()` 函数可使用如下 4 中版本：

```javascript
        static void Main()
        static void Main(string[] args)
        static int Main()
        static int Main(string[] args)
```

&emsp;&emsp;上面的第三、四个版本返回一个 `int` 值，它们可以用于表示应用程序的终止方式，通常用作一种错误提示（但这不是强制的）。一般情况下，返回 0 反映了 “正常” 的终止（即应用程序执行完毕，并安全地终止）。

&emsp;&emsp;`Main()` 的可选参数 `args` 是从应用程序的外部接受信息的方法，这些信息在运行应用程序时以命令行参数的形式指定。




🔚