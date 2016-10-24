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


&emsp;&emsp;前面已经遇到了命令行参数，在命令行上执行应用程序时，通常可以直接指定信息，如在执行应用程序时加载一个文件。例如，考虑 `Windows` 中的记事本应用程序。在命令提示窗口中键入 `notepad`，或在 `Windows` 的 `Start` 菜单中选择 `Run` 选项，再在打开的窗口中键入 `notepad`，就可以运行该应用程序。也可以键入 `notepad "myfile.txt"`，结果是 `Notepad` 在运行时将加载文件 `myfile.txt`，结果是 `Notepad` 在运行时将加载文件 `myfile.txt`，如果该文件不存在，`Notepad` 也会创建该文件。这里 `myfile.txt` 是一个命令行参数。利用 `args` 参数，可以编写以类似方式工作的控制台应用程序。

>&emsp;&emsp;在执行控制台应用程序时，指定的任何命令行参数都放在这个 `args` 数组中，接着可以根据需要在应用程序中使用这些参数。下面用一个示例来说明。这个示例可以指定任意数量的命令行参数，每个参数都输出到控制台上。

>把下列代码添加到 `Program.cs` 中：

>```javascript
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("{0} command line arguments were specified:", args.Length);
                foreach (string arg in args)
                {
                    Console.WriteLine(arg);
                }
            }
        }
```

>&emsp;&emsp;打开项目的属性页面，选择 `调试` 页面，在 `命令行参数` 设置中添加所希望的命令行参数，`如图 6-7 所示`。

>![图6-7](/assets/6-7.png)

>**`图 6-7`**

>&emsp;&emsp;**示例的说明**

>&emsp;&emsp;这里使用的代码非常简单：

>```javascript
        Console.WriteLine("{0} command line arguments were specified:", args.Length);
        foreach (string arg in args)
            Console.WriteLine(arg);
```
>&emsp;&emsp;使用 `args` 参数与使用其他字符串数组类似。我们没有对参数进行任何异样的操作，只是把指定信息写到屏幕上。在本示例中，通过IDE中的项目属性提供参数，这是一种很便携的方式，只要在IDE中运行应用程序，就可以使用相同的命令行参数，无需每次都在命令行提示窗口中键入它们。




















🔚