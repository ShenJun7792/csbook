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